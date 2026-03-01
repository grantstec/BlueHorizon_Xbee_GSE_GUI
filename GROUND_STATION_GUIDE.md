# KestrelSAT Ground Control Station - Setup Guide

This guide explains how to install, run, and compile the modified Ground Control Station (GCS) software for the KestrelSAT project.

## 1. Prerequisites
Ensure you have Python 3.8+ installed.

## 2. Setting Up the Environment
Open a terminal in the project directory and run:

```bash
# Create a virtual environment (if not already done)
python -m venv .venv

# Activate the virtual environment (Windows)
.venv\Scripts\Activate.ps1

# Install required packages
pip install -r requirements.txt
```

## 3. Running the GUI
To run the ground station interface:

```bash
python serial_gui.py
```

## 4. Compiling to .EXE
To create a standalone executable that can be run on any Windows PC without Python installed:

1. Double-click `build_exe.bat`
   OR run from terminal:
   ```cmd
   build_exe.bat
   ```

2. The output file `SerialGUI.exe` will be located in the `dist/` folder.

## 5. Using the Ground Station Protocol

### Connection
- Select the COM port for your XBee module/adapter.
- Set the Baud Rate (ensure it matches your XBee configuration).
- Click **Connect**.

### Telemetry Display
- The new "Ground Station" tab displays live telemetry:
  - **Pressure (PT)**: PSI value
  - **Tank Thrust**: lbs
  - **Engine Thrust**: lbs
  - **Continuity**: Launch/Spare Pyro status (Green=Good/1, Red=Bad/0)
  - **System State**: Current state (UNARMED, ARMED, etc.)

### Sending Commands
- Use the **Command Center** buttons (DISARM, ARM, LOAD, etc.).
- The system will send `CMD,[OP_CODE],[MSG_ID]` and wait for an `ACK,[MSG_ID]`.
- Status of the command and retries will be shown below the buttons.

### Plotting
- Switch to the **Plot** tab to see real-time graphs of the telemetry data.
- The new protocol automatically maps:
  - `PT`, `Tank_Thrust`, `Engine_Thrust`, `Cont1`, `Cont2`, `State` as plot channels.
