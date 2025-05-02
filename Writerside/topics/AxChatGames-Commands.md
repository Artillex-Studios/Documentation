# Commands

| Command                                            | Permission             | Description                            | Default                    |
|----------------------------------------------------|------------------------|----------------------------------------|----------------------------|
| /axchatgames help                                  | axchatgames.help       | View help                              | true                       |
| /axchatgames reload                                | axchatgames.reload     | Reload plugin                          | OP                         |
| /axchatgames start [game]                          | axchatgames.start      | Start chat game                        | OP                         |
| /axchatgames custom <game> <settings..>            | axchatgames.custom     | Start game with custom answer          | OP                         |
| /axchatgames stop [game]                           | axchatgames.stop       | Stop chat game                         | OP                         |
| /axchatgames stopall                               | axchatgames.stopall    | Stop all chat games                    | OP                         |
| /axchatgames statistics [player]                   | axchatgames.statistics | Show statistics of player              | true (player parameter op) |
| /axchatgames toggle                                | axchatgames.toggle     | Toggle broadcast visibility and sounds | true                       |
| /axchatgames top &lt;records/wins> [game]          | axchatgames.top        | View leaderboard                       | true                       |
| /axchatgames top update                            | axchatgames.top.update | Manually update leaderboards           | OP                         |
| /axchatgames status                                | axchatgames.status     | Display when last games happened       | OP                         |
| /axchatgames logs global [page] [game]             | axchatgames.logs       | Display win logs                       | OP                         |
| /axchatgames logs player &lt;player> [page] [game] | axchatgames.logs       | Display win logs                       | OP                         |
| /axchatgames reset &lt;player> [game]              | axchatgames.reset      | Reset stats of player                  | OP                         |

* note: there are multiple command aliases that can be used (axchatgames, axchatgame, axcg, chatgames, chatgame, cg)