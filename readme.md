# STM32 AI Deployment Setup

### (PyTorch CNN → NUCLEO-N657X0-Q)

This document describes the minimal toolchain and installation process used to deploy and test a CNN model on an STM32 NUCLEO-N657X0-Q board.

---

## 1. Python Environment (Model Development)

**Purpose:** Model training, ONNX export, and validation data preparation.

### Required Tools

- Python (64-bit)
- PyTorch
- NumPy
- ONNX
- ONNX Runtime

### Links

- Python: https://www.python.org/downloads/
- PyTorch: https://pytorch.org/get-started/locally/
- ONNX: https://onnx.ai/
- ONNX Runtime: https://onnxruntime.ai/

---

## 2. STM32CubeMX (Standalone)

**Purpose:** Hardware configuration and middleware management.

### Key Functions

- Select target board (NUCLEO-N657X0-Q)
- Configure MCU and peripherals
- Manage STM32 software packs

### Important Note

- Automatically creates STM32Cube Repository:

- No manual installation required for the repository.

### Link

- STM32CubeMX: https://www.st.com/en/development-tools/stm32cubemx.html

---

## 3. X-CUBE-AI Expansion Package

**Purpose:** AI model optimization, quantization, and code generation.

### Installation

- Installed via STM32CubeMX:
- Software Packs → Manage Software Packs → X-CUBE-AI

### Features

- ONNX model parser
- Quantization (INT8)
- STM32N6 backend support
- Code generation utilities
- Validation tools

### Link

- X-CUBE-AI: https://www.st.com/en/embedded-software/x-cube-ai.html

---

## 4. STM32 Edge AI CLI (stedgeai)

**Purpose:** Model conversion, optimization, and validation.

### Notes

- Installed automatically with X-CUBE-AI
- No separate installation required

### Key Commands

- `generate` → Model conversion & optimization
- `validate` → Target-aware validation

---

## 5. STM32CubeIDE

**Purpose:** Firmware compilation, flashing, and debugging.

### Features

- ARM GCC toolchain
- Build system
- Debugging support
- Flashing to STM32 hardware

### Link

- STM32CubeIDE: https://www.st.com/en/development-tools/stm32cubeide.html

---

## 6. ST-LINK Server

**Purpose:** Hardware communication, flashing, and debugging backend.

### Notes

- Replaces legacy ST-LINK USB driver
- Enables communication between STM32CubeIDE and the NUCLEO board

### Link

- ST-LINK Server: https://www.st.com/en/development-tools/st-link-server.html

---

## Installation Order

1. Python + required libraries
2. STM32CubeMX (standalone)
3. X-CUBE-AI (via CubeMX)
4. STM32CubeIDE
5. ST-LINK Server

---

## Workflow Summary

```text
PyTorch Model → ONNX → X-CUBE-AI (stedgeai)
→ Code Generation → STM32CubeIDE → Flash to NUCLEO-N657X0-Q
```
