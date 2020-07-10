## Required GCP setup

> [!NOTE]
> During our private beta, platform deployments are restricted to Google's Cloud Platform. More cloud providers are to follow, as driven by customer demand.

Before getting started with Seashell, it is necessary to have a valid Google Cloud Platform (GCP) project. Below is all the information needed to properly configure this project and setup its service account for use with Seashell.

#### Enable GCP APIs
- Compute Engine API
- Cloud SQL Admin API

For further information about managing APIs, refer to the official documentation at:
https://cloud.google.com/apis/docs/getting-started

#### Create a GCP service account
...

#### Define GCP service account's roles
- Service Account User
- Cloud SQL Client

#### Generate GCP service account's credential keys
...

## Creating projects
...

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