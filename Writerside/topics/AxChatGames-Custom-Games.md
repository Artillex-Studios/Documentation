# Custom Games

* The plugin allows for starting custom games. These games will follow the builtin gamemodes, however you can manually give an answer or sometimes even the question can be customized!
* Note: this is not the same as `/chatgames start <game>`!

> You can put spaces in your inputs by covering them with quotation marks ("value")

### How to start a custom game?
- You can use the following command: `/chatgames custom <game> <settings...>`

### Parameters:

**type / unreverse / unscramble**
- `/chatgames custom <game> <word>`
- Start a game with custom word
- **Example**: `/chatgames custom type "my custom word"`

![image_107.png](image_107.png)

**completion**
- `/chatgames custom completion <word> [missing percent]`
- Start a game with custom word and set how many percent (%) of the letters are missing
- The missing percent value is optional, if it is missing, the default configured value will be used.
- **Example**: `/chatgames custom completion "my custom word" 30`

![image_108.png](image_108.png)

**math**
- `/chatgames custom math <math hint> <answer>`
- Start a game with a custom math equation. You also have to give the answer.
- **Example**: `/chatgames custom math "√4" 2`

![image_109.png](image_109.png)

**trivia**
- `/chatgames custom trivia <question> <answer>`
- Start a game with a custom question and answer. Answers are case-insensitive.
- **Example**: `/chatgames custom trivia "my custom question" "my custom answer"`

![image_110.png](image_110.png)

**guess_the_number**
- `/chatgames custom guess_the_number <minimum value> <maximum value> [answer]`
- Start a game with a custom question and answer. Answers are case-insensitive.
- The answer value is optional, if it is missing, a random value will be picked within the given number range.
- **Example**: `/chatgames custom guess_the_number 5 10 8`

![image_111.png](image_111.png)