# From Demand Forecasting to Operational Decisions: Building GridWise AI

A forecasting model can tell us what demand may look like. An operational system must go one step further: it must help decide what action is feasible under constraints.

That distinction is the reason I built [GridWise AI](https://github.com/hossiendehghan989/gridwise-ai), an end-to-end research prototype that connects time-series forecasting to constrained energy scheduling.

## The problem

Many applied machine-learning projects end at a prediction. In energy operations, that is only one part of the problem. A useful system must also account for flexible load, power limits, peak demand, price signals, carbon signals, uncertainty, and the difference between a model metric and an operational outcome.

GridWise was designed around a simple question:

> Given the forecast, what action is feasible under the constraints?

## The workflow

The project makes the path from data to decision explicit:

```text
UCI energy data
      ↓
Validation and leakage-aware features
      ↓
Chronological model benchmark
      ↓
Forecast and uncertainty experiments
      ↓
Constrained linear-program scheduler
      ↓
Streamlit dashboard and FastAPI service
```

The public UCI Appliances Energy Prediction dataset is used as a reproducible proxy for building and industrial telemetry. It is useful for demonstrating the workflow, but it is not a substitute for validating against real equipment or grid data.

## Why chronological evaluation matters

Forecasting is directional: a production system trains on the past and predicts the future. A random split can allow information from later periods to influence the training set and make the result look stronger than it would be operationally.

GridWise uses the first 80% of the ordered data for training and reserves the final 20% as an out-of-sample holdout. Every model and baseline is evaluated on the same holdout.

The feature layer also shifts historical variables before calculating rolling statistics. That keeps the current target out of its own predictors.

## What the benchmark showed

The benchmark produced a useful, non-obvious result:

| Model | MAE (Wh) | RMSE (Wh) | R² |
| --- | ---: | ---: | ---: |
| Naive: previous reading | 26.5 | 66.2 | 0.46 |
| **Gradient Boosting** | **29.2** | **62.0** | **0.53** |
| Naive: rolling mean | 34.1 | 75.1 | 0.31 |
| Extra Trees | 39.4 | 67.7 | 0.44 |

The naive previous-reading baseline has lower MAE, while Gradient Boosting has the best RMSE and R². That is more useful than a simple leaderboard: model choice depends on which errors are costly for the decision.

## From forecast to schedule

The scheduler introduces a flexible load variable `x_t` and a peak variable `z`. It solves a constrained linear program subject to:

```text
0 ≤ x_t ≤ maximum_power_per_period
Σ x_t = required_flexible_energy
forecast_demand_t + x_t ≤ z
```

The included scenario preserves a 1,200 Wh flexible-energy budget and reduces the combined demand peak by 100 Wh under a 300 Wh per-period cap.

The result is not a claim that the illustrative schedule is ready to control physical equipment. It is a transparent demonstration of how a forecast can become a constrained decision.

## What makes the prototype useful

The repository includes a Streamlit dashboard, FastAPI endpoints, Docker support, automated tests, CI, walk-forward experiments, uncertainty intervals, feature ablation, explainability, robust scheduling, and a production guide that documents what is still missing.

That last part matters. A good prototype should make its limitations visible:

- the dataset represents a home rather than a factory or grid asset;
- tariff and carbon vectors are illustrative;
- the scheduler is scenario-based rather than a full mixed-integer industrial optimizer;
- production deployment would require monitoring, security review, real data contracts, and equipment-level constraints.

## What I would build next

The next useful extension is an adapter layer for live or user-supplied tariff and carbon-intensity data. The adapter should normalize timestamps, units, missing values, and provenance while keeping the optimization core independent from any single provider.

That discussion is open in [GridWise issue #1](https://github.com/hossiendehghan989/gridwise-ai/issues/1).

## Final takeaway

A model is only one component of a decision system. The system becomes more useful when it makes assumptions explicit, evaluates the future honestly, respects constraints, and delivers an output that someone can inspect and challenge.

Full implementation: [github.com/hossiendehghan989/gridwise-ai](https://github.com/hossiendehghan989/gridwise-ai)

---

**Author:** [Hossein Dehghan](https://github.com/hossiendehghan989) — Industrial Engineering, applied AI, energy intelligence, and operational decision support.
