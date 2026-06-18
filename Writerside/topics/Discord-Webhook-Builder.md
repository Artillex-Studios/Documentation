# Discord Webhook Builder

### List of plugins using this system:
| Plugin     | Version |
|------------|---------|
| AxAuctions | New     |
(everything else uses the legacy system)

<tabs>
<tab title="New">

<h3>Good to know:</h3>

- Most fields are optional.
- The content field is the only where you can add a working ping, example: `<@&1234567890123456789>`

<h3>Example using all options:</h3>

<code-block lang="yaml">
    webhook:
      content: "content"
      username: "username"
      avatar-url: "url"
      tts: false
      embeds:
        - title:
            text: "title"
            url: "https://dc.artillex-studios.com/"
          description: "description"
          timestamp: 1759315291174
          color: "#00CCFF"
          image-url: "https://example.com/"
          thumbnail-url: "https://example.com/"
          video-url: "https://example.com/"
          author:
            name: "author"
            url: "https://dc.artillex-studios.com/"
            icon-url: "https://example.com/"
          footer:
            text: "footer"
            icon-url: "https://example.com/"
          fields:
            - name: "field 1"
              value: "value 1"
              inline: true
            - name: "field 2"
              value: "value 2"
              inline: true
      thread-name: ""
      poll:
        question:
          text: "text"
        answers:
          - text: "answer 1"
            emoji: "😂"
          - text: "answer 2"
            emoji: "😂"
        expiry: 1759315291174
        allow-multiselect: false
</code-block>

</tab>
<tab title="Legacy">

<h3>Full Example:</h3>

<code-block lang="yaml">
    webhook:
        content: "Get ready!"
        color: "#FF0000"
        title:
          text: "Example - STARTED"
        fields:
          1:
            inline: true
            name: "Time"
            value: "100"
</code-block>

<h3>Content:</h3>
- The content field is the only where you can add a working ping, example: `<@&1234567890123456789>`
<code-block lang="yaml">
  content: "Content Field"
</code-block>

<h3>Title</h3>
<code-block lang="yaml">
    title:
      # required
      text: 'Title text!'
      # optional
      icon: ""
</code-block>

<h3>Color</h3>
<code-block lang="yaml">
    color: "#RRGGBB"
</code-block>

<h3>Description</h3>
<code-block lang="yaml">
    description: "Description"
</code-block>

<h3>Field</h3>
* You can add multiple fields
<code-block lang="yaml">
    fields:
      '1':
        # optional
        inline: true
        # required
        name: "Name"
        # optional
        value: 'Value'
</code-block>

<h3>Author</h3>
<code-block lang="yaml">
    author:
      # required
      name: 'Author Text'
      # optional
      icon-url: "some-url"
      # optional
      url: "some-url"
</code-block>

<h3>Footer</h3>
<code-block lang="yaml">
    footer:
      # required
      text: 'Footer Text'
      # optional
      icon: "some-url"
</code-block>

<h3>Image URL</h3>
<code-block lang="yaml">
    image-url: "some-url"
</code-block>

<h3>Thumbnail URL</h3>
<code-block lang="yaml">
    thumbnail-url: "some-url"
</code-block>

</tab>
</tabs>