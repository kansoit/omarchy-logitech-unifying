# Logitech Unifying

An [Omarchy](https://omarchy.org) shell plugin that shows the devices paired to Logitech Unifying and Bolt receivers right in the bar, and lets you pair or unpair Unifying devices without needing Solaar or any other companion app.

Click the icon to see connected devices, their kind, and battery level. Put the receiver into pairing mode and unpair devices you no longer use — all from the panel.

![Logitech Unifying panel](preview.png)

## Install

```
omarchy plugin add https://github.com/axelfontaine/omarchy-logitech-unifying.git --enable
```

## Uninstall

```
omarchy plugin remove axelfontaine.logitech-unifying
```

## Permissions

Talking to the receiver requires read/write access to its `hidraw` device node, which isn't granted by default. If the panel shows a permission error, click the **Fix permissions** button inside it — it installs a udev rule (via a one-time authentication prompt) that grants your user access, no reboot required.

## Dependencies

The HID++ helper is self-contained, but the plugin relies on the system's
`udevadm`, `pkexec`, Python 3, and access to the receiver's `hidraw` device.
Pairing controls are currently available for Unifying receivers; Bolt devices
are listed and can be unpaired, but Bolt discovery/pairing is not exposed by
the panel yet.

If more than one supported receiver is connected, use the receiver selector in
the panel header to inspect each one.

The **Fix permissions** action rewrites a dedicated udev rule and re-enumerates
hidraw devices. This can briefly interrupt input from Logitech receivers, so
run it only when the permission error is present.

## Credit where credit is due

This would not have been possible without the hard work, reverse-engineering and dedication of the people behind [Solaar](https://github.com/pwr-Solaar/Solaar) who did the original heavy lifting to bring Logitech device support to Linux.

## License

MIT
