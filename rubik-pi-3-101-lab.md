# Lab: RUBIK Pi 3 101 — Hardware Assembly, ARM Architecture, and Linux

**Level:** Beginner  
**Platform:** Windows / macOS  
**Hardware:** Qualcomm RUBIK Pi 3  
**Format:** Hands-on lab (students work in pairs)

---

## 1. Lab Overview

The RUBIK Pi 3 is a single-board computer powered by the Qualcomm QCS6490 processor. It provides a platform for learning embedded computing, ARM architecture, Linux, and hardware interfacing.

In this lab, you will explore the RUBIK Pi 3 hardware, install a heatsink and cooling fan, learn about ARM-based processors, and connect to the board using serial communication.

You will also execute basic Linux commands to investigate the computer's hardware and operating system.

**No operating-system installation, flashing, or machine learning is required.**

### Learning Objectives

By the end of this lab, you should be able to:

1. Identify the major components and interfaces of the RUBIK Pi 3.
2. Explain the difference between ARM and x86 processor architectures.
3. Explain why processors require thermal management.
4. Safely install a compatible heatsink and cooling fan.
5. Describe the basic boot process of an embedded Linux computer.
6. Establish a serial connection using Windows or macOS.
7. Execute basic Linux commands to inspect system information.

---

## 2. Required Equipment

Each student pair should have access to:

- Qualcomm RUBIK Pi 3
- Compatible heatsink and cooling fan kit
- Manufacturer-specified thermal pads
- Laptop running Windows or macOS
- Micro-USB data cable
- Suitable USB-C power adapter
- PuTTY (Windows) or Terminal (macOS)
- Small screwdriver, if required by the cooling kit

### Safety Rules

**Read before beginning:**

1. Keep the RUBIK Pi disconnected from power during hardware assembly.
2. Handle the board by its edges whenever possible.
3. Avoid touching exposed electronic components and connector contacts.
4. Use ESD precautions and work on a clean, nonconductive surface.
5. Do not force the heatsink, mounting clips, or fan connector.
6. Use only the approved thermal pads and mounting hardware.
7. Do not connect power until the instructor has inspected the installation.
8. Connect the USB-C power supply last.

---

## Part A: Introduction to RUBIK Pi 3

### Activity 1: Identify Hardware Components

Examine the RUBIK Pi 3 board.

Identify the following components:

| Component | Function |
|---|---|
| Qualcomm QCS6490 | Main processing system |
| RAM | Temporary storage for running programs |
| UFS storage | Nonvolatile storage for the OS and files |
| Micro-USB DEBUG | Serial console |
| USB-C power connection | Power supply |
| HDMI | External display |
| Ethernet | Wired network |
| USB | Peripheral connectivity |
| GPIO header | Hardware interfacing |

### Questions

1. What is a single-board computer?
2. How is the RUBIK Pi different from a desktop computer?
3. What is the difference between RAM and UFS storage?
4. Why does the board provide GPIO pins?

---

## Part B: ARM Architecture and Boot Process

### Activity 2: ARM vs. x86

The RUBIK Pi 3 uses an ARM-based processor.

An Instruction Set Architecture (ISA) defines the instructions that a processor can execute.

| Computer | Typical architecture |
|---|---|
| RUBIK Pi 3 | ARM64 |
| Apple Silicon Mac | ARM64 |
| Intel/AMD Windows laptop | x86-64 |
| Raspberry Pi 5 | ARM64 |

### Questions

1. What does ARM stand for?
2. What is an Instruction Set Architecture?
3. What is the difference between ARM64 and x86-64?
4. Why is ARM commonly used in embedded systems?

### Activity 3: Understand the Boot Process

When the RUBIK Pi receives power, firmware initializes the system and starts the operating system.

A simplified boot process is:

```text
Power On
    |
    v
Boot Firmware
    |
    v
Bootloader
    |
    v
Linux Kernel
    |
    v
System Initialization
    |
    v
Login / Command Shell
```

### Questions

1. What is the purpose of a bootloader?
2. What does the Linux kernel do?
3. Why can a serial console be useful when the operating system fails to boot?

---

## Part C: Installing the Heatsink and Cooling Fan

### Activity 4: Thermal Management

Modern processors generate heat while executing instructions.

If processor temperature becomes too high, the system may reduce its operating frequency to prevent overheating. This is known as **thermal throttling**.

A cooling system helps transfer heat away from the processor.

### Understand the Components

| Component | Purpose |
|---|---|
| Heatsink | Transfers heat away from the chip and increases the surface area for cooling |
| Thermal pad | Improves thermal contact between the chip and heatsink |
| Cooling fan | Moves air across the heatsink |
| Fan connector | Supplies power and, where supported, control signals to the fan |

### Activity 4.1: Inspect the Cooling Kit

Before installation:

1. Identify the heatsink.
2. Locate the cooling fan.
3. Examine the thermal pads.
4. Identify the mounting points.
5. Locate the board's fan connector using the official hardware diagram.

**Do not remove the protective film from the thermal pads until you are ready to install them.**

### Activity 4.2: Install the Cooling System

Follow the manufacturer's instructions for your exact cooling kit.

1. Verify that the RUBIK Pi is completely powered off and disconnected.
2. Place the board on a clean, nonconductive surface.
3. Identify the SoC and memory components that require thermal contact.
4. Remove the protective film from the approved thermal pads.
5. Position the pads according to the manufacturer's installation diagram.
6. Align the heatsink with the mounting points.
7. Carefully secure the cooler using the supplied mounting mechanism.
8. Connect the fan cable to the correct fan header.
9. Check that the fan cable cannot touch moving fan blades.
10. Ask the instructor to inspect the installation before applying power.

**Important:** Do not guess the thermal-pad placement, thickness, or fan-header orientation. Use the instructions supplied with the exact cooler. Do not apply thermal paste unless the kit specifically requires it.

### Activity 4.3: Verify the Installation

Before powering on, confirm:

- [ ] Heatsink is properly aligned.
- [ ] Thermal pads are correctly positioned.
- [ ] Mounting hardware is secure without excessive force.
- [ ] Fan connector is correctly attached.
- [ ] Fan blades can rotate freely.
- [ ] No loose screws, tools, or conductive objects remain on the board.
- [ ] Instructor has approved the installation.

### Questions

1. Why does the processor generate heat?
2. What is the purpose of a heatsink?
3. What is the difference between passive and active cooling?
4. Why are thermal pads used?
5. What is thermal throttling?
6. Why should hardware installation be completed before connecting power?

---

## Part D: Serial Communication

### Activity 5: Connect to the RUBIK Pi Using UART

UART stands for **Universal Asynchronous Receiver/Transmitter**.

UART allows two devices to communicate by transmitting data serially.

The RUBIK Pi provides a serial debugging connection through its Micro-USB DEBUG port.

### Step 1: Connect the Hardware

After the instructor approves the cooling installation:

1. Connect the Micro-USB data cable to the RUBIK Pi DEBUG port.
2. Connect the other end to your laptop.
3. Connect the USB-C power supply last.
4. Power on the board if required.

### Step 2A: Windows

**Download PuTTY:**

https://www.putty.org/

Open **Device Manager**:

1. Right-click Start and select Device Manager.
2. Expand **Ports (COM & LPT)**.
3. Find the USB serial device.

Example:

```text
USB Serial Device (COM3)
```

Record the assigned COM port number.

If the serial device does not appear, check the USB cable and ask the instructor for assistance before installing drivers.

Open PuTTY and configure:

| Setting | Value |
|---|---|
| Connection type | Serial |
| Serial line | COM3 (example) |
| Speed | 115200 |
| Data bits | 8 |
| Stop bits | 1 |
| Parity | None |
| Flow control | None |

Click **Open**.

### Step 2B: macOS

Open Terminal.

List available serial devices:

```bash
ls /dev/cu.*
```

Find the USB serial device, for example:

```text
/dev/cu.usbserial-XXXX
```

Connect using:

```bash
screen /dev/cu.usbserial-XXXX 115200
```

Replace the example device name with the actual device name.

To exit the serial session, press `Ctrl+A`, followed by `Ctrl+\`, and confirm if prompted.

### Step 3: Log In

If the board has a functioning Linux installation, you should see a login prompt.

```text
login:
```

Enter the credentials provided by your instructor.

The credentials depend on the operating-system image installed on the board.

### Questions

1. What does UART stand for?
2. What is the purpose of the Micro-USB DEBUG port?
3. What does 115200 baud represent?
4. Does UART communication require an IP address?
5. How is UART different from SSH?

---

## Part E: Linux System Exploration

**Prerequisite:** This activity requires a working Linux installation on the RUBIK Pi.

### Activity 6: Explore the Processor

Execute:

```bash
uname -a
uname -m
```

The architecture should normally be reported as:

```text
aarch64
```

Next:

```bash
lscpu
nproc
```

Questions:

1. What architecture is reported?
2. How many processing units are available to the current process?

### Activity 7: Explore Memory

Execute:

```bash
free -h
```

Record:

- Total RAM:
- Used RAM:
- Available RAM:

**Question:** Why does a computer require RAM?

### Activity 8: Explore Storage

Execute:

```bash
df -h
```

**Question:** What is the difference between RAM and permanent storage?

### Activity 9: Explore Processes

Execute:

```bash
top
```

Observe CPU and memory activity.

Press `q` to exit.

**Question:** What is a process, and why can multiple processes run simultaneously?

### Activity 10: Explore Network Interfaces

Execute:

```bash
ip addr
```

**Question:** What is the difference between Ethernet and UART communication?

---

## Part F: Reflection and Wrap-Up

### Activity 11: Embedded Systems Challenge

Imagine you are designing a temperature-monitoring system using the RUBIK Pi 3.

Your system needs to:

- Read temperature measurements from a sensor.
- Display temperature readings.
- Send measurements to another computer.
- Run continuously for several hours.

Answer the following:

1. Which interface could connect a temperature sensor?
2. Which interface could connect a small OLED display?
3. How could the RUBIK Pi transmit temperature readings over a network?
4. Why is processor cooling important for continuous operation?
5. Why might a single-board computer be preferable to a desktop PC for this application?

### Final Reflection

Write three things you learned today:

1. One thing about the RUBIK Pi hardware.
2. One thing about ARM architecture or Linux.
3. One thing about serial communication or cooling.

---

## Safe Shutdown

If Linux is running, execute:

```bash
sudo shutdown -h now
```

If you are logged in as root and `sudo` is unavailable:

```bash
shutdown -h now
```

Wait for the operating system to finish shutting down.

**Disconnect the USB-C power supply first**, followed by the Micro-USB cable and any other connections.

Do not remove the heatsink or fan while the board is powered.

---

## References

- [RUBIK Pi Official Website](https://www.rubikpi.ai/)
- [RUBIK Pi 3 Documentation](https://www.thundercomm.com/rubik-pi-3/en/docs/)
- [PuTTY](https://www.putty.org/)
- [Linux Manual Pages](https://man7.org/linux/man-pages/)

**End of Lab**
