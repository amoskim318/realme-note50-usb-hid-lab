# Troubleshooting — Realme Note 50 USB HID Lab

**Device:** Realme Note 50 (RMX3834)  
**Android:** 15  
**Platform:** UMS9230  
**Project:** realme-note50-usb-hid-lab  
**Author:** Amos Kimunya

## 1. Purpose

This guide provides a disciplined process for investigating problems with USB HID, the `nh-usb-hid` Magisk module, Kali NetHunter, and DuckHunter automation on the Realme Note 50.

It is not a list of guaranteed fixes. Diagnose the failing layer first, preserve the evidence, and change one thing at a time.

## 2. Troubleshooting Rules

1. Stop repeating a command that has already failed.
2. Copy the complete error output before changing anything.
3. Record what was expected and what actually happened.
4. Check the current device state before attempting repair.
5. Change one variable at a time.
6. Re-test the original failure after each change.
7. Do not delete system files or reset USB configuration based on a guess.
8. Keep normal USB connectivity and a recovery route in mind.

## 3. Identify the Failing Layer

USB HID depends on multiple layers. Narrow the problem down before attempting a fix.

| Layer | Example symptom | What to investigate |
|---|---|---|
| Physical connection | Host does not detect phone | Cable, port, connection, USB role |
| USB controller | No gadget can bind | Controller availability and kernel state |
| Gadget framework | Gadget cannot be configured | Supported gadget mechanism and kernel support |
| HID function | Host does not see keyboard or mouse | Function setup, descriptors, interface state |
| Report interface | No input reaches host | Report format, endpoint, permissions |
| Magisk module | Activation or startup fails | Module scripts, permissions, logs |
| DuckHunter | Wrong keys or no action | Script syntax, timing, focus, host state |
| Target operating system | Input appears in wrong window | Window focus, prompts, host behavior |

## 4. Basic Checks

Before changing configuration, establish:

- Does the phone still connect normally over USB?
- Is the Magisk module installed and enabled?
- Did the problem begin after a specific change?
- Does the problem occur before or after HID activation?
- Does the host detect any USB device?
- Is the problem limited to keyboard, mouse, or both?
- Does deactivation return the phone to normal USB behavior?

Record the answers in the test log.

## 5. Common Symptoms

### 5.1 Host does not detect the phone

Possible areas to investigate:

- Physical cable and USB port
- USB connection mode
- Device role and connection state
- USB controller state
- Gadget binding state

Do not assume the HID function is the cause until basic USB connectivity has been checked.

### 5.2 HID keyboard is not detected

Investigate:

- Whether the HID function is configured
- Whether the gadget is active and bound
- Whether the host sees a HID interface
- Whether the report descriptor is valid
- Whether the report interface is available
- Whether report data matches the descriptor

Do not send arbitrary bytes to an unknown interface.

### 5.3 Keyboard is detected but no keys appear

Investigate:

- Whether the report writer is targeting the correct interface
- Whether the report length matches the descriptor
- Whether key codes and modifier bits are correct
- Whether the process has permission to write
- Whether the host window has focus
- Whether a key-release report is sent where required

Use a harmless single-key test before running a longer automation script.

### 5.4 Mouse is detected but does not move

Investigate:

- Mouse HID descriptor and report format
- Button and movement field definitions
- Report length
- Correct report interface
- Permissions and write errors
- Whether the host recognizes the interface as a mouse

Test a small, controlled movement before testing buttons or scrolling.

### 5.5 Magisk module activation fails

Investigate:

- Module installation status
- Module script syntax
- File permissions
- Required paths and interfaces
- USB gadget state before activation
- Conflicts with other USB configuration services
- Relevant module and system logs

Preserve the complete error output. Do not edit multiple scripts at once.

### 5.6 USB behavior changes after deactivation

This requires careful investigation.

Compare the current state with the state recorded before HID activation. Determine which settings or functions changed and whether the module restored them.

Do not blindly force a USB mode or overwrite configuration files. Follow only a recovery procedure verified for this device.

### 5.7 DuckHunter sends input to the wrong window

Possible causes include:

- Insufficient delay after opening an application
- A different window has focus
- A dialog or notification appeared
- The target operating system handled a shortcut differently
- The automation continued before the previous action completed

Test the sequence one action at a time and use appropriate delays. Avoid sending commands to a window whose focus has not been confirmed.

### 5.8 Windows elevation prompt appears

Windows may display User Account Control when an elevated Command Prompt is requested.

A person at the Windows computer must review and approve the prompt. A script should not be described as bypassing this approval.

If the prompt is not approved, the elevated command sequence will not proceed as expected.

## 6. Evidence Collection

For each failure, preserve:

- Date and time
- Device model and Android build
- Kernel version
- Magisk version
- NetHunter version, if applicable
- Module version
- Exact command or script
- Complete output and error message
- USB state before and after
- Host operating system
- Expected result
- Actual result
- Changes made immediately before the failure

Remove passwords, tokens, serial numbers, personal data, and other sensitive information before publishing logs.

## 7. Incident Record Template

Copy this template into a new issue or test record:

```text
Title:
Date and time:

Device:
Android build:
Kernel:
Magisk:
NetHunter:
Module version:

Host operating system:

Expected behavior:

Actual behavior:

Exact command or script:

Complete error output:

USB state before:

USB state after:

Last known working state:

Changes made before failure:

Troubleshooting steps attempted:

Current status:
```

## 8. When to Stop

Stop and preserve the current state if:

- The phone loses normal USB connectivity.
- The device becomes unstable.
- A command would overwrite unknown system configuration.
- The required interface or path cannot be identified.
- A proposed fix depends on an unverified assumption.
- The recovery procedure is unclear.

Use `docs/recovery.md` only after its steps have been confirmed for the device.

## 9. Known Project Evidence

The project README records these confirmed demonstrations:

- DuckHunter opened a Kali terminal using `CTRL ALT t`.
- DuckHunter opened the Windows Run dialog and requested an elevated Command Prompt.
- The Windows User Account Control prompt was approved manually.
- The command `start "" firefox & exit` was tested directly in an elevated Command Prompt.

These results do not prove that every HID configuration, module version, or automation script works.

---

**Status:** Troubleshooting guide drafted. Add device-specific fixes only after reproducing the issue, testing the fix, and recording the result.
