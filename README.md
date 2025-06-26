<p align="center">
  <img src= "https://github.com/thrushlang/thrushc/blob/master/assets/thrushlang-v1.5.png" alt= "logo" style= "width: 2hv; height: 2hv;"> </img>
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

By creating a compiler, you could port your thrush programming language code to Q#. Q# can then compile it excellently into code for quantum computers.

The quantum compiler for the thrush programming language would be **thrushqc**. This would be responsible for transferring the thrush programming language code into Q# code so that it can then be compiled.

`thrushqc test.th`

# > QIR is the other solution.

**[QIR](https://qir-alliance.org/)** is an intermediary representation on top of LLVM IR, which can be executed by quantum backends such as those from Rigetti and IBM or even Azure.

This intermediate representation is very similar to LLVM IR, so I can directly use the LLVM C infrastructure around it and generate the intrinsics that emulate the behavior of quantum programming.

The process is repeated, and a compiler is created that outputs this portable IR format to be used in quantum executors.

------------

Although this is a **superficial introduction**, it is the very future idea of ​​implementing support for quantum programming by Thrush Programming Language, opening a new era in programming languages.
