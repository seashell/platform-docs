## Creating projects

<div>
    <img src="assets/screenshots/filler.png" alt="" />
</div>

## Deploying platforms
...

## Onboarding devices
Onboarding devices is a straightforward process of two steps. First, a device credential file must be generated through the platform. Second, this file must be placed on the appropriate path on the device's operating system, allowing any compatible linux device to be onboarded.

#### Registering a device
Access a project through the web dashboard ...

This will generate a `<device-id>.json` JSON file, e.g. `device-fdhocf2bzici.json`, with the following content:
```
{
  "name": "<device-id>",
  "drago": {
    "server": "<drago-server-address>",
    "token": "<secret-token>"
  }
}
```

#### Configuring a device
Download and flash the appropriate Seashell OS image to an SD card.

Place the downloaded credentials file in the image's root partition under `/etc/seashell.json`.

Boot the device.

> [!NOTE]
> Currently, the Seashell OS supports the complete Raspberry Pi, Beaglebone and BeagleCore device families. Additional hardware platforms are to follow, driven by customer demand. To integrate a custom board or adapt a custom operating system on the Seashell cloud platform, instructions can be found [here](https://www.google.com).

## Interacting with a deployment
...