# USB HID Configuration — Realme Note 50

**Device:** Realme Note 50 (RMX3834)  
**Android:** 15  
**Platform:** UMS9230  
**Project:** realme-note50-usb-hid-lab  
**Author:** Amos Kimunya

## 1. Purpose

This document records how USB HID is configured and managed on the Realme Note 50.

The purpose is to create a reproducible device-specific configuration reference. It distinguishes the general Linux USB gadget concepts from the exact implementation used by this phone.

**Important:** Do not copy configuration commands or filesystem paths from another device without checking that they exist and behave as expected on the RMX3834.

## 2. Configuration Layers

USB HID operation involves several layers:

1. **USB hardware:** The phone's USB device controller and physical connection.
2. **Kernel:** USB gadget support and the available gadget functions.
3. **Gadget configuration:** USB device identity, configurations, interfaces, and endpoints.
4. **HID function:** HID descriptors and report format for keyboard or mouse input.
5. **Privileged control:** The scripts or services that configure the gadget.
6. **Automation:** DuckHunter scripts that request keyboard input for an authorized test.

A problem at one layer can prevent the entire HID setup from working.

## 3. Configuration Inventory

Complete this table using output collected from the actual device.

| Item | Device-specific value |
|---|---|
| Android build | To be recorded |
| Kernel release | To be recorded |
| USB Device Controller (UDC) | To be recorded |
| Gadget configuration method | To be verified |
| Gadget name | To be recorded |
| HID function instance | To be recorded |
| Keyboard report descriptor | To be archived |
| Mouse report descriptor | To be archived |
| HID report interface path | To be recorded |
| Activation script | `nh-usb-hid` module source |
| Deactivation script | To be verified |
| USB restoration method | To be verified |

Do not fill unknown values with examples from other Android devices.

## 4. USB Device Identity

A USB device may expose identity information such as:

- Vendor ID (VID)
- Product ID (PID)
- Device release number
- Manufacturer string
- Product string
- Serial number

These values help the host identify the connected USB device.

Record the values used by the tested configuration. Do not change identity values without understanding the effect on host recognition and compatibility.

## 5. USB Gadget Configuration

The Linux USB gadget subsystem provides the device-side framework for presenting USB functions to a host.

Depending on kernel and platform support, gadget configuration may use configfs or another implementation.

The following details must be established from the running RMX3834:

- Available gadget configuration interface
- Available USB functions
- Active configuration and function links
- UDC binding state
- Existing Android USB functions that must be preserved
- Platform services or properties that may modify USB state

The presence of a directory or interface on another Android device does not prove it exists on this device.

## 6. HID Function Configuration

A HID function must expose descriptors that correctly describe the input device.

### Keyboard

Record:

- HID interface details
- Report descriptor
- Report length
- Modifier-key representation
- Key-code representation
- Report write interface
- Permissions and ownership

### Mouse

Record:

- HID interface details
- Report descriptor
- Report length
- Button representation
- Pointer movement representation
- Scroll representation, if supported
- Report write interface
- Permissions and ownership

Keyboard and mouse reports must match their descriptors. Incorrect report lengths or formats can cause malformed or unexpected input.

## 7. Magisk Module Configuration

The module under development is:

- Display name: `NetHunter USB HID`
- Module ID: `nh-usb-hid`

Document the actual module implementation here as it is verified.

| Area | What to document |
|---|---|
| Module metadata | Actual module properties and version |
| Installation | Files installed and permissions set |
| Boot behavior | Scripts executed during startup |
| Activation | Exact configuration changes |
| Status | How active and inactive states are detected |
| Deactivation | Exact changes made to stop HID |
| Restoration | How previous USB state is recovered |
| Logging | Log locations and error reporting |
| Compatibility | Magisk, Android, and kernel requirements |

Do not assume that a module's display name or version proves its internal behavior.

## 8. Configuration Lifecycle

The intended lifecycle should be documented and tested in this order:

1. Read and record the current USB state.
2. Check that the required gadget interfaces are available.
3. Check for conflicting or already active configurations.
4. Prepare the intended HID configuration.
5. Bind or activate the HID gadget using the verified device-specific method.
6. Confirm the host recognizes the expected HID interface.
7. Send only deliberate, authorized test reports.
8. Stop input transmission.
9. Deactivate the HID configuration.
10. Restore and verify the appropriate normal USB state.

The actual module commands and state transitions must be added from the tested source code.

## 9. Safety and Compatibility

- Preserve the device's original USB configuration before making changes.
- Avoid changing multiple USB properties at once.
- Do not overwrite unrelated gadget functions.
- Do not assume a fixed UDC name.
- Do not leave a HID interface active unintentionally.
- Check the result of each operation.
- Handle disconnects and interrupted activation.
- Verify restoration after every test.
- Keep a recovery route available.

## 10. Configuration Change Log

Record every meaningful change.

| Date | File or setting | Change | Reason | Test result |
|---|---|---|---|---|
| To be recorded | To be recorded | To be recorded | To be recorded | To be recorded |

Include relevant command output or log references in the repository. Remove personal information and secrets before publishing logs.

## 11. Verification Checklist

- [ ] Current USB state recorded before activation
- [ ] Gadget mechanism confirmed on RMX3834
- [ ] UDC name confirmed
- [ ] HID function confirmed
- [ ] Keyboard descriptor and report format archived
- [ ] Mouse descriptor and report format archived
- [ ] Permissions verified
- [ ] Keyboard test completed and recorded
- [ ] Mouse test completed and recorded
- [ ] Deactivation tested
- [ ] Normal USB behavior restored
- [ ] Failure recovery tested

---

**Status:** Configuration reference drafted. Exact paths, descriptors, commands, and module behavior remain device-specific and must be populated from verified RMX3834 test evidence.
