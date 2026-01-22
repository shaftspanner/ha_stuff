# ShaftSpanner's Home Assistant Stuff

This is my repository for sorting some ideas and projects using Home Assistant

## Pangolin Public Resource Control from Home Assistant

- [**Pangolin Resource Control**](./pangolin_control.md).  Enable or Disable a Pangolin public resource from within Home Assistant using RESTful commands and the Pangolin Integration API

## Automations

 - [**Automatic Porch Light**](./automations/automatic_porch_light.md).  Turn on the porch light at night if the front door is opened, or if the Ring doorbell detects motion

## Proxmox Control

Controlling Proxmox VE virtual machines and LXCs using Home Assistant.  Topics explored:

- Bubble Card
- Bubble Card styling
- Scripts
- Python scripts: Python set_state
- Passing fields to scripts

Link: [Proxmox Container and Virtual Machine Control](./proxmox_control.md)

## Docker Control

Controlling Docker containers using Home Assistant.  This is a modified version of my [Proxmox Control](#proxmox-control) write-up above.  Topics explored:

- Bubble Card
- Bubble Card styling
- Scripts
- Passing fields to scripts

Link: [Docker Container Control](./docker_control.md)

## Signal Lights

Use lights as a signal to alert someone to something!

This is a simple script with a field that allows you to flash any `on`/`off` light, returning the light to its original state after the script has run

Link: [Signal Lights](./signal_lights.md)