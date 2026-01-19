Project Structure

Parts 1–3: Model Specification and Estimation

Formulation of a structural market model motivated by IRL principles

Estimation of signal weights and market impact parameters via likelihood-based methods

Calibration using historical DJIA data

Part 4: IRL-Implied Structure Validation

Evaluation of the predictive implications of the estimated IRL-inspired structure

Comparison against a random walk baseline

Assessment of whether the inferred latent structure provides incremental explanatory power

Methodological Notes

This project is IRL-inspired rather than a strict theoretical implementation of inverse reinforcement learning. In particular:

The model does not explicitly recover a full reward–policy pair in the formal IRL sense.

Estimated parameters are interpreted as reflecting latent reward structure consistent with observed market behavior.

Part 4 focuses on validation and interpretation rather than introducing a new learning architecture.

This framing is intentional and aligns with the exploratory and applied nature of the course assignment.

Results Summary

The final analysis examines whether the inferred IRL-implied structure exhibits predictive or explanatory value relative to a random walk benchmark. Results are presented quantitatively and discussed with attention to limitations, stability, and interpretation rather than overfitting or performance claims.

Limitations

Financial markets are highly noisy and non-stationary; results should be interpreted cautiously.

The model abstracts from many institutional features of real-world trading.

The IRL interpretation is structural and illustrative rather than a formal proof of optimal agent behavior.

Academic Context

This repository represents individual coursework completed for an NYU Tandon graduate-level course. It is shared for educational and portfolio purposes only and is not intended as trading advice or a production-ready system.
