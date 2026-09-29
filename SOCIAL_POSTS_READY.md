# Social Posts Ready to Publish

These posts are written in English for LinkedIn, X, Dev.to, or similar channels. Each one links to the exact public project and ends with a technical question.

## Post A — launch

I built **GridWise AI**, an end-to-end energy decision-support research prototype.

It connects:

- leakage-aware time-series forecasting
- chronological model evaluation
- constrained optimization
- Streamlit and FastAPI delivery
- Docker, tests, and CI

The main question was not only:

> What will demand be?

It was:

> Given the forecast, what action is feasible under operational constraints?

On a chronological holdout:

- RMSE: **62.04 Wh**
- R²: **0.53**
- peak reduction in the included scenario: **100 Wh**
- energy-budget error: **0 Wh**

This is a research prototype using public household-energy data as a proxy for building and industrial telemetry.

GitHub: https://github.com/hossiendehghan989/gridwise-ai

What should be added first: live tariffs, carbon-intensity feeds, or equipment-level constraints?

## Post B — engineering lesson

A forecasting model is not automatically an operational solution.

While building GridWise AI, I treated the forecast as one layer in a larger decision system:

1. validate the data
2. prevent target leakage
3. evaluate chronologically
4. expose uncertainty and limitations
5. optimize an action under constraints
6. deliver the result through an interface or API

The lesson: model quality matters, but the decision boundary around the model matters just as much.

Repository: https://github.com/hossiendehghan989/gridwise-ai

## Post C — limitations

One of the most important parts of an AI project is explaining what it does **not** claim.

GridWise AI uses a public household-energy dataset and illustrative price/carbon signals. It demonstrates a forecasting-to-optimization workflow, but it is not production-ready control software.

A real deployment would still need:

- validated live data contracts
- equipment-level constraints
- monitoring and drift detection
- security review
- operational approval and fail-safe behavior

Being explicit about limitations makes a technical project easier to trust.

Project and roadmap: https://github.com/hossiendehghan989/gridwise-ai

## Post D — portfolio positioning

My work sits at the intersection of:

- industrial engineering
- applied AI and data science
- energy intelligence
- operational and investment decision support

Public projects:

- GridWise AI — forecast to constrained energy schedule
- AtlasRE — transparent downside-first investment screening
- Tesla Stock Analysis — forecasting and sentiment research

The common thread is simple: make the system understandable, make assumptions explicit, and turn analysis into a decision someone can inspect.

Portfolio: https://github.com/hossiendehghan989
