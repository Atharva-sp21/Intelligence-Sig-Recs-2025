## KEY POINTS

* first i loaded the big training data (w, x, y). it was huge so i used only a small sample to check patterns.
* did some quick EDA — checked nulls, data types, describe and correlation. saw that **y had strong relation with w and x**.
* plotted `y` vs `w*x` and saw a **clear sine wave pattern**. that was the main discovery.
* made a new feature `sin_wx = sin(w*x)` which showed almost perfect linear link with y.
* trained a simple **XGBoostRegressor** using this feature. the rmse was very low (~0.0025) so model was good.
* later i thought, since the graph looked like a **pure sine function**, it’s kind of physics based (y'' + y = 0).
* so i tried a **PINN (Physics Informed Neural Network)** to see if it can learn both data and the physics law together.
* PINN training logs showed total loss and physics loss going down steady → means it learned the sine behavior well.
* overall, found that `y` depends on `w*x` in a periodic (sinusoidal) way and both XGBoost and PINN captured it nicely.
* plots of predicted vs actual look almost same wave, so final result is very accurate.

