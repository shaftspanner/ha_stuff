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
input_boolean:
  temp_toggle_2:
    name: Another toggle to demonstrate button styling
```

## Index

- [Conditionally Change Icon Color](#icon_color)
- [Rotating Icon](#rotating-icon)
- [Rotating Sub-Button Icon](#rotating-sub-button-icon)
- [Rotating Sub-Button-1 with Color Change](#rotating-sub-button-1-with-color-change)
- [2 Rotating Sub-buttons with Color and Icon Change](#2-rotating-sub-buttons-with-color-and-icon-change)

## Conditionally Change Icon Color

![Bubble Card button with icon that changes color when the button is clicked](../media/conditional_icon_color_change.gif)

The main icon color changes based on the value of another entity 

<details>
  <summary>YAML Code</summary>

```yaml
type: custom:bubble-card
card_type: button
button_type: state
entity: input_boolean.temp_toggle
name: Color Change Icon
styles: |-
  .bubble-icon {
    color: ${hass.states['input_boolean.temp_toggle'].state === 'on' ? 'rgb(0, 204, 0)' : ''} !important;
  }
button_action:
  tap_action:
    action: toggle
```
</details>

[🔼 Back to top](#bubble-card-styling-snippets)


## Rotating Icon

![Bubble Card button with icon that rotates when the button is clicked](../media/rotating_icon.gif)

The existing (or default) icon rotates when the linked input boolean is `on`.  In this case, that could be triggered remotely (e.g. a manual switch) or by toggling the button itself

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

[🔼 Back to top](#bubble-card-styling-snippets)

## Rotating Sub-Button Icon

When the input boolean is toggled (either remotely or by pressing the sub-button), the sub-button icon changes to a loading symbol and rotates

![Bubble Card button with sub-button.  Sub-button icon rotates when the button is clicked](../media/rotating_sub_button_icon.gif)

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

[🔼 Back to top](#bubble-card-styling-snippets)

## Rotating Sub-Button-1 with Color change

When the input boolean is toggled (either remotely or by pressing the sub-button), the sub-button icon changes to a loading symbol, changes color and rotates

![Bubble Card with sub-button.  When the sub-button is clicked, the icon changes to a loading symbol, changes color and rotates](../media/rotating_sub_button_icon_with_color_change.gif)

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

[🔼 Back to top](#bubble-card-styling-snippets)

## 2 Rotating Sub-Buttons with Color and Icon Change

When the input boolean is toggled (either remotely or by pressing the sub-button), the sub-button-1 icon changes to a loading symbol, changes color and rotates.  The same happens with sub-button-2

![Bubble Card with 2 sub-buttons.  When the each sub-button is clicked, the icon changes to a loading symbol, changes color and rotates](../media/2_rotating_sub_button_icons_with_color_change.gif)

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

[🔼 Back to top](#bubble-card-styling-snippets)

## Credits

Many thanks to the following who helped me with these snippets:

- [u/aponomar](https://www.reddit.com/user/aponomar/) - Help with the animated icons


[def]: ../media/rotating_icon.gif