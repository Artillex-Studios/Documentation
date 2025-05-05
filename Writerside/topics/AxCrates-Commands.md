# Commands

| Command                                                                                    | Permission           | Description            | Default |
|--------------------------------------------------------------------------------------------|----------------------|------------------------|---------|
| /axcrates help                                                                             | axcrates.help        | View help              | true    |
| /axcrates give &lt;player(s)> &lt;key> [amount] [--silent] [--virtual]                     | axcrates.give        | Give keys to players   | OP      |
| /axcrates take &lt;player(s)> &lt;key> [amount] [--silent] [--physical]                    | axcrates.take        | Take keys from players | OP      |
| /axcrates transfer &lt;player> &lt;key> [amount]                                           | axcrates.transfer    | Transfer virtual keys  | true    |
| /axcrates keys                                                                             | axcrates.keys        | Check virtual keys     | true    |
| /axcrates keys [player]                                                                    | axcrates.keys.others | Check virtual keys     | op      |
| /axcrates drop location &lt;key> &lt;world> &lt;x> &lt;y> &lt;z> [amount] [--withVelocity] | axcrates.drop        | Drop key at location   | op      |
| /axcrates drop entity &lt;key> &lt;entity> [amount] [--withVelocity]                       | axcrates.drop        | Drop key at entity     | op      |
| /axcrates show &lt;crate>                                                                  | axcrates.show        | Show crate preview     | true    |
| /axcrates show &lt;crate> [player]                                                         | axcrates.show.others | Show crate preview     | op      |
| /axcrates open &lt;crate> &lt;player> [amount] [--force] [--silent]                        | axcrates.open        | Open create for player | op      |
| /axcrates reload                                                                           | axcrates.reload      | Reload configuration   | op      |
| /axcrates editor [crate]                                                                   | axcrates.editor      | Open editor            | op      |

* note: there are multiple command aliases that can be used (axcrate, axcrates, crate, crates)