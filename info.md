# Set State
Home Assistant Python Script to force set an entity state

## How it works
This script adds a service that lets you update the state and/or attributes of any entity, similar to the developer tools

Requires `python_script:` to be enabled in you configuration

## Service arguments

| key             | required | type    | description                                                                                                                                                           |
|-----------------|----------|---------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `entity_id:`    | True     | string  | The full entity id to update                                                                                                                                          |
| `state:`        | False    | any     | The state value                                                                                                                                                       |
| `state_id:`     | False    | any     | The state of a other entity                                                                                                                                           |
| `allow_create:` | False    | Boolean | Allow the entity to be created if it does not exists (Defaults to false so mis-typed entities do not                                       accidentally get created.) |
| `...:`          | False    | any     | any additional name becomes or replaces and attribute on the entity                                                                                                   |


## Usage
Each call requires at least an entity_id and a state or attributes (otherwise it wont do anything)

example:

```
service: python_script.set_state
data:
 entity_id: sensor.random_sensor
 state: "off"
 
service: python_script.set_state
data:
 entity_id: sensor.random_sensor
 state_id: sensor.random_other_sensor
```

(Thanks to [@rodpayne](https://community.home-assistant.io/u/rodpayne) for the initial script:
(https://community.home-assistant.io/t/how-to-manually-set-state-value-of-sensor/43975)
