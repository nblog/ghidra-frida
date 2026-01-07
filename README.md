## ghidra-frida: 
- Description: support for Frida-based analysis using the Ghidra traceRMI
- Author: d-millar

---

## Build Guide

### Step-by-Step Compilation Instructions

#### Clone the Repository
`~\repos\ghidra$`
```bash
git clone https://github.com/nblog/ghidra-frida Ghidra/Debug/Debugger-agent-xfrida
```

#### Download Python Dependencies
```bash
pip download Ghidra/Debug/Debugger-agent-xfrida/src/main/py --dest Ghidra/Debug/Debugger-agent-xfrida/src/main/py/dist
```
Note: Since `protobuf` is already imported by default, it can be removed.

#### Initialize and Fetch Dependencies
```bash
.\gradlew -I gradle/support/fetchDependencies.gradle
```
This command initializes the Gradle environment and downloads all required dependencies specified in the build configuration.

#### Build the Python Package
```bash
.\gradlew :Debugger-agent-xfrida:assemblePyPackage
```
This builds the Python package that integrates Frida with Ghidra's trace RMI interface.

#### Package as Ghidra Extension (ZIP)
```bash
.\gradlew :Debugger-agent-xfrida:zipExtensions
```
This creates a standalone ZIP extension package that can be installed via Ghidra's `File > Install Extensions` menu.

The output file will be located at:
```
build/dist/ghidra_<version>_<date>_Debugger-agent-xfrida.zip