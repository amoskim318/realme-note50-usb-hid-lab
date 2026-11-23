# Realme Note 50 USB HID Lab

**Realme Note 50 (RMX3834) | Android 15 | UMS9230**

A hands-on cybersecurity and Android research project focused on USB Human Interface Device (HID) functionality, Kali NetHunter, Magisk-based USB configuration, and DuckHunter automation.

**Author:** Amos Kimunya  
**Repository:** https://github.com/amoskim318/realme-note50-usb-hid-lab  
**Project status:** Development and testing

---

## 1. Project Overview

This repository documents research, development, configuration, and testing of USB HID functionality on the Realme Note 50.

The project explores how an Android device can expose USB HID interfaces and how those interfaces can be used for authorized keyboard and mouse emulation.

It also documents the practical work involved in configuring the device, troubleshooting compatibility issues, and testing HID automation using DuckHunter.

The goal is to maintain a clear technical record of what was built, why changes were made, what worked, and what still needs investigation.

## 2. Device and Environment

| Component | Details |
|---|---|
| Device | Realme Note 50 |
| Model | RMX3834 |
| Android version | Android 15 |
| Platform | UMS9230 |
| Operating environment | Kali NetHunter |
| Root management | Magisk |
| USB functionality | USB HID |
| Automation | DuckHunter |

## 3. Project Components

### USB HID

Research and configuration of USB Human Interface Device functionality, including:

- USB HID keyboard emulation
- USB HID mouse emulation
- USB gadget configuration
- HID activation and deactivation
- USB mode management
- Troubleshooting device compatibility

### Magisk USB HID Module

The project includes work on a Magisk module named:

`NetHunter USB HID`

Module identifier:

`nh-usb-hid`

The module is intended to manage USB HID configuration and activation on the device.

Development documentation will cover:

- Module structure
- Installation and removal
- Activation and deactivation
- USB configuration
- System initialization and property interactions
- Recovery and restoration procedures
- Compatibility testing

### DuckHunter Automation

DuckHunter is used to test HID keyboard automation.

**Kali Linux — opening a terminal**

```text
REM Open Kali terminal
DELAY 1000
CTRL ALT t
DELAY 1500
```

**Windows — opening an elevated Command Prompt**

```text
REM Open Windows Run
DELAY 1000
GUI r
DELAY 800
STRING cmd
CTRL SHIFT ENTER
DELAY 5000
```

Windows displays a User Account Control prompt. Authorization must be provided manually.

**Windows — launching Firefox and closing the original Command Prompt**

The following command was tested directly in an elevated Command Prompt:

```cmd
start "" firefox & exit
```

These demonstrations are documented as individual tests. Experimental scripts and unverified behavior will be identified separately.

## 4. Repository Structure

The planned repository structure is:

```text
realme-note50-usb-hid-lab/
│
├── README.md
│
├── module/
│   └── nh-usb-hid/
│
├── duckyscripts/
│   ├── kali/
│   └── windows/
│
├── docs/
│   ├── architecture.md
│   ├── installation.md
│   ├── configuration.md
│   ├── troubleshooting.md
│   └── recovery.md
│
├── tests/
│   ├── keyboard.md
│   ├── mouse.md
│   └── automation.md
│
└── LICENSE
```

This is the intended documentation layout. Files and directories will be added as their contents are prepared and verified.

## 5. Testing and Verification

Testing is an important part of this project.

The documentation will distinguish between:

- Confirmed working configurations
- Commands tested directly
- Scripts tested through HID
- Experimental configurations
- Failed attempts and their causes
- Known limitations
- Unresolved compatibility issues

No experimental result should be presented as a confirmed success.

## 6. Safety and Authorized Use

This project is intended for cybersecurity education, Android research, and authorized testing.

USB HID automation can send keyboard and mouse input to connected systems. Only use it on devices and systems you own or have explicit permission to test.

Always understand the commands being executed before running an automation script.

## 7. Development Philosophy

The project follows several principles:

1. Preserve working configurations.
2. Test changes before treating them as successful.
3. Document commands and their actual results.
4. Avoid unnecessary modifications to system files.
5. Provide safe activation, deactivation, and recovery procedures.
6. Record failures and compatibility problems rather than hiding them.

## 8. Project Goals

- Document USB HID functionality on the Realme Note 50.
- Develop and document a device-compatible Magisk USB HID module.
- Test keyboard and mouse emulation.
- Document DuckHunter automation for Kali Linux and Windows.
- Investigate Android USB gadget configuration.
- Maintain reproducible technical documentation.
- Share the research and learning process with the cybersecurity community.

## 9. Author

**Amos Kimunya**

Android security research | Cybersecurity | USB HID experimentation | Kali NetHunter

---

*This repository is a continuing technical research project. Documentation and implementation details will evolve as additional testing and development are completed.*
