# HPhiJulia.jl
Julia 1.0 wrapper for the HPhi.
This just calls HPhi from Julia.
Now this is very limited. 
I confirmed that this can work on Ubuntu and Mac OS 10.13. 

# HPhi 
Quantum Lattice Model Simulator Package
https://github.com/issp-center-dev/HPhi

HPhi is installed in "~/.julia/packages/HPhiJulia".
At the first time, the HPhi 3.1.2 is downloaded and installed. 


# Install 
Push ] to enter the package mode of Julia 1.0.

```julia
add https://github.com/ultimatile/HPhiJulia.jl
```

# models, methods,lattices
We can see 

```julia
using HPhiJulia
println(HPhiJulia.models)
println(HPhiJulia.methods)
println(HPhiJulia.lattices)
```

# Examples

## Heisenberg model on a 2D square lattice

```julia
using HPhiJulia
L = 4
W = 4
J = 1
results = HPhiJulia.HPhi("Spin","square",W,L,J=J,mpinum=1)
println(results["Energy"])
```

## Hubbard model on a 2D square lattice

```julia
using HPhiJulia
L = 2
W = 2
U = 8
t = 1
nelec = 4
results =  HPhiJulia.HPhi("Hubbard","square",W,L,U=U,t=t,nelec=nelec)
println(results["Energy"])
```
To obtain the eigenvector:

```julia
using HPhiJulia
L = 2
W = 2
U = 8
t = 1
nelec = 4
results,evec =  HPhiJulia.HPhi("Hubbard","square",W,L,U=U,t=t,nelec=nelec,expart=true,OutputEigenVec=true)
println(results["Energy"])
println(evec)
```
