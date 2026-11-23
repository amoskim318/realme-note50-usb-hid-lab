# USB HID Keyboard Test Record

**Project:** Realme Note 50 USB HID Lab  
**Device:** Realme Note 50 (RMX3834)  
**Platform:** UMS9230  
**Android:** 15  
**Author:** Amos Kimunya  
**Status:** Test record — update with device-specific evidence

---

## 1. Purpose

This document records testing of the USB HID keyboard interface exposed by the Realme Note 50 project.

The goal is to distinguish successful keyboard enumeration, successful key delivery, and successful application-level behavior. These are separate results and should not be treated as interchangeable.

## 2. Test Environment

| Field | Value |
|---|---|
| Phone model | Realme Note 50 |
| Model number | RMX3834 |
| Android version | Android 15 |
| Platform | UMS9230 |
| Root management | Magisk |
| HID implementation | `nh-usb-hid` |
| HID host | Record the host OS and version |
| USB cable / adapter | Record the hardware used |
| Test date | Record date and time |

## 3. Test Scope

Test the following stages independently:

1. The phone enters the intended USB gadget mode.
2. The host detects a USB HID keyboard interface.
3. The host accepts keyboard reports.
4. Individual keys and key combinations are interpreted correctly.
5. Repeated input works with appropriate delays.
6. Deactivation restores normal USB behavior.

Do not run automation against systems without authorization.

## 4. Confirmed DuckHunter Demonstration

The following DuckyScript was confirmed to open a terminal in Kali Linux:

```text
REM Open Kali terminal
DELAY 1000
CTRL ALT t
DELAY 1500
```

**Recorded result:** Kali terminal opened successfully.

This confirms that the tested HID path delivered the required key combination in that test environment. Record the Kali version, desktop environment, and date when available.

## 5. Windows Demonstration

The following DuckyScript was confirmed to open the Windows Run dialog and request an elevated Command Prompt:

```text
REM Open Windows Run
DELAY 1000
GUI r
DELAY 800
STRING cmd
CTRL SHIFT ENTER
DELAY 5000
```

**Recorded result:** The elevation prompt appeared. The user approved the User Account Control prompt manually.

Elevation is not automatic; Windows requires the user to authorize the prompt.

A command also tested directly in an elevated Command Prompt was:

```cmd
start "" firefox & exit
```

**Recorded result:** Firefox launched and the original Command Prompt closed when this command was entered directly.

This command result is separate from the HID script result. Do not claim the complete command sequence was verified through HID unless that exact sequence is tested and recorded.

## 6. Test Cases

| Test ID | Test | Expected result | Result |
|---|---|---|---|
| KBD-001 | Host detects HID keyboard | Keyboard interface appears | Not recorded |
| KBD-002 | Single key input | Correct character appears | Not recorded |
| KBD-003 | Modifier key input | Modifier is interpreted correctly | Not recorded |
| KBD-004 | `CTRL ALT t` in Kali | Terminal opens | Confirmed |
| KBD-005 | Windows `GUI r` | Run dialog opens | Confirmed as part of the Windows demonstration |
| KBD-006 | Windows elevation request | UAC prompt appears | Confirmed; user approved manually |
| KBD-007 | Repeated key input | All intended inputs are received | Not recorded |
| KBD-008 | HID deactivation | Normal USB mode can be restored | Record separately |

## 7. Test Evidence Template

For each new test, record:

- Test ID:
- Date and time:
- Host operating system and version:
- Phone Android build:
- Module version:
- USB mode:
- Exact script or key sequence:
- Expected result:
- Actual result:
- Error messages:
- Log or screenshot reference:
- Recovery required:
- Final status: PASS / FAIL / NOT TESTED

Do not publish sensitive identifiers, credentials, or private host information in screenshots or logs.

## 8. Safety and Test Discipline

- Use a controlled test host.
- Obtain authorization before sending HID input.
- Start with harmless input such as opening a text editor and typing a short test string.
- Use deliberate delays to make tests reproducible.
- Stop the script if focus moves to an unintended application.
- Test keyboard and mouse separately before combining them.
- Verify normal USB behavior after deactivation.

## 9. Current Evidence Summary

**Confirmed:**
- DuckHunter opened a Kali terminal using `CTRL ALT t`.
- The Windows Run sequence opened an elevation prompt.
- The user manually approved the Windows UAC prompt.
- `start "" firefox & exit` worked when entered directly in an elevated Command Prompt.

**Not yet established in this record:**
- Complete HID keyboard enumeration details.
- Individual key coverage and modifier coverage.
- Repeated-input reliability.
- Exact Windows multi-window automation behavior.
- Full device-specific recovery validation.

---

Update this record only with tests actually performed on the target setup. Preserve failed tests as well as successful ones.
