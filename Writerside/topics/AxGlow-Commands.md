# Commands & Permissions

| Command                                           | Permission         | Default | Description        |
|---------------------------------------------------|--------------------|---------|--------------------|
| /axglow                                           | axglow.open        | true    | Open menu          |
| /axglow help                                      | axglow.help        | true    | View help          |
| /axglow toggle [player]                           | axglow.toggle*     | true    | Toggle glow on/off |
| /axglow set &lt;glow> [player]                    | axglow.set*        | true    | Set glow           |
| /axglow remove [player]                           | axglow.remove*     | true    | Remove glow        |
| /axglow visibility <all/own/others/none> [player] | axglow.visibility* | true    | Set visibility     |
| /axglow reload                                    | axglow.reload      | op      | Reload plugin      |
* The [player] parameter requires the `.others` permission, for example `axglow.toggle.others`.
* The `.others` permissions are only given to operators by default.

### Glow Permissions
- By default, the permission for colors is `axglow.color.<color>`, so for example `axglow.color.rainbow`.
- Note that this is 100% customizable in the glows folder.