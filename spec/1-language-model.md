# Language Model

## Test Program Package
A QTL test program contains the following source files:
- Test sequence source code file
- Config and limit values file
- Optional: Test assets (e.g. waveforms)

The source code is compiled into executable VM bytecode and packaged with the config/limits and assets files (package tbd) before being made available to test units alongside the config/limit file and any test assets.
- TODO: consider options for signing/verifying versions, possibly out of scope for the language?

## Program Structure

TODOs:
- sections: metadata, init, test
- mapping in values from limit file (+ identifiers)

TODOs - metadata:
- aliasing resources (e.g. input pin given name that identifies net on DUT)
- setting up resources & resource pin mapping/direction
- dut/fixture id
