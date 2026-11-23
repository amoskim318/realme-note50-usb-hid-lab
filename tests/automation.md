# HID Automation Test Record

**Project:** Realme Note 50 USB HID Lab  
**Device:** Realme Note 50 (RMX3834)  
**Platform:** UMS9230  
**Android:** 15  
**Author:** Amos Kimunya  
**Status:** Test record — update only with observed results

---

## 1. Purpose

This document records authorized automation tests performed through the USB HID interfaces of the Realme Note 50.

It covers automation timing, keyboard sequences, application focus, repeatability, and safe stopping behavior. Keyboard and mouse functionality should first be tested independently using `keyboard.md` and `mouse.md`.

## 2. Test Environment

| Field | Value |
|---|---|
| Phone model | Realme Note 50 |
| Model number | RMX3834 |
| Android version | Android 15 |
| Platform | UMS9230 |
| Root management | Magisk |
| HID implementation | `nh-usb-hid` |
| Automation tool | DuckHunter |
| Host operating system | Record version |
| Desktop environment | Record if applicable |
| Test date | Record date and time |

## 3. Confirmed Automation Demonstrations

### 3.1 Kali Linux terminal launch

The following DuckHunter script was confirmed to open a Kali terminal:

```text
REM Open Kali terminal
DELAY 1000
CTRL ALT t
DELAY 1500
```

**Observed result:** A Kali terminal opened successfully.

### 3.2 Windows elevated Command Prompt request

The following script was confirmed to open Windows Run and request an elevated Command Prompt:

```text
REM Open Windows Run
DELAY 1000
GUI r
DELAY 800
STRING cmd
CTRL SHIFT ENTER
DELAY 5000
```

**Observed result:** Windows displayed a User Account Control prompt. The user approved it manually.

### 3.3 Firefox launch from an elevated Command Prompt

This command was tested directly in an elevated Command Prompt:

```cmd
start "" firefox & exit
```

**Observed result:** Firefox launched and the original Command Prompt closed.

This direct shell test is not evidence that every HID automation sequence involving the command has been tested. Record the exact delivery method for each future test.

## 4. Automation Test Cases

| Test ID | Test | Expected result | Result |
|---|---|---|---|
| AUT-001 | Open Kali terminal | Terminal opens | Confirmed |
| AUT-002 | Open Windows Run | Run dialog opens | Confirmed as part of Windows demonstration |
| AUT-003 | Request elevated Command Prompt | UAC prompt appears | Confirmed; user approved manually |
| AUT-004 | Type harmless test text | Exact text appears in intended field | Not recorded |
| AUT-005 | Launch Firefox command directly | Firefox launches; original prompt closes | Confirmed by direct command test |
| AUT-006 | Repeat a short safe sequence | Same result on each run | Not recorded |
| AUT-007 | Stop automation during execution | No further input is sent | Not recorded |
| AUT-008 | Test focus changes | Input goes only to intended window | Not recorded |
| AUT-009 | Test timing variations | Sequence remains predictable | Not recorded |
| AUT-010 | Deactivate HID afterward | Normal USB behavior returns | Record separately |

## 5. Timing and Focus

Automation depends on more than correct key names. The host must be ready to receive input, and the intended application must have focus.

When documenting a timing issue, record:

- Delay before the first key.
- Delay after opening a dialog or application.
- Delay after typing text.
- Delay before submitting a command.
- Whether a prompt or permission dialog appeared.
- Which window had focus when the next input was sent.

A command typed after an application takes focus may go to that application rather than the original terminal. Treat focus changes as a separate test condition.

## 6. Safe Test Procedure

1. Use a computer and account you are authorized to test.
2. Start with a harmless action, such as opening a text editor.
3. Type a short, recognizable test string.
4. Verify the target window before sending additional input.
5. Test one sequence at a time.
6. Keep a reliable way to stop the automation.
7. Avoid scripts that delete data, change security settings, or execute destructive actions.
8. Deactivate HID and verify ordinary USB operation after testing.

For Windows elevation tests, a person must review and approve the User Account Control prompt.

## 7. Test Evidence Template

For each automation test, record:

- Test ID:
- Date and time:
- DuckHunter version:
- Exact script:
- Delivery method:
- Phone and module versions:
- Host operating system:
- Initial active window:
- Expected result:
- Actual result:
- Timing values:
- Focus changes:
- Error messages:
- Evidence reference:
- Recovery required:
- Final status: PASS / FAIL / NOT TESTED

Redact credentials, tokens, personal data, and sensitive host details from published evidence.

## 8. Current Evidence Summary

**Confirmed:**
- DuckHunter opened a Kali terminal using `CTRL ALT t`.
- The Windows Run sequence requested an elevated Command Prompt.
- The Windows UAC prompt required and received manual user approval.
- `start "" firefox & exit` worked when entered directly in an elevated Command Prompt.

**Not established in this record:**
- Repeatability across multiple runs and host configurations.
- Exact timing tolerances.
- A verified multi-window Firefox demonstration.
- Automated focus management.
- Full stop-and-recovery behavior.

Do not describe an experimental multi-window script as successful until the exact script has been tested and its result recorded.

---

Preserve both successful and failed results. This file is a test log, not a claim that every planned automation feature is implemented.
