# Parkinson's Monitoring System
### Hardware-Software Co-Design on Zynq-7000 SoC (ZedBoard)

## 📌 Project Overview
This project implements an end-to-end diagnostic pipeline to detect Parkinson's Disease through the analysis of spiral drawing patterns. By leveraging the **Zynq-7000 SoC**, the system combines a high-level Python-trained neural network with custom FPGA hardware acceleration to achieve high-speed, real-time inference.

---

## 🛠 Engineering Workflow
The repository is structured to reflect the complete development lifecycle, from model training to hardware deployment:

### 📂 [01_ML_Model_Python](./01_Python)
* **Objective**: Train the diagnostic "brain" using deep learning.
* **Activities**: 
    * Dataset preprocessing and normalization of spiral images to $128 \times 128$ resolution.
    * Convolutional Neural Network (CNN) construction using TensorFlow and Keras.
    * Exporting trained weights into a C++ header (`weights.h`) for hardware compatibility.

### 📂 [02_Vitis_HLS_IP](./02_Vitis_HLS)
* **Objective**: Transform software logic into hardware RTL.
* **Activities**: 
    * Developing HLS-optimized C++ kernels to implement the CNN layers.
    * Generating a custom IP core to be used in the Vivado Block Design.

### 📂 [03_Vivado_Hardware](./03_Vivado)
* **Objective**: SoC Architecture Design and Integration.
* **Activities**: 
    * Integrating the HLS IP with the Zynq Processing System (PS) via AXI4 interconnects.
    * Configuring hardware constraints and generating the bitstream for the ZedBoard.

### 📂 [04_Vitis_IDE_App](./04_Vitis_ide)
* **Objective**: Embedded Software Deployment.
* **Activities**: 
    * Developing the final C application to manage data flow between the ARM processor and FPGA logic.
    * System verification using "Golden Logits" to ensure hardware-software parity.

---

## 🚀 Hardware & Tools
* **Development Board**: Avnet ZedBoard (Zynq-7000)
* **Camera Sensor**: OV7670 (connected via Pmod/GPIO)
* **Software Stack**: Vivado ML, Vitis HLS, Vitis IDE, and Google Colab (Python 3)

---
# Images and Results

---

## Experimental Setup

<p align="center">
  <img src="Images/Experiment_setup.jpg" width="700"/>
</p>

<p align="center">
  <em>
    Real-time experimental setup consisting of the Zynq-7000 ZedBoard,
    OV7670 camera module, VGA display, and live handwriting acquisition platform.
  </em>
</p>

---

## Healthy Control Handwriting Sample

<p align="center">
  <img src="Images/HandPD_H.jpg" width="350"/>
</p>

<p align="center">
  <em>
    Sample handwriting image from a healthy control subject used for CNN training and testing.
  </em>
</p>

---

## Parkinson’s Disease Handwriting Sample

<p align="center">
  <img src="Images/HANDPD_PD.jpg" width="350"/>
</p>

<p align="center">
  <em>
    Sample handwriting image from a Parkinson’s Disease patient showing motor irregularities.
  </em>
</p>

---

## Meander Healthy Sample

<p align="center">
  <img src="Images/meander_hc.jpg" width="350"/>
</p>

<p align="center">
  <em>
    Meander drawing pattern from a healthy subject.
  </em>
</p>

---

## Meander Parkinson’s Sample

<p align="center">
  <img src="Images/meander_pd.jpg" width="350"/>
</p>

<p align="center">
  <em>
    Meander drawing pattern from a Parkinson’s Disease patient.
  </em>
</p>

---

## Hardware and Camera Interface

<p align="center">
  <img src="Images/HW_Camera_Interface.jpg" width="500"/>
</p>

<p align="center">
  <em>
    Hardware integration of OV7670 camera module with ZedBoard for real-time image capture.
  </em>
</p>

---

## Hardware–Software Co-simulation

<p align="center">
  <img src="Images/HW_SW_COSIM.png" width="700"/>
</p>

<p align="center">
  <em>
    Hardware–software co-simulation results validating CNN accelerator functionality.
  </em>
</p>

---

## Simplified SoC Architecture

<p align="center">
  <img src="Images/simplified_soc_schematic.png" width="750"/>
</p>

<p align="center">
  <em>
    Simplified AXI-based Zynq SoC architecture integrating Processing System and CNN accelerator.
  </em>
</p>

---

## Workflow Diagram

<p align="center">
  <img src="Images/workflow.png" width="750"/>
</p>

<p align="center">
  <em>
    Complete software-to-hardware workflow for CNN model deployment using Vivado HLS.
  </em>
</p>

---

## Spiral Curve Accuracy and Loss

<p align="center">
  <img src="Images/Spiral_Curves.png" width="700"/>
</p>

<p align="center">
  <em>
    Training and validation accuracy/loss curves for spiral handwriting classification.
  </em>
</p>

---

## Meander Curve Accuracy and Loss

<p align="center">
  <img src="Images/Meander_Curves.png" width="700"/>
</p>

<p align="center">
  <em>
    Training and validation accuracy/loss curves for meander handwriting classification.
  </em>
</p>

---

## Spiral Power Consumption

<p align="center">
  <img src="Images/spiral_power.png" width="500"/>
</p>

<p align="center">
  <em>
    On-chip power consumption breakdown for spiral image processing.
  </em>
</p>

---

## Meander Power Consumption

<p align="center">
  <img src="Images/meander_power.png" width="500"/>
</p>

<p align="center">
  <em>
    On-chip power consumption breakdown for meander image processing.
  </em>
</p>

---

## Real-Time Prediction Output

<p align="center">
  <img src="Images/Prediction.jpg" width="500"/>
</p>

<p align="center">
  <em>
    Real-time Parkinson’s Disease prediction output displayed during live inference.
  </em>
</p>

---

---

## 📊 Performance
The model utilizes optimized CNN layers to identify tremors with high precision. Detailed accuracy charts and loss curves are located in the [01_ML_Model_Python](./01_ML_Model_Python) folder.
