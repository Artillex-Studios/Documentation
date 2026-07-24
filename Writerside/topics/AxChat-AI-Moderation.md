# AI Moderation

- AxChat provides a AI check that you can use to moderate your players. This page contains all the information related to how it works and how to use it.

### Configuration
<procedure title="modules/moderation.yml" collapsible="true">
<code-block lang="yaml" ignore-vars="true" collapsible="false" validate="false">
<![CDATA[

	# uses artificial intelligence chatbots to analyse player messages and block disallowed content
	# requires an API key from one of the supported AI services
	# NOTE: the AI check sends an async request, so the [replace] and [cancel] punishment actions are not possible
	# we suggest using this module by requiring high confidence scores for punishments or you can also remove automatic mutes and just use it to notify human moderators
	example-ai-check:
	  enabled: false
	  type: ai
	  name: "%detection%"
	  bypass: "axchat.moderation.bypass"
	  scope:
		chat: true
		direct-messaging: true
		helpop: true
		report: true
		staff-chat: true
	  violation-expiry-minutes: 300
	  punishments:
		- "1:1 [alert]"
		- "1:1 [webhook]"
		- "1:1 [message] <#FF0000>%detection% is not allowed on the server!"
		- "1-1:1 [command] tempmute %player% 10m %detection%"
		- "2-2:1 [command] tempmute %player% 30m %detection%"
		- "3-3:1 [command] tempmute %player% 1h %detection%"
	  # the check requires using https://openrouter.ai/, you need an api key and a model
	  service:
		api-key: "YOUR API KEY HERE"
		# using a paid model is recommended to prevent rate limits causing errors
		model: "poolside/laguna-s-2.1:free"
	  # list of things that the AI should block
	  # the plugin will ask the model to score the message from 0-100% based on these factors
	  # you can add your own factors that you want the ai to score
	  detections:
		"harassment":
		  # the name that will be used for messages, only the section key above is sent to the AI
		  name: "Harassment"
		  # starting at what confidence percentage should the plugin punish the player?
		  punish: 50
		"hate":
		  name: "Hatred"
		  punish: 50
		"violence":
		  name: "Violence"
		  punish: 50
		"sexual":
		  name: "Sexual Content"
		  punish: 50
		"self harm":
		  name: "Self Harm"
		  punish: 50
		"scam":
		  name: "Scamming"
		  punish: 80

]]>
</code-block>
</procedure>

### How does it work?
- Every user message is sent to the model and the AI responds with a list of confidence percentage scores for each of your defined detections.
- If you confidence score is higher than the `punish` value of the detection, the plugin will run the punishments.

### Disclaimers
- We are not responsible for the plugin's token usage or the AI models, make sure to set strict budget limits in case anything goes wrong and monitor its usage.
- You should disclose to your users what AI model is receiving their messages for their own privacy.

### How to set it up?
- The AI check uses [OpenRouter](https://openrouter.ai/), so you should create an account first.
- You should receive an API key formatted like `sk-or-v1-...`. If you haven't, make sure to create a new one at [https://openrouter.ai/workspaces/default/keys](https://openrouter.ai/workspaces/default/keys)
- Next up you need to pick a text model from [https://openrouter.ai/models](https://openrouter.ai/models). We suggest choosing cheaper, light models considering that every chat message can use hundreds of tokens. If you are using a paid model, you will have to upload credits at [https://openrouter.ai/settings/credits](https://openrouter.ai/settings/credits)
- For this tutorial, lets use the included free model, `Poolside: Laguna S 2.1 (free)`, click on your selected model and copy the identifier. (you should only use this for testing as it is slow, and it is almost always rate limited)

![image_229.png](image_229.png)
- Now that you have got the API Key and the model of your choice, go to the plugins/AxChat/modules/moderation.yml and find the AI check or create a new one using the example at the top of the page.
- Make sure to set `enabled` to true, so the check will be active.
- Next, it is time to set your api key and model into the `service` section like this:

```yaml
service:
  api-key: "sk-or-v1-..." # make sure to replace this with your own api key!
  model: "poolside/laguna-s-2.1:free"
```
- And thats's all, run /axchat reload and test it out! (note that OP users by default have a bypass, so take away their `axchat.moderation.bypass` permission if needed)
- If you want, you can tweak the detections or add new ones. You can always add more more rules. You can also change the usual settings, like the punishments or the scope of the check.