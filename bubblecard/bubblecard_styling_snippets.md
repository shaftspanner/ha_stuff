# Bubble Card Styling Snippets

A dumping ground for various code snippets used to style aspects of the awesome [Bubble Cards](https://github.com/Clooos/Bubble-Card)

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

**Insert Example Here**

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
## Rotating Sub-Button Icon

** Insert Example Here**

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


