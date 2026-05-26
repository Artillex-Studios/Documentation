# Commands

| Command                          | Permission                                                            | Given by Default |
|----------------------------------|-----------------------------------------------------------------------|------------------|
| /axchat                          | axchat.help                                                           | true             |
| /axchat reload                   | axchat.reload                                                         | op               |
| /msgtoggle [player]              | axchat.msgtoggle (axchat.msgtoggle.others for the player parameter)   | true, op         |
| /socialspy [player]              | axchat.socialspy (axchat.socialspy.others for the player parameter)   | op, op           |
| /commandspy [player]             | axchat.commandspy (axchat.commandspy.others for the player parameter) | op, op           |
| /ignore &lt;player>              | axchat.ignore                                                         | true             |
| /staffchat [player]              | axchat.staffchat (axchat.staffchat.others for the player parameter)   | op, op           |
| /helpop &lt;message>             | axchat.helpop                                                         | true             |
| /report &lt;player> &lt;message> | axchat.report                                                         | true             |
| /alert &lt;message>              | axchat.alert                                                          | op               |

* Note: some commands can have aliases, like /staffchat, /commandspy, etc. The same permissions apply to those as for example for /axchat staffchat, /axchat commandspy