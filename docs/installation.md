# Installation Guide — Realme Note 50 USB HID Lab

**Device:** Realme Note 50 (RMX3834)  
**Android:** 15  
**Platform:** UMS9230  
**Project:** realme-note50-usb-hid-lab  
**Author:** Amos Kimunya

## 1. Purpose

This guide is a place to document installation of the project's USB HID components on the Realme Note 50.

**Important:** This is a documentation template, not a ready-to-run installation procedure. The exact release package, prerequisites, installation commands, and supported versions must be verified before use. Do not install an archive or run commands simply because its name resembles this project.

## 2. Scope

The project includes work involving:

- Kali NetHunter on Android
- Magisk root management
- The `nh-usb-hid` Magisk module
- USB HID keyboard and mouse functionality
- DuckHunter automation scripts

These components have different installation and configuration requirements. Installing a DuckHunter script does not install a kernel HID function or a Magisk module.

## 3. Prerequisites to Verify

Before installing any project component, confirm the following:

| Requirement | What to verify |
|---|---|
| Device | Realme Note 50, model RMX3834 |
| Android | Android version and build currently installed |
| Root | Magisk is installed and functioning |
| Bootloader | Device bootloader state |
| NetHunter | Installed environment and version, if used |
| Kernel | Running kernel version and required USB gadget support |
| USB | Cable and host connection work normally |
| Backup | Important data and a recovery plan are available |
| Package | Archive source, integrity, and version are known |

Do not assume that another Realme model or Android build is compatible.

## 4. Back Up Before Changes

Before changing USB gadget settings or installing a root module:

1. Back up important personal data.
2. Keep a copy of the current module package and configuration files.
3. Record the current USB mode and normal USB behavior.
4. Make sure the device can be restarted and accessed if HID activation fails.
5. Keep a known-good recovery method available.

Do not delete or overwrite existing USB configuration files without understanding their purpose.

## 5. Magisk Module Installation

The project module is identified as:

- Display name: `NetHunter USB HID`
- Module ID: `nh-usb-hid`

The exact installation package and release procedure must be linked here once a verified release is published.

### Installation checklist

- [ ] Confirm the ZIP came from the project's intended release.
- [ ] Verify the archive integrity and checksum, when published.
- [ ] Inspect the archive contents.
- [ ] Review the module's installation and startup scripts.
- [ ] Confirm compatibility with the current device and Magisk version.
- [ ] Install only after reviewing the documented risks.
- [ ] Reboot only when the tested installation procedure requires it.
- [ ] Confirm the module status and inspect logs for errors.
- [ ] Verify normal USB operation before enabling HID mode.

**No installation command is provided here yet.** It should be added only after the actual release package and its tested installation steps are available.

## 6. DuckHunter Script Setup

DuckHunter automation scripts are separate from the Magisk module.

Before using a script:

1. Obtain the script from this repository.
2. Read every command in it.
3. Confirm the target computer is yours or you have explicit permission to test it.
4. Confirm the HID keyboard works with a harmless test.
5. Run the demonstration manually or through the documented DuckHunter workflow.
6. Record the result and any differences between operating systems.

Windows may display a User Account Control prompt for elevation. A person at the Windows computer must approve it.

## 7. First-Installation Verification

After installing a component, verify it independently before proceeding to the next one.

| Check | Expected evidence |
|---|---|
| Magisk module | Module appears enabled without installation errors |
| Android stability | Device boots and operates normally |
| USB connection | Normal USB connection still works |
| HID activation | Actual gadget status confirms the intended HID interface |
| Keyboard | A harmless test key is received by the host |
| Mouse | A controlled movement or button test is received by the host |
| Deactivation | HID stops sending input |
| USB restoration | Normal USB behavior returns |

Record the date, software versions, commands used, and observed output for each test.

## 8. Troubleshooting

If installation or activation fails:

- Stop repeating the failed command.
- Save the exact error output and relevant logs.
- Check whether the module is enabled and whether its scripts ran.
- Compare the current USB state with the state recorded before installation.
- Use the project's recovery guide only after its instructions have been verified for the device.
- Do not remove unrelated system files or change multiple settings at once.

See `docs/troubleshooting.md` and `docs/recovery.md` when those documents are available.

## 9. Uninstall and Recovery

A verified uninstall procedure must explain:

- How to disable the module safely
- Whether a reboot is required
- Which configuration is removed
- Which previous USB settings are restored
- How to recover if the device loses normal USB connectivity

These steps are not specified here until the module's actual uninstall and restoration behavior has been tested.

## 10. Installation Record

Use this section to record each real installation:

| Field | Record |
|---|---|
| Date | To be completed |
| Device model | RMX3834 |
| Android build | To be recorded |
| Kernel version | To be recorded |
| Magisk version | To be recorded |
| NetHunter version | To be recorded, if applicable |
| Module version | To be recorded |
| Package checksum | To be recorded |
| Installation result | To be recorded |
| Notes and logs | Link to evidence |

---

**Status:** Installation guide drafted. Exact installation commands and recovery steps are intentionally pending verification against the actual module package and device.
