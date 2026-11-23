# USB HID Recovery Procedures

**Project:** Realme Note 50 USB HID Lab  
**Device:** Realme Note 50 (RMX3834)  
**Author:** Amos Kimunya  
**Status:** Recovery guidance — verify device-specific steps before use

---

## 1. Purpose

This document describes a cautious recovery approach for situations where USB HID activation, a Magisk module, or a USB gadget configuration leaves the device's USB connection behaving unexpectedly.

The exact recovery method depends on the device firmware, kernel, Android build, Magisk version, and the changes made. Do not assume that paths or commands from another Android device apply to this device.

## 2. Before Making Changes

1. Stop any running HID automation.
2. Disconnect the USB cable from the host computer if it is safe to do so.
3. Keep the phone powered and avoid rebooting repeatedly.
4. Record the current symptoms and any error messages.
5. If the device is still accessible, preserve relevant logs and copies of configuration files before changing them.
6. Do not delete or overwrite files unless their purpose and backup are understood.

## 3. Restore Normal USB Behavior

Use the least disruptive recovery method available:

1. If the HID manager provides a documented **deactivate** or **restore** operation, use that operation first.
2. Disconnect and reconnect the USB cable after deactivation.
3. On Android, select the intended USB mode from the system USB notification or settings, if available.
4. Test ordinary charging and file transfer before attempting HID again.

Do not manually remove USB gadget configuration entries unless the exact configuration and restoration procedure have been verified for this device.

## 4. If the Magisk Module Causes Problems

If the device remains bootable and Magisk is accessible:

1. Open the Magisk app.
2. Locate the USB HID module.
3. Disable the module.
4. Reboot only when prompted or when required by the module's documented procedure.
5. After restarting, verify ordinary USB behavior before re-enabling the module.

If Android cannot boot normally, use only a recovery procedure known to be compatible with the installed Magisk version and device. Do not flash unrelated boot images or remove unknown files from `/data/adb`.

## 5. If USB HID Stops Responding

Check the following without making destructive changes:

- Is the USB cable capable of data transfer?
- Is the host computer detecting any USB device?
- Is the phone in the expected USB mode?
- Is the HID gadget configured and active?
- Are the expected HID interfaces present?
- Did a recent module, property, init, or gadget-configuration change cause the failure?
- Does ordinary USB file transfer still work?

Record the results separately for keyboard and mouse testing.

## 6. If the Host Computer Behaves Unexpectedly

1. Stop the automation script.
2. Disconnect the phone if continued input could interfere with the host.
3. Restore control using the host's normal keyboard and mouse.
4. Close any unintended applications or terminals manually.
5. Review the exact script and command sequence before testing again.

Run HID automation only on systems you own or are explicitly authorized to test.

## 7. Evidence to Collect

For each recovery attempt, document:

| Field | Record |
|---|---|
| Date and time | |
| Android build | |
| Magisk version | |
| Module version | |
| USB mode before test | |
| Action immediately before failure | |
| Host operating system | |
| Keyboard result | |
| Mouse result | |
| USB file-transfer result | |
| Recovery action | |
| Final result | |

Include relevant logs and command output, but remove passwords, tokens, serial numbers, and other sensitive information before publishing.

## 8. Recovery Validation Checklist

- [ ] HID automation is stopped.
- [ ] The module's documented deactivation procedure was followed, if available.
- [ ] The phone boots normally.
- [ ] Charging works.
- [ ] Normal USB data transfer works.
- [ ] Keyboard and mouse behavior has been tested independently.
- [ ] No unverified system files were deleted or overwritten.
- [ ] Recovery steps and results have been documented.

## 9. Important Limitations

This document is a conservative recovery checklist, not a device-specific unbrick guide. It intentionally does not provide commands to rewrite USB gadget state, modify boot images, or delete Magisk module files because those operations must be based on the exact tested implementation and recovery environment.

Before publishing a device-specific command, test it on the target Realme Note 50 build, record the result, and include a known-good rollback procedure.

---

**Project note:** Update this document as recovery procedures are verified on the Realme Note 50 (RMX3834). Clearly label untested procedures as experimental.
