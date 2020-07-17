## Creating a project

From the web dashboard home page, access the project's creation page by either clicking the `create` button or `+ new project` in the `projects` tab on the left menu.

<div>
    <img src="assets/screenshots/home.png" alt="" />
</div>

Fill in the project name, description and insert the credentials from the cloud provider of choice. Instructions on how to generate the credentials for Google Cloud can be found [here](pages/setup?id=generate-service-accounts-credential-keys).

<div>
    <img src="assets/screenshots/project_creation.png" alt="" />
</div>

After creation, projects are listed both in the `projects` tab on the left menu, as well as in the home page.

<div>
    <img src="assets/screenshots/project_creation_2.png" alt="" />
</div>


## Creating a deployment

Access a project or create one if there are none avaiable. Start the process by clicking on the`create a new deployment` card. This will prompt for deployment configuration options, which are disabled for the private beta. After clicking the `create` button, the process of provisioning resources on appropriate cloud provider infrastructure will be triggered. 

<div>
    <img src="assets/screenshots/create_deployment_1.png" alt="" />
</div>

The progress of a deployment can be monitored by accessing the deployment's home page, which becomes aviable at the project's home page once it has started. 

<div>
    <img src="assets/screenshots/create_deployment_3.png" alt="" />
</div>

As deployments are created at the infrastructure of the cloud provider of choice, the process is subject to delays and availability of this specific provider and can take several take several minutes to complete.

<div>
    <img src="assets/screenshots/create_deployment_4.png" alt="" />
</div>


Once the deployment is ready,, a list of the deployed instances and relevant information about becomes available, such as IP addresses or quick-access links for those with their own user interfaces. 

<div>
    <img src="assets/screenshots/create_deployment_5.png" alt="" />
</div>

## Onboarding devices
Onboarding devices is a straightforward process of two steps:
1. Register a device, by generating and downloading the credential file on the platform
2. Configure a device, by placing the credential file on the appropriate partition and path on the device's operating system image.

This allows any compatible linux device to be onboarded with minimal effort. Currently, the Seashell OS is available for the complete Raspberry Pi, Beaglebone and BeagleCore device families.

> [!NOTE]
> Additional hardware platforms are to follow, driven by customer demand. To integrate a custom board or adapt a custom operating system, instructions can be found [here](https://www.google.com).


#### Registering a device
Access the `Devices` tab on a project with a running deployment, or create a project and a deployment if there are none avaiable. Register a new device by clicking on the`new device` card. This will prompt for device configuration options, which are disabled for the private beta. After clicking the `provision` button, the process of registering the device within the deployment will be triggered. 

<div>
    <img src="assets/screenshots/onboard_device_2.png" alt="" />
</div>

After registration, devices are listed under `Provisoned devices` in the `Devices` tab of the project.

<div>
    <img src="assets/screenshots/onboard_device_3.png" alt="" />
</div>

#### Configuring a device

To configure a device for joining a deployment after its registration, a device credentials file is necessary.
Access the `Devices` tab of the project and click on `get settings` from the desired device card's collapsed menu.

<div>
    <img src="assets/screenshots/onboard_device_4.png" alt="" />
</div>

This will download a `device-<device-id>.json` credentials file, e.g. `device-hvrjwe58ik1w.json`  with the following content:
```json
{
  "name": "device-hvrjwe58ik1w",
  "drago": {
    "server": "http://35.207.128.119:8080",
    "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJleHAiOjE5MTAzMDMyMzgsImlhdCI6MTU5NDk0MzIzOCwiaWQiOiI3NGU1NzAyZS0xZDI0LTRlZmUtYTUzYi1lYTExNzZkOGNmYWMiLCJsYWJlbHMiOlsiZGV2aWNlIl0sIm5iZiI6MTU5NDk0MzIzOCwic3ViIjoiM2Y0Y2YxNTUtMzUwYS00NjUzLTg4OTEtMjM2ZGI0NzgwYjQ1IiwidHlwZSI6ImNsaWVudCJ9.vSEtCWEkTgDvAur9VsClDKTx2RhpbZesozio2Ph11Mk"
  }
}
```

Download the appropriate Seashell OS image. Seashell OS images can be donwloaded from the web dashboard under `platforms` in the `explore` tab on the left menu.

<div>
    <img src="assets/screenshots/os_platforms.png" alt="" />
</div>


Flash the image to an SD card using the tool of your choice. We recommend using the *bmaptool* for its performance advantages against other common tools. General information about it can be found [here](https://github.com/intel/bmap-tools). 

```sh
bmaptool copy --nobmap <path_to_seashell_os_image> <path_to_sd_card_device>
```

Mount the SD card and place the downloaded credentials file in the image's root partition under `/etc/seashell.json`.

```sh
cp <path_to_device_credentials_file> <path_to_sd_card_root_partition>/etc/seashell.json
```

Although not required, it is recommended to expand the image's root partition to fill the SD card, in order to better use the available resources. Instructions on using *parted* to achieve this can be found at the arch linux official documentation [here](https://wiki.archlinux.org/index.php/Parted#Resizing_partitions).

> [!TIP]
> Seashell OS comes with an utility for configuring a device's wifi connection. Upon boot, if no internet connection is detected, an unprotected network with SSID set to the device's id is brought up, e.g `device-hvrjwe58ik1w`. Once connected to this network on a mobile phone or computer, the user is redirected to a captive portal where the desired internet connection can be selected and its password set. 

Insert the SD card and boot the device. Upon a sucessfull boot, once connected to the internet, the device will automatically establish the apropriate connections to the cloud services, becoming available for receving workloads and being managed thorugh the platform. 

This can be verified by accessing Nomad's user interface, available from the project's deployment page at the web dashboard, and checking for registered clients with `ready` state.

<div>
    <img src="assets/screenshots/onboard_device_6.png" alt="" />
</div>

## Interacting with a deployment
TODO: move to a different section
