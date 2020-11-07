# Lecture on transport phenomena

This repository contains two jupyter notebooks for the lecture on transport phenomena. 

Please open the file named TransportPhenomenaLab.ipynb first. It contains the interactive assigment. To gain a deeper understanding of the contents shown in the lecture with more examples, look at TransportPhenomenaLab-Addition.ipynb. 

## This notebook is designed for the lecture on transport phenomena 

__As you will see, this notebook consists of four parts:__
- Real data for comparison
- A finite-differences implementation to solve the Partial Differential Equation (PDE)
- A cell to define the thermal diffusivity $\alpha$
- A comparison between real values and calculated ones

__First, choose a value for the thermal diffusivity, here called $\alpha$, for Section 2. Then, run all Sections 0 to 4 to get a result. If you want to change the parameter alpha afterwards, rerun Section 2-4 after changing alpha__

You can run the cells either by clicking on the cell and then on Run or press ctrl+enter

### Differential Heat Equation 

![equation](https://latex.codecogs.com/png.latex?\Large&space;\frac{\partial{T(x,y,t)}}{\partial{t}}&space;=&space;\alpha\&space;(\frac{\partial^2{T(x,y,t)}}{\partial^2{x}}&space;&plus;&space;\frac{\partial^2{T(x,y,t)}}{\partial^2{y}}&space;)
)


To solve this partial differential equation (PDE), we need to define one initial condition (accounting for time) and four boundary conditions (accounting for space)

Initial condition:
- ![equation](https://latex.codecogs.com/png.latex?\inline&space;T(x\neq&space;0,y,t=0)&space;=&space;T_{initial}) At time t=0, the rest of the plate is cold

The plate is assumed to be adiabatic. Hence, the temperature function's change on the edges of the plate is zero. This can be formulated into the following boundary conditions:

Boundary conditions:
- ![equation](https://latex.codecogs.com/png.latex?\frac{\partial{T(x,y,t)}}{\partial{x}}&space;=&space;0&space;\&space;$&space;for&space;$&space;x=0&space;\&space;$&space;or&space;\&space;x=w&space;\)) (w = plate's width) 

- ![equation](https://latex.codecogs.com/png.latex?\frac{\partial{T(x,y,t)}}{\partial{y}}&space;=&space;0&space;\&space;$&space;for&space;$&space;y=0&space;\&space;$&space;or&space;\&space;x=h&space;\)) (h = plate's height) 

To account for the isothermal left side, we will furthermore define a constraint:

- ![equation](https://latex.codecogs.com/png.latex?T(x=0,y,t)&space;=&space;T_{hot}) : We assume that at all time, the left edge of the plate is at temperature ![equation](https://latex.codecogs.com/png.latex?\inline&space;T_{hot})


### Finite Difference Discretization of Temperature equation
For a ![equation](https://latex.codecogs.com/png.latex?\inline&space;x_n,&space;y_n&space;\&space;and&space;\&space;time&space;\&space;t_n) the temperature ![equation](https://latex.codecogs.com/png.latex?\inline&space;T_{x_n,y_n}^{n&plus;1}) at the next time step is approximated by:

![equation](https://latex.codecogs.com/png.latex?\inline&space;\Large&space;T_{x_n,y_n}^{t_{n&plus;1}}&space;=&space;T_{x_n,y_n}^{t_n}&space;&plus;&space;\alpha&space;\Delta&space;t&space;(\frac{T_{x_n,y_{n&plus;1}}^{t_n}&space;-&space;2&space;T_{x_n,y_{n}}^{t_n}&plus;&space;T_{x_n,y_{n-1}}^{t_n}}{\Delta&space;y^2}&space;&plus;&space;\frac{T_{x_{n&plus;1},y_{n}}^{t_n}&space;-&space;2&space;T_{x_n,y_{n}}^{t_n}&space;&plus;&space;T_{x_{n-1},y_{n}}^{t_n}}{\Delta&space;x^2}))

[![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/maxtheisen/lecture_hmt/main?urlpath=https%3A%2F%2Fgithub.com%2Fmaxtheisen%2Flecture_hmt%2Fblob%2Fmain%2FTransportPhenomenaLab.ipynb)
