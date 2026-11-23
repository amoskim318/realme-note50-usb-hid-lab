# USB HID Architecture — Realme Note 50

**Device:** Realme Note 50 (RMX3834)  
**Android:** 15  
**Platform:** UMS9230  
**Project:** realme-note50-usb-hid-lab  
**Author:** Amos Kimunya

## 1. Purpose

This document describes the conceptual software and hardware layers involved in USB Human Interface Device (HID) operation on the Realme Note 50.

It is an architecture overview, not a claim that every implementation detail has already been verified on this device. Device-specific paths, kernel configuration, gadget functions, descriptors, and initialization behavior should be added only after they have been inspected and tested.

## 2. High-Level Architecture

A USB HID keyboard or mouse setup involves several cooperating layers:

```text
External computer
       |
       | USB cable
       v
USB device controller (phone hardware)
       |
       v
Linux USB gadget framework
       |
       v
HID gadget function / USB configuration
       |
       v
HID report data
       ^
       |
HID control script or service
       ^
       |
Magisk module / privileged Android environment
       ^
       |
User action or authorized automation
```

The exact kernel interfaces and configuration mechanism used by this device must be confirmed from its running system and module scripts.

## 3. Hardware Layer

The phone's USB hardware provides the physical connection to the host computer.

Relevant elements include:

- USB port and cable
- USB device controller (UDC)
- USB power and connection state
- USB role and mode negotiation

The device controller is the hardware endpoint used by the operating system's USB device stack. A cable alone does not provide HID functionality; the operating system and kernel must configure the device to expose the required USB interfaces.

## 4. Kernel and USB Gadget Layer

Linux supports USB device functionality through its USB gadget subsystem when the device kernel and platform implementation provide it.

The gadget layer is responsible for presenting USB functions to a connected host. A HID function can expose an interface that a host recognizes as a keyboard or mouse.

Implementation details that should be recorded for this device include:

- Whether the kernel has the required gadget support
- Which USB Device Controller is used
- Which configfs or legacy gadget mechanism is available
- The active gadget name and configuration
- HID function instances and report descriptor details
- The method used to bind and unbind the gadget to the UDC

Do not assume that paths or commands from another Android device apply to the RMX3834.

## 5. HID Function Layer

USB HID describes how input devices communicate with a host.

A HID interface generally uses:

- A USB interface descriptor
- A HID descriptor
- One or more endpoint descriptors
- A report descriptor defining the format of input reports

A keyboard report can describe modifier keys and key states. A mouse report can describe buttons and pointer movement.

The report descriptor and report format must agree. Incorrect report data can cause unexpected input or make the interface unusable.

This repository should eventually include the exact descriptors and report format used by the tested implementation, together with their source and verification method.

## 6. Android and Privileged Control Layer

Android runs on a Linux kernel, but access to low-level USB gadget controls is commonly restricted.

This project uses a rooted NetHunter environment and a Magisk module to manage privileged operations.

The module under development is identified as:

- Display name: `NetHunter USB HID`
- Module ID: `nh-usb-hid`

The module's responsibilities and exact implementation should be documented from its actual source code. Areas to inspect include:

- Installation and module metadata
- Startup scripts and service scripts
- USB gadget setup and teardown
- Required permissions and ownership
- System properties or init interactions
- Status checks and error handling
- Restoration of the previous USB configuration

A module should not be described as safely restoring every previous USB mode until that behavior has been tested.

## 7. HID Control and Automation Layer

A control script or service can write HID report data to the interface exposed by the gadget function.

DuckHunter scripts provide a way to automate keyboard input for authorized demonstrations. The script sends key combinations and text; the phone's HID implementation translates the input into USB HID reports.

Confirmed demonstrations documented in the project README include:

- Opening a terminal in Kali Linux with `CTRL ALT t`
- Opening the Windows Run dialog and requesting an elevated Command Prompt
- Launching Firefox and exiting the original Command Prompt using a tested Windows shell command

The Windows User Account Control prompt requires the person at the target computer to approve the request. These examples should be used only on systems where testing is authorized.

## 8. Activation and Deactivation Flow

The intended lifecycle is:

```text
User requests HID mode
        |
        v
Check device and USB state
        |
        v
Prepare HID gadget configuration
        |
        v
Expose HID interface to USB host
        |
        v
Send authorized keyboard or mouse reports
        |
        v
Stop sending reports
        |
        v
Disable HID configuration
        |
        v
Restore the appropriate USB state
```

This is a conceptual flow. The exact commands, safeguards, and restoration behavior must be taken from the tested module implementation.

## 9. Reliability and Safety Requirements

The implementation should be tested for the following:

1. Do not activate HID if required gadget interfaces are unavailable.
2. Check whether the USB controller is already bound before changing its state.
3. Avoid overwriting unrelated USB functions or configurations.
4. Keep activation and deactivation operations reversible.
5. Handle interrupted activation and unexpected disconnects.
6. Record errors instead of silently continuing.
7. Provide a recovery procedure if the USB connection stops working.
8. Verify that normal USB behavior returns after HID is disabled.

## 10. Device-Specific Evidence To Add

The following information remains to be captured from the actual RMX3834 implementation:

| Item | Evidence to record |
|---|---|
| Kernel version | Exact running kernel release |
| USB controller | UDC name from the running device |
| Gadget mechanism | configfs or other mechanism confirmed on device |
| HID function | Actual function instance and configuration |
| Report descriptor | Exact descriptor used |
| HID report endpoint | Actual interface path and permissions |
| Module lifecycle | Actual install, activation, and deactivation scripts |
| USB restoration | Before-and-after state and test result |
| Keyboard test | Exact test procedure and observed result |
| Mouse test | Exact test procedure and observed result |

Do not fill these fields with guessed values. Capture them from the device and preserve the command output as project evidence.

## 11. Related Documentation

- `README.md` — project overview and confirmed demonstrations
- `docs/installation.md` — planned installation guide
- `docs/configuration.md` — planned device configuration reference
- `docs/troubleshooting.md` — planned troubleshooting guide
- `docs/recovery.md` — planned recovery procedure
- `tests/keyboard.md` — planned keyboard test record
- `tests/mouse.md` — planned mouse test record

---

**Status:** Architecture overview drafted. Device-specific implementation details require verification against the Realme Note 50 and the actual `nh-usb-hid` module source.
