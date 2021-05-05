# Home Automation with esphome

## Boards

esp8266 board: nodemcu V2
esp32 board: esp32doit-devkit-v1 (ESP-WROOM-32 Dev Kit V1)

## Getting Started

We need Python3 and Pip3 to install esphome

### Install Python

* Chocolatey `choco install python3`
* winget `winget install -e --id Python.Python`
  
### Install pip

* Debian `sudo apt install python3-pip`

### installing esphome

`pip3 install esphome`

### Compiling with esphome

`esphome example.yaml compile`

### To Compile and Download

`esphome example.yaml run`

if the devices is connected via USB it'll ask for the com port selection and flashes it to the board. if you've already have firmware on the board, select OTA and enter OTA password if you've added it to the [secrets.yaml](#secretsyaml)

## secrets.yaml

You need secrets.yaml config file with WiFi details, mqtt details(if mqtt is used) to compile. Follow bellow steps to create a secrets.yaml

### Method One

* Create new file named secrets.yaml in the same directory
* add the file name to `.gitignore`
* add content mentioned bellow to [secrets.yaml](#secrets-eg) file and replace/add the required details

### Method Two: (Recommended)

* Create new directory in some other location other than this repo
* create secrets.yaml
* create a [link](#symbolic-link-for-secrets) between those two folders for secrets.yaml [(follow the method given later here)](#secrets-eg)

### Secrets eg

#### With MQTT

````yaml
wifi_ssid: "ssid"
wifi_password: "wifi-password"
api_password: ""
ota_password: ""
mqtt_broker: ""
mqtt_port: 1883
mqtt_username: ""
mqtt_password: ""  
````

#### Without MQTT

````yaml
wifi_ssid: "ssid"
wifi_password: "wifi-password"
api_password: ""
ota_password: ""
````

#### Use example file

Example file for secrets is already included in the repo. Rename file from `secrets.yaml.example` to `secrets.yaml` and add the correct details and compile. Otherwise you can download the file [Here](/blob/master/secrets.yaml.example).

### Symbolic link for secrets

* Windows: (Elevated Command Prompt) `mklink /H "$targetpath" "$sourcepath"`
* Linux: `ln -s "path/secrets.yaml" .`
