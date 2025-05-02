# Word Lists

> Feel free to share your custom word lists in our discord server at the `share-your-configs` channel so other can use them!
{style="note"}

[//]: # ( https://github.com/dgibbs64/discord-banners/blob/master/README.md)
[![A](https://discordapp.com/api/guilds/1130070418150133761/widget.png?style=banner2)](https://dc.artillex-studios.com/)

### What is the purpose of word lists?
- Word lists are used in some game types (type, unreverse) as the words that need to be typed out or unreversed.
- So basically this is where you can define which words do you want to see in games.
- Word lists are shared between games, so you don't have to copy paste your words multiple times. Also they are stored in plain text (.txt) for minimal space usage.

### Where can I find them?
- You can find them in the `plugins/AxChatGames/word-lists` folder!

### How can I edit a word list?
- It is very simple, you just open the txt file and write your new words in there! Make sure that you only put 1 word per line. So for example:
```plain text
word1
word2
word3 
```

### How can I create new word lists?
- First you need to go to the word-lists folder. Next simple create a new file. Make sure that it is a .txt (plain text) file. After that you can add your words. (make sure that you only write 1 word per line)
- Next up, you need to use this word list. Go to the game where you want to use your word list. For example the `games/type.yml` supports word lists.
- Search for the word-lists section in the game type's configuration file and add your word list by the name of the file. (without the .txt) For example let's add the "mywordlist.txt":
```yaml
# used word lists
# NOTE: these are not the used words!
# you can define/find them in the word-lists folder! we also include some default lists
# word lists are txt files which all include 1 word / row
word-lists:
- example
- minecraft-blocks
- minecraft-items
- minecraft-entities
- mywordlist
```
- And of course, you can remove other word lists that you don't need, the plugin includes some default minecraft names so the plugin is possible to use out of the box!