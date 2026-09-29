# GitHub Audience Content Kit

This kit turns the public portfolio into a repeatable publishing system. The core narrative is:

> **I build practical AI decision systems for energy and industrial operations.**

## Post 1 — flagship project launch

I built **GridWise AI**, an end-to-end energy decision-support system.

It combines:

- leakage-aware time-series forecasting
- chronological model benchmarking
- constrained optimization
- a Streamlit decision dashboard
- FastAPI, Docker, tests, and CI

The important step is moving from:

> “What will demand be?”

to:

> “Given the forecast, what action is feasible under the constraints?”

On a chronological holdout, Gradient Boosting achieved **62.0 Wh RMSE** and **0.53 R²**. The optimizer preserved a fixed flexible-energy budget while reducing the modeled peak by **100 Wh** in the included scenario.

Repository: https://github.com/hossiendehghan989/gridwise-ai

Demo video: https://files.manuscdn.com/user_upload_by_module/session_file/310519663990434475/zqNLMpQwgsMVbxyz.mp4

What would you add first: live tariffs, carbon-intensity feeds, or equipment-level constraints?

## Post 2 — engineering lesson

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

## Post 3 — portfolio positioning

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

## Short bio

Industrial Engineering graduate building AI decision systems for energy and industrial operations.

## Publishing rhythm

Publish one technical post per week. Rotate between a project result, an engineering lesson, and a limitation or next step. End with one specific question so readers have a clear way to participate.

## Rules

Use measured results, link the exact repository, disclose illustrative data, and never claim investment or production readiness without evidence. Do not ask for artificial stars or followers; ask for technical feedback instead.
