# Commands

| Command                                      | Permission                                       | Default  | Description            |
|----------------------------------------------|--------------------------------------------------|----------|------------------------|
| /axhoes [help]                               | axtools.help                                     | true     | Help                   |
| /axhoes give &lt;player> [level]             | axtools.give                                     | OP       | Give hoe to player     |
| /axhoes tool setlevel &lt;level> [reset-xp]  | axtools.tool.setlevel                            | OP       | Set tool level         |
| /axhoes tool setxp &lt;xp>                   | axtools.tool.setxp                               | OP       | Set tool XP            |
| /axhoes tool setprestige &lt;prestige>       | axtools.tool.setprestige                         | OP       | Set tool prestige      |
| /axhoes reload                               | axtools.reload                                   | OP       | Reload configuration   |
| /axhoes essence view [player]                | axtools.essence.view, axtools.essence.view.other | true, OP | View essence balance   |
| /axhoes essence give &lt;player> &lt;amount> | axtools.essence.give                             | OP       | Give essence           |
| /axhoes essence take &lt;player> &lt;amount> | axtools.essence.take                             | OP       | Take essence           |
| /axhoes essence set &lt;player> &lt;amount>  | axtools.essence.set                              | OP       | Set essence            |
| /axhoes essence reset [player]               | axtools.essence.reset                            | OP       | Reset essence          |
| /axhoes essence pay &lt;player> &lt;amount>  | axtools.essence.pay                              | true     | Send essence to player |
| /axhoes xp view [player]                     | axtools.xp.view, axtools.xp.view.other           | true, OP | View player xp balance |
| /axhoes xp give &lt;player> &lt;amount>      | axtools.xp.give                                  | OP       | Give player xp         |
| /axhoes xp take &lt;player> &lt;amount>      | axtools.xp.take                                  | OP       | Take player xp         |
| /axhoes xp set &lt;player> &lt;amount>       | axtools.xp.set                                   | OP       | Set player xp          |
| /axhoes xp reset [player]                    | axtools.xp.reset                                 | OP       | Reset player xp        |
| /axhoes xp reset [player]                    | axtools.xp.reset                                 | OP       | Reset player xp        |
| /axhoes shop [player]                        | axtools.shop, axtools.shop.other                 | true, OP | Open shop gui          |
| /axhoes leaderboard [player]                 | axtools.leaderboard, axtools.leaderboard.other   | true, OP | Open leaderboard gui   |

> Note that the permissions start with `axtools`, not axhoes!