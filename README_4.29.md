

## 4.29_FD_2D_faultzone
### 2D Finite difference simulation of trapped waves in a fault zone

#### Modeling waves using the scalar wave equation


<div style="width:20%; float:right; padding-left:25px; padding-right:25px; text-align:center;">
  <img src="lovewave.gif">
  <span style="font-size:smaller; display:block; line-height:1.2;">
    Love wave. [britannica.com]
  </span>
</div>

In an SH wave, the particle motion is in the horizontal plane and is also perpendicular to the direction of the wave’s travel. For example, a Love wave is a type of SH wave in which the direction of propagation and direction of particle motion are perpendicular to each other, but both lie in the plane of the earth’s surface. 

Another example is an S-wave (a transverse seismic wave) traveling through a plane of cross-section, with particle motion perpendicular to the direction of travel. This is the situation we’ll use in this problem. <br>

<center>
    <img src="s-wave.gif" style="width:30%;">
  <span style="font-size:smaller; display:block; line-height:1.2;">
    S-wave. [britannica.com]
  </span>
</center>

<br>It turns out that in 2D the math behind SH wave propagation is equivalent to that of an acoustic wave, so we can use the acoustic wave equation to model it:<br>

$$\partial_t^2 p(x, z, t) = c(x, z)^2 (\partial^2_x p(x, z, t) \partial^2_z p(x, z, t)) + s(x, z,t),$$

where we model the source $s(t)$ of the wave as a point in 2D using a rather arbitrary Gaussian function. In this scenario, we can refer to the equation as the scalar wave equation.

#### Finite-difference solution

So, what we have is a second-order partial differential equation in space and time. By manipulating the definition of the derivative, we come up with a "3-point" finite-difference scheme to obtain a numerical solution. (This requires an iterative process of looking one time step forward while simultaneously looking at the neighboring spatial points in two dimensions. See notebook for the math.)

<div style="width:35%; float:right; padding-left:50px; padding-right:50px; text-align:center;">
  <img src="4.29_Greens.png" style="width:100%;">
</div>


#### Comparing the analytical solution

The above equations will determine our numerical solution, but we'd also like to obtain an analytical solution to check our work. To do this, we need to use the established Green's function for the 2D acoustic equation (see exercise for the definition). In 2D, the Green's function is essentially a "spike" with a rapidly attenuating tail. Since we've already defined the source function, we can again get the solution by convolution: 

$$p(t) = G(t) * s(t)$$



<center>
    <img src="4.29_sol_compare.png" style="width:50%;">
</center>

