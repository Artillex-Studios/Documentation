# Title & Actionbar

### Description
- Sends a title and actionbar to players who join

### Configuration
(might not be up to date)

<code-block lang="yaml" ignore-vars="true" collapsible="false" validate="false">
    <![CDATA[
# set to false to disable the module
enabled: true

# after how many ticks should the title/action bar be sent?
# 20 ticks = 1 second
send-delay-ticks: 10

# welcome title
join-title:
  enabled: true
  title: "&#FF4500Welcome &f%player%&#FF4500!"
  subtitle: "&#FFAAAABuy perks @ shop.example.com"
  # times are all in milliseconds
  # 1 second = 1000 milliseconds
  times:
    fade-in: 500
    stay: 2000
    fade-out: 500

# welcome action bar
join-action-bar:
  enabled: true
  message: "&#FF4500Welcome &f%player%&#FF4500!"

# do not change this value
version: 1
    ]]>
</code-block>
