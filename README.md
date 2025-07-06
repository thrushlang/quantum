<p align="center">
  <img src= "https://github.com/thrushlang/thrushc/blob/master/assets/thrushlang-v1.6.png" alt= "logo" style= "width: 2hv; height: 2hv;"> </img>
</p>

# Quantum programming

There are plans to enable **quantum programming support** for the Thrush Programming Language. Here we explain how we could implement it.

# > ¿What is Quantum Programming?

**Quantum programming** is the development of software for quantum computers, which use principles of quantum mechanics, such as superposition and entanglement, to perform calculations. Unlike classical bits (0 or 1), qubits in quantum computing can be in multiple states simultaneously, allowing certain problems, such as factoring large numbers or simulating molecules, to be solved more efficiently than traditional computers.

# > We have problems.

The infrastructure of **[LLVM](https://llvm.org/)** and **[MLIR](https://mlir.llvm.org/)** is not yet stable enough to generate intermediate code for quantum computers. So we have to resort to other methods.

In addition to this, although there are dialects and infrastructures to generate quantum code, they are very complex and not available in Rust, in a conventional way, through some type of constructor or bridge.

# > Q# is the solution.

**[Q#](https://github.com/microsoft/qsharp)** is a quantum programming language created by **Microsoft**.

This language has a compilation to multiple intermediate representations, which can be taken by IBM quantum compilers, Rigetti or Quantinuum, and translated into instructions valid for quantum computers.
Using this language in a manner that allows Thrush to be ported to it would be beneficial to add support for Thrush in this area of computing.

The quantum compiler for the Thrush programming language would be **thrushqc**. This would be responsible for transferring the Thrush programming language code into Q# code so that it can then be compiled.

`thrushqc test.th`

# > QIR is the other solution.

**[QIR](https://qir-alliance.org/)** is an intermediary representation on top of LLVM IR, which can be executed by quantum backends such as those from Rigetti and IBM or even Azure.

This intermediate representation is used by Microsoft's current Q# to compile and emulate quantum code. 

This QIR is simply an LLVM IR, providing support for linking to runtime functions that emulate the operation of a quantum component.
It can also be taken and run on IBM, Rigetti, Azure, and Quantinuum executors.

The same LLVM-C API can be utilized to create this specialized IR and dispatch it at compile time for users to employ in any executor that supports QIR.

It can also be executed by embedding the QIR compiler, unpacking it during the main compiler installation, and utilizing it to emulate the runtime.

------------

Although this is a **superficial introduction**, it is the very future idea of ​​implementing support for quantum programming by Thrush Programming Language, opening a new era in programming languages.
