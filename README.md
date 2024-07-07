# SDR FPGA for GSM-R Tester

## Table of Contents
- [Introduction](#introduction)
- [Project Structure](#project-structure)
- [System Requirements](#system-requirements)
- [Dependencies](#dependencies)
- [Setup](#setup)
- [Download and Replace `radio_legacy.v`](#download-and-replace-radio_legacyv)
- [Build the FPGA image](#build-the-fpga-image)
- [Testing](#testing)
- [Contributing](#contributing)
- [License](#license)

## Introduction
This project involves developing FPGA code to enhance the functionality of the Ettus Research B200mini SDR for use in a GSM-R (Global System for Mobile Communications - Railway) testing environment. The enhancements include adding an adjustable RF front-end and implementing custom control interfaces.

This project is customized based on the following source: [Ettus Research UHD Repository](https://github.com/EttusResearch/uhd/tree/master/fpga/usrp3/top/b2xxmini).

## Project Structure
The repository is organized as follows:
- `src/`: Contains the FPGA source code.
- `docs/`: Contains documentation related to the project.
- `scripts/`: Contains scripts for building and testing the FPGA code.
- `examples/`: Contains example configurations and usage scenarios.

## System Requirements
- Operating System: Windows 10 (for Xilinx ISE), Virtual Box Linux (for running scripts and software)
- Hardware: Ettus Research B200mini SDR, USB 3.0 port

## Dependencies
The following dependencies are required for building and running the project:
- Xilinx ISE Design Suite (version 14.7 for Windows 10)
- UHD (USRP Hardware Driver)
- GCC (for building control software)
- Python (for running setup and utility scripts)

## Setup
1. **Clone the repository**:
   ```bash
   git clone https://github.com/superbabii/FPGA-of-USRP-B2xx-board.git
   cd FPGA-of-USRP-B2xx-board
   ```
2. **Clone the EttusResearch/uhd repository**:
   ```bash
   git clone https://github.com/EttusResearch/uhd.git
   cd uhd
   git checkout master
   cd ..
   ```

3. **Replace the `fpga/usrp3/top/b2xxmini` folder**:
   ```bash
   rm -rf uhd/fpga/usrp3/top/b2xxmini
   cp -r FPGA-of-USRP-B2xx-board/src uhd/fpga/usrp3/top/b2xxmini
   ```

4. **Install the necessary dependencies**:
   ```bash
   sudo apt-get install uhd-host gcc python3
   ```

5. **Install Xilinx ISE Design Suite 14.7 for Windows 10**:
   - Download and install from the [Xilinx website](https://www.xilinx.com/support/download/index.html/content/xilinx/en/downloadNav/design-tools.html).
   - Follow the installation guide provided in the package.

6. **Refer to the Ettus Research build instructions for installation, setup, and build**:
   - [USRP3 Build Instructions](https://files.ettus.com/manual/page_build_guide.html)

## Download and Replace `radio_legacy.v`
1. **Download the `radio_legacy.v` file**:
   - Download the file from the following URL: [radio_legacy.v](https://drive.google.com/file/d/1jXr1t0q7j_bo5dVSHTVZvg0ekwtskPF0/view?usp=sharing)

2. **Replace the existing `radio_legacy.v` file**:
   ```bash
   cp /path/to/downloaded/radio_legacy.v uhd/fpga/usrp3/lib/radio_200/radio_legacy.v
   ```

## Build the FPGA image
1. **Run the Make file on the Ubuntu environment of Virtual Box of ISE 14.7 (Windows 10)**:
   ```bash
   cd uhd/fpga/usrp3/top/b2xxmini
   make
   ```

2. **Open the configured ISE project with ISE and build to create bin or bit file for programming to FPGA**:
   - Open the ISE project file located in `uhd/fpga/usrp3/top/b2xxmini` using Xilinx ISE.
   - Follow the build instructions within ISE to generate the bin or bit file.

## Testing
- **Testing the FPGA image**:
  - Instructions on how to test the loaded FPGA image to ensure it works correctly.
  
- **Testing the control software**:
  - Steps to verify the control software functionality, including sample commands and expected outputs.

## Contributing
Contributions are welcome! Please follow these steps:
1. Fork the repository.
2. Create a new branch (`git checkout -b feature-branch`).
3. Make your changes and commit them (`git commit -am 'Add new feature'`).
4. Push to the branch (`git push origin feature-branch`).
5. Create a new Pull Request.

## License
This project is licensed under the MIT License. See the LICENSE file for details.
