# Discord Webhook Builder

> Some of these might not work in all of our plugins!
{style="warning"}

On this page you can find every webhook related configuration that is possible to create in our plugins!

### Example:

```yaml
    content: "Get ready!"
    color: "#FF0000"
    title:
      text: "Example - STARTED"
    fields:
      1:
        inline: true
        name: "Time"
        value: "100"
```

### Content:
* The content field is the only that can contain a working ping, example: `<@&1234567890123456789>`
```yaml
  content: "Content Field"
```

## Embeds:

### Title (required)
```yaml
    title:
      # required
      text: 'Title text!'
      # optional
      icon: ""
```

### Color (optional)
```yaml
    color: "#RRGGBB"
```

### Description (optional)
```yaml
    description: "Description"
```

### Field (optional)
* You can add multiple fields
```yaml
    fields:
      '1':
        # optional
        inline: true
        # required
        name: "Name"
        # optional
        value: 'Value'
```

### Author (optional)
```yaml
    author:
      # required
      name: 'Author Text'
      # optional
      icon-url: "some-url"
      # optional
      url: "some-url"
```

### Footer (optional)
```yaml
    footer:
      # required
      text: 'Footer Text'
      # optional
      icon: "some-url"
```

### Image URL (optional)
```yaml
    image-url: "some-url"
```

### Thumbnail URL (optional)
```yaml
    thumbnail-url: "some-url"
```