# Model Support

- AxCrates supports model plugins which can be used as a crate block. Open/close animations are also possible.

### Supported Plugins
- ModelEngine v3
- ModelEngine v4

### Settings:
```yaml
texture:
    enabled: false
    # supported plugins: modelengine v3
    mode: "modelengine"
    model: "some-model"
    rotation: 0
    # leave "" if you don't have animations
    open-animation: ""
    close-animation: ""
```