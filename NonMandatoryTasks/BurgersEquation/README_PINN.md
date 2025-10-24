# Burgers’ 2D PINN Project

I recently started exploring new sub-domains in ML, and PINNs really caught my attention. This project applies a **Physics-Informed Neural Network** to solve the **2D Burgers’ equations**, a simplified version of Navier–Stokes that models fluid convection and diffusion.

I generated a **synthetic time-series dataset** with varying viscosities (ν) and trained a PINN that takes (x, y, t, ν) as input to predict velocity components (u, v). The model combines **data loss** (mean squared error) and **physics loss** (enforcing PDE residuals) for better generalization, even on unseen ν values.

Optimization was done using **Adam** followed by **LBFGS**. I also tested the model’s stability under noise and tuned hyperparameters to maintain accuracy. Recently, I read about **Trust-Region Sequential Quadratic Programming** by *Xiaoran Cheng and Sen Na*, which inspired me to explore better convergence strategies for future PINN work.
