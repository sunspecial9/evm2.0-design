# EVM2 Design
> This repository contains documents describing the design and high-level overview of EVM 2.0. Expect the contents of this repository to be in flux: everything is still under discussion.

The goal for this repository is to track research and development of alternative VM's for use in Ethereum.
Currently eWASM has had the most research.

## What is WebAssembly?

> WebAssembly (or WASM for short) is a new, portable, size- and load-time-efficient format. WebAssembly is currently being designed as an open standard by a W3C Community Group.

Please review the [WebAssembly design and instruction set](https://github.com/WebAssembly/design) first.

A few key points:
* WebAssembly defines an instruction set, intermediate source format (WAST) and a binary encoded format (WASM).
* WebAssembly has a few higher level features, such as the ability to import and execute outside methods defined via an interface.
* LLVM includes a WebAssembly backend to generate WASM output.
* Multiple JIT or interpreted VMs exist for WASM. Notably the V8 Javascript engine includes one, which is used in both Node.js and Chrome. Firefox has its own VM implementation.

## What is Ethereum flavored WebAssembly (eWASM)?

eWASM is a restricted subset of WASM to be used for contracts in Ethereum.

eWASM:
* specifies the [semantics for an *eWASM contract*](./contract_interface.md)
* specifies an [Ethereum environment interface](./eth_interface.md) to facilitate interaction with the Ethereum environment from an *eWASM contract*
* specifies [metering](./metering.md) for instructions
* and aims to restrict [non-deterministic behavior](https://github.com/WebAssembly/design/blob/master/Nondeterminism.md)

### Goals of the eWASM project

* To provide a specification of *eWASM contract* semantics and the *Ethereum interface*
* To provide an *EVM transpiler*, preferably as an eWASM contract
* To provide a *metering injector*, preferably as an eWASM contract
* To provide a VM implementation for executing eWASM contracts
* To implement an eWASM backend in the Solidity compiler
* To provide a library and instructions for writing contracts in Rust
* To provide a library and instructions for writing contracts in C

### Glossary

* *eWASM contract*: a contract adhering to the eWASM specification
* *Ethereum environment interface (EEI)*: a set of methods available to eWASM contracts
* *metering*: the act of measuring execution cost in a deterministic way
* *metering injector*: a transformation tool inserting metering code to an eWASM contract
* *EVM transpiler*: an EVM bytecode (the current Ethereum VM) to eWASM transcompiler

### Resources

* [FAQ](./faq.md)
* [Rationale](./rationale.md)
* [Ethereum environment interface](./eth_interface.md)
* [eWASM Contract Interface](./contract_interface.md)
* [Original Proposal](https://github.com/ethereum/EIPs/issues/48) (EIP#48)
* [WebAssembly design documents](https://github.com/WebAssembly/design)

### Projects

* [ewasm-tests](https://github.com/ewasm/ewasm-tests)
* [wasm-metering](https://github.com/ewasm/wasm-metering)
* [ewasm-kernel](https://github.com/ewasm/ewasm-kernel)
* [evm2wasm](https://github.com/ewasm/evm2wasm)
* [c-libeth](https://github.com/ewasm/c-libeth)
* [rust-libeth](https://github.com/ewasm/rust-libeth)

### Design Process & Contributing
For now, high-level design discussions should continue to be held in the design repository, via issues and pull requests. Feel free to file [issues](https://github.com/ethereum/ewasm-design/issues).

## Chat
[Gitter](https://gitter.im/ethereum/ewasm-design)
