## Creating projects

<div>
    <img src="assets/screenshots/home.png" alt="" />
</div>

<div>
    <img src="assets/screenshots/project_creation.png" alt="" />
</div>


## Deploying platforms
...

## Onboarding devices
Onboarding devices is a straightforward process of two steps:
1. Register a device, by generating and downloading the credential file on the platform
2. Configure a device, by placing the credential file on the appropriate partition and path on the device's operating system image.

This allows any compatible linux device to be onboarded. Currently, the Seashell OS is available for the complete Raspberry Pi, Beaglebone and BeagleCore device families.

> [!NOTE]
> Additional hardware platforms are to follow, driven by customer demand. To integrate a custom board or adapt a custom operating system for use with Seashell cloud platform, instructions can be found [here](https://www.google.com).


#### Registering a device
Access a project through the web dashboard ...

<div>
    <img src="assets/screenshots/filler.png" alt="" />
</div>

This will generate a `<device-id>.json` JSON file, e.g. `device-fdhocf2bzici.json`  with the following content:
```json
{
  "name": "device-fdhocf2bzici",
  "drago": {
    "server": "http://35.127.87.54:8080",
    "token": <secret-token>
  }
}
```

#### Configuring a device
Download the appropriate Seashell OS image. Seashell OS images can be donwloaded from the web dashboard under `Platforms` in the `Explore` tab on the left menu.

<div>
    <img src="assets/screenshots/os_platforms.png" alt="" />
</div>


Flash the image to an SD card.

```sh
bzmap ...
```

Place the downloaded credentials file in the image's root partition under `/etc/seashell.json`.

Boot the device.

> [!TIP]
> Seashell OS comes with an utility for configuring your device's wifi. Upon boot, if no internet connection is detected, an unprotected network with SSID set to the device's id is brought up, e.g `device-fdhocf2bzici`. Once connected to this network on a mobile phone or computer, the user is redirected to a captive portal where the desired internet connection can be selected and its password set. 


## Interacting with a deployment
...