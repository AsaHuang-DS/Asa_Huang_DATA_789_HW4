# HW4 — Short Answers

Answer each question in 2–3 sentences.

## 1. Rolling-update safety
Why does the Deployment use `maxUnavailable: 0`, and what would change if it were `maxUnavailable: 1`?

> Using `maxUnavailable: 0` guarantees that zero downtime occurs during a rollout because Kubernetes won't terminate an old pod until a new one if fully running and ready. If set to `maxUnavailable: 1`, Kubernetes would allow one pod to drop offline before bringing up its replacement which temporarily reduces cluster capacity and risks dropping traffic under high load.

## 2. Health probes
Why do the liveness/readiness probes target `/health` instead of `/predict`?

> Targeting `/health` provides a quick, lightwiehgt check that confirms the application process is running without triggering expensive inference logic. In constrast, probing `/predict` would force the container to execute unnecessary model predictions on every check, causing high CPU overhead and potential false-positive failures if the model latencies spike.
