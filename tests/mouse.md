# USB HID Mouse Test Record

**Project:** Realme Note 50 USB HID Lab  
**Device:** Realme Note 50 (RMX3834)  
**Platform:** UMS9230  
**Android:** 15  
**Author:** Amos Kimunya  
**Status:** Test record — populate with observed results

---

## 1. Purpose

This document records testing of the USB HID mouse interface on the Realme Note 50.

Mouse testing must be documented separately from keyboard testing. A working keyboard interface does not prove that the mouse interface is configured or functioning correctly.

## 2. Test Environment

| Field | Value |
|---|---|
| Phone model | Realme Note 50 |
| Model number | RMX3834 |
| Android version | Android 15 |
| Platform | UMS9230 |
| Root management | Magisk |
| HID implementation | `nh-usb-hid` |
| Host operating system | Record version |
| Host hardware | Record computer model if relevant |
| USB cable / adapter | Record hardware used |
| Test date | Record date and time |

## 3. Test Scope

Test each mouse function independently:

1. Host detects the USB HID mouse interface.
2. Pointer movement is received.
3. Movement in each direction is correct.
4. Left button press and release work.
5. Right button press and release work.
6. Middle button works, if implemented.
7. Scroll wheel works, if implemented.
8. Repeated reports do not leave buttons stuck.
9. Deactivation restores normal USB behavior.

Only mark a function as supported if it has been tested on the target device and host.

## 4. Test Cases

| Test ID | Test | Expected result | Result |
|---|---|---|---|
| MSE-001 | Host detects HID mouse | Mouse interface appears | Not recorded |
| MSE-002 | Move pointer left | Pointer moves left | Not recorded |
| MSE-003 | Move pointer right | Pointer moves right | Not recorded |
| MSE-004 | Move pointer up | Pointer moves up | Not recorded |
| MSE-005 | Move pointer down | Pointer moves down | Not recorded |
| MSE-006 | Left button | One press and release | Not recorded |
| MSE-007 | Right button | One press and release | Not recorded |
| MSE-008 | Middle button | One press and release, if supported | Not recorded |
| MSE-009 | Scroll wheel | Scroll direction and amount are correct | Not recorded |
| MSE-010 | Repeated reports | No stuck buttons or unexpected movement | Not recorded |
| MSE-011 | HID deactivation | Normal USB mode can be restored | Record separately |

## 5. Test Procedure

For each test:

1. Confirm that the test host is authorized and ready.
2. Activate the documented HID configuration.
3. Confirm that the host detects a mouse interface.
4. Perform one test action at a time.
5. Observe the pointer or button response.
6. Record unexpected movement, missed events, or stuck buttons.
7. Deactivate HID using the documented procedure.
8. Confirm that ordinary USB behavior is restored.

Begin with small pointer movements and single button clicks. Avoid automated clicks on destructive controls or actions that could change system settings.

## 6. Test Evidence Template

Record the following for each test:

- Test ID:
- Date and time:
- Host operating system and version:
- Phone Android build:
- Module version:
- USB mode:
- Exact action or report tested:
- Expected result:
- Actual result:
- Pointer behavior:
- Button behavior:
- Error messages:
- Log or screenshot reference:
- Recovery required:
- Final status: PASS / FAIL / NOT TESTED

Remove sensitive identifiers and private information from evidence before publishing.

## 7. Troubleshooting Notes

If the host does not detect a mouse:

- Confirm that the intended USB gadget configuration is active.
- Check whether the HID mouse interface is included in the active configuration.
- Check the host's USB device list.
- Verify that the mouse report descriptor matches the reports being sent.
- Compare the result with keyboard-only operation.
- Review relevant logs before changing configuration.

If pointer movement works but buttons do not, investigate the button bit fields and report format. If buttons work but movement does not, investigate the X/Y movement fields and report format.

Do not copy descriptors or report layouts from another device without verifying compatibility with the implementation in this project.

## 8. Current Evidence Summary

No specific mouse test result is recorded in this document yet.

This is intentional: keyboard success must not be presented as proof of mouse success. Add confirmed results, failures, and supporting evidence after the corresponding tests are performed.

---

Update this file as mouse testing progresses on the Realme Note 50 (RMX3834). Preserve failed tests and unresolved issues.
