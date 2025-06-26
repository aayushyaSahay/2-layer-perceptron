# FPGA-Based Multi-Class 2-layer Perceptron Classifier

This project implements a **2-layer Perceptron** inference engine on the Basys3 FPGA board using VHDL. The system classifies a 16-bit input vector into one of two categories (e.g., Safe/Unsafe, Introvert/Extrovert), using **fixed-point weights** and **pre-trained models**.

## 🧠 Architecture

- **Input Layer**: 16 binary switches (features)
- **Hidden Layer**: 4 neurons (fixed weights + threshold)
- **Output Layer**: 1 neuron (binary class output)

## 🎮 Features

- **Multiple Classifier Modes**: Toggle between classifiers using push buttons (e.g., political alignment, personality type).
- **Mode Display**: Current mode shown on 7-segment or LEDs.
- **Inference Engine**: All computation in fixed-point arithmetic, with mode-specific weights loaded from memory.

## 📂 VHDL Module Structure

| Filename               | Description                                           |
|------------------------|-------------------------------------------------------|
| `top_level.vhdl`       | Top module connecting inputs, layers, and outputs     |
| `input_switches.vhdl`  | Reads and debounces the 16 input switches             |
| `hidden_layer.vhdl`    | 4 neurons, computes weighted sums and applies activation |
| `output_layer.vhdl`    | Single neuron combining hidden layer outputs          |
| `weights_pkg.vhdl`     | Pre-trained weights and biases for each mode          |
| `mode_controller.vhdl` | FSM to switch between classifier modes using buttons  |
| `seven_segment.vhdl`   | Displays mode or output class                         |
| `testbench.vhdl`       | Simulation testbench for 2-layer inference            |

## ⚙️ Modes Implemented

1. Introvert vs Extrovert  
2. Liberal vs Conservative  
3. Safe vs Unsafe Hardware Config  
4. (Optional: Spam vs Non-Spam, etc.)

## 🔄 Mode Switching

- Use push buttons to cycle through modes (debounced FSM)
- Each mode loads a different set of weights from `weights_pkg.vhdl`

## 📈 Workflow

1. Design datasets in Python (16-bit binary input + binary label)  
2. Train 2-layer perceptrons using `scikit-learn`  
3. Export weights, quantize to fixed-point  
4. Implement logic in VHDL and test on Basys3  
5. Toggle modes via button, see results live

## 👨‍💻 Author
Aayushya Sahay — IIT Delhi
