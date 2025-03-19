# Bubble Card Styling Snippets

A dumping ground for various code snippets used to style aspects of the awesome [Bubble Cards](https://github.com/Clooos/Bubble-Card)

Each example includes enough code to make a fully functional button

All snipets are tested on [v2.4.0](https://github.com/Clooos/Bubble-Card/releases/tag/v2.4.0)

## Setup

The snippets rely on having 2 toggle helpers defined `temp_toggle` and `temp_toggle_2`

```yaml
# Example configuration.yaml entry
input_boolean:
  temp_toggle:
    name: Toggle to demonstrate button styling
  temp_toggle_2:
    name: Another toggle to demonstrate button styling
```

## Rotating Icon

The existing (or default) icon rotates when the linked input boolean is `on`.  In this case, that could be triggered remotely (e.g. a manual switch) or by toggling the button itself

**Insert Example Here**

<details>
  <summary>YAML Code</summary>

```yaml
type: custom:bubble-card
card_type: button
button_type: state
entity: input_boolean.temp_toggle
name: Rotating Icon
styles: |-
    .bubble-icon {
    animation: ${hass.states['input_boolean.temp_toggle'].state === 'on' ? 'slow-rotate 2s linear infinite' : ''};
    }
    @keyframes slow-rotate {
    0% { transform: rotate(0deg); }
    100% { transform: rotate(360deg); }
    }
button_action:
    tap_action:
    action: toggle
```
</details>

## Rotating Sub-Button Icon

When the input boolean is toggled (either remotely or by pressing the sub-button), the sub-button icon changes to a loading symbol and rotates

**Insert Example Here**

<details>
  <summary>YAML Code</summary>

```yaml
type: custom:bubble-card
card_type: button
button_type: state
entity: input_boolean.temp_toggle
name: Rotating Sub-button-1
sub_button:
  - name: Toggle
    tap_action:
      action: toggle
    icon: mdi:server
    state_background: false
styles: >-
  .bubble-sub-button-1 { 
    animation: ${hass.states['input_boolean.temp_toggle'].state === 'on' ? 'slow-rotate 2s linear infinite' : ''};
  } 

  @keyframes slow-rotate { 
    0% { transform: rotate(0deg); } 
    100% { transform: rotate(360deg); } 
  }

  ${subButtonIcon[0].setAttribute("icon",
  hass.states['input_boolean.temp_toggle'].state === 'on' ? 'mdi:loading' 
     : hass.states['input_boolean.temp_toggle'].state === 'off' ? 'mdi:server' :'mdi:server' )}
tap_action:
  action: none
double_tap_action:
  action: none
hold_action:
  action: none
button_action:
  tap_action:
    action: none
  double_tap_action:
    action: none
  hold_action:
    action: none
```
</details>

## Rotating Sub-Button-1 with Color change

When the input boolean is toggled (either remotely or by pressing the sub-button), the sub-button icon changes to a loading symbol, changes color and rotates

**Insert Example Here**

<details>
  <summary>YAML Code</summary>

```yaml
type: custom:bubble-card
card_type: button
button_type: state
entity: input_boolean.temp_toggle
name: Rotating Sub-button-1 with color change
sub_button:
  - name: Toggle
    tap_action:
      action: toggle
    icon: mdi:server
    state_background: false
styles: >-
  .bubble-sub-button-1 { 
    background-color: ${hass.states['input_boolean.temp_toggle'].state != 'on' ? 'rgb(1, 1, 1)' : 'rgb(230, 128, 41)'} !important;
    animation: ${hass.states['input_boolean.temp_toggle'].state === 'on' ? 'slow-rotate 2s linear infinite' : ''};
  } 

  @keyframes slow-rotate { 
    0% { transform: rotate(0deg); } 
    100% { transform: rotate(360deg); } 
  }

  ${subButtonIcon[0].setAttribute("icon",
  hass.states['input_boolean.temp_toggle'].state === 'on' ? 'mdi:loading' 
     : hass.states['input_boolean.temp_toggle'].state === 'off' ? 'mdi:server' :'mdi:server' )}
tap_action:
  action: none
double_tap_action:
  action: none
hold_action:
  action: none
button_action:
  tap_action:
    action: none
  double_tap_action:
    action: none
  hold_action:
    action: none

```
</details>

## 2 Rotating Sub-Button with Color change

When the input boolean is toggled (either remotely or by pressing the sub-button), the sub-button-1 icon changes to a loading symbol, changes color and rotates.  The same happens with sub-button-2

**Insert Example Here**

<details>
  <summary>YAML Code</summary>

```yaml
type: custom:bubble-card
card_type: button
button_type: state
entity: input_boolean.temp_toggle
name: Two Sub-buttons, both changing icons, color and rotating
sub_button:
  - entity: input_boolean.temp_toggle
    name: Toggle
    tap_action:
      action: toggle
    icon: mdi:server
    state_background: false
  - entity: input_boolean.temp_toggle_2
    name: Toggle
    tap_action:
      action: toggle
    icon: mdi:reload
    state_background: false
styles: >-
  .bubble-sub-button-1 { 
    background-color: ${hass.states['input_boolean.temp_toggle'].state != 'on' ? 'rgb(1, 1, 1)' : 'rgb(230, 128, 41)'} !important;
    animation: ${hass.states['input_boolean.temp_toggle'].state === 'on' ? 'slow-rotate 2s linear infinite' : ''};
  }  .bubble-sub-button-2 { 
    background-color: ${hass.states['input_boolean.temp_toggle_2'].state != 'on' ? 'rgb(1, 1, 1)' : 'rgb(230, 128, 41)'} !important;
    animation: ${hass.states['input_boolean.temp_toggle_2'].state === 'on' ? 'slow-rotate 2s linear infinite' : ''};
  } 

  @keyframes slow-rotate { 
    0% { transform: rotate(0deg); } 
    100% { transform: rotate(360deg); } 
  }

  ${subButtonIcon[0].setAttribute("icon",
  hass.states['input_boolean.temp_toggle'].state === 'on' ? 'mdi:loading' 
     : hass.states['input_boolean.temp_toggle'].state === 'off' ? 'mdi:server' :'mdi:server' )}
  ${subButtonIcon[1].setAttribute("icon",
  hass.states['input_boolean.temp_toggle_2'].state === 'on' ? 'mdi:loading' 
     : hass.states['input_boolean.temp_toggle_2'].state === 'off' ? 'mdi:reload' :'mdi:reload' )}
tap_action:
  action: none
double_tap_action:
  action: none
hold_action:
  action: none
button_action:
  tap_action:
    action: none
  double_tap_action:
    action: none
  hold_action:
    action: none
```
</details>
