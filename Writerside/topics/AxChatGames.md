# AxChatGames

### What is AxChatGames?
- A feature rich chat game plugin with 7 games and many variations.

![image_105.png](image_105.png)

## Most Important Features
- Ability to add **unlimited** command/item rewards to each game type.
- **Word Lists**: Instead of copy-pasting the same words for all games, you can define word lists which can be used easily for multiple games.
- **Builtin Word Lists**: All minecraft blocks, items, entities, downloaded at first startup (**1700**+ minecraft related words)
- Option to notify users if they have the incorrect capitalization.

![image_98.png](image_98.png)

- Customizable sounds
- Optional **Title/Subtitle/Actionbar** support for start/win/end messages.
- Game Type chance (it is possible to make certain game types appear more often)
- Ability to disable game types
- 4 Databases Supported: H2, SQLite, MySQL, PostgreSQL
- /chatgames toggle command to disable messages and sounds
- Hover message support (using minimessage)
- Placeholders
- Folia Support
- Toggleable case-sensitive and case-insensitive mode
- Minimum required players setting
- Start games manually
- Ability to start custom games for some modes
- World Blacklisting: Make players unable to see/win chat games from certain worlds
- **Statistics Command:**

![image_99.png](image_99.png)

- **Global and per Game Type top wins/record time Leaderboards:**

![image_101.png](image_101.png)
* *note: only 1 player is shown as on the dev server only 1 account had wins*

- **Ingame Log reader to see and filter wins:**

![image_104.png](image_104.png)

![image_103.png](image_103.png)

- **Status Command to see when was a game type last happened**

![image_102.png](image_102.png)

### Game Types
**Completion**:
- Some letters of the word will be missing (example: Gol__n _p__e) and players have to figure out which was the original word.
- **Configurable**: It is possible configure the percent (%) of missing characters.

![g1.webp](g1.webp)

**Guess The Number**:
- a random number will be generated and the first to guess it wins
- **Configurable**: You can set the range in which the numbers will be generated.

![g2.webp](g2.webp)

**Math**:
- a randomly generated math equation will be generated and players have to solve them to win.

![g3.webp](g3.webp)

- **Configurable**: You can fully customize what kind of math questions are generated.

![g4.webp](g4.webp)

**Trivia**:
- A question will be sent in the chat and players have to answer it.
- **Configurable**: Create any number of questions.
- The default config comes with more than 50 minecraft related questions.

![g5.webp](g5.webp)

**Type**:
- A random word will be picked and players just have to write them out.

![g6.webp](g6.webp)

- **Configurable**: Randomized Text Option

![g7.webp](g7.webp)

**Unreverse**:
- A random word will be picked and players have to write them out backwards.

![g8.webp](g8.webp)

- **Configurable**: Randomized Text Option

![g9.webp](g9.webp)

**Unscramble**:
- A random word will be picked and scrambled and players have to figure out the original word.
- **Smart Scramble** option: When a word contains a space, the different sections won't be mixed up, for example: "Jungle Sapling" will always be something like: "lgeJun alSignp", instead of: "aSplgiJg lunne"

![g10.webp](g10.webp)