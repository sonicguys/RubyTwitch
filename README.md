# TwitchChatbot
A simple chatbot for Twitch written in Ruby. Used for handling commands and previewing chat so that you don't need to have the browser open and can avoid using a lot of RAM and CPU.

----

## Preview
![alt text](https://i.imgur.com/QOuqtfS.png "Preview of the chat bot")

----

I use this chatbot to preview chat without having a browser open so that I save CPU and RAM.
But as you can see in the preview image it's also able to handle custom commands including API commands.

----

## How To Use:  
1. Clone this repo to the system which will run the bot
2. `cd` into the repo root and create the file `./credentials.txt` (i.e. `touch credentials.txt`)
2. Copy/paste into the file as such:
  *     OAUTH = "oauth:GENERATED_OAUTH_TOKEN"
        CHANNEL = "TWITCH_CHANNEL_NAME"
        BOTNAME = "TWITCH_USERNAME"
  * Generate the token for the **OAUTH value** from
    <https://twitchapps.com/tmi/>
  * The **CHANNEL value** is the path fragment of your Twitch URL:
    <s>https://twitch.tv/</s>channel_name
  * The **BOTNAME value** is your Twitch username or the bot's
    username (if you created a separate one)
2. Run `ruby TwitchBot.rb`

----  

## **Adding Commands:**  
### **Regular Commands:**  
1. Open **"CommandsHandler.rb"** and scroll down to the `commands` array and add your own.
2. Go to folder **"Responses"** and add the command as a text file in all lowercase. _Examples have been included_  

### **Admin Commands:**  
If you are adding admin commands add a custom response next to it. There you'll be able to add commands that gives data to the socket instead of a chat message as a response. Example:  
    `admin_commands = {
		"disconnect" => "PART ##{CHANNEL}"
		}`  
  
When the command `"!disconnect"` has been typed in chat by the channel owner _(or anyone specified in the `admins` array)_ it will send a request to disconnect from the current Twitch channel.   
  
![alt text](https://i.imgur.com/iYtSvaG.png "Prefix, commands and admin commands")  
  
### **API Commands:**  
If you want to add API commands you just scroll down to `# ----- API COMMANDS ----- #` _(First section after receiving messages)_ and add your commands. In the example it calls some functions which are made at the bottom of the script.  
![alt text](https://i.imgur.com/CBF7vYf.png "Right after the received messages section")  
  
Then you scroll down to the bottom under `# ----- API COMMANDS ----- #` and add a function to that command.  
![alt text](https://i.imgur.com/xejccqp.png "Here you add your dedicated function for the API command")  

----

## Extras:
_**The response files in the Responses folder have 3 arguments available**_ (You can add your own)  

![alt text](https://i.imgur.com/Pb6JPz8.png "Preview of command arguments")

In the template the arguments USER, CHANNEL, COMMANDS are available. _(COMMANDS shows all available commands)_  
  
![alt text](https://i.imgur.com/7oRcLvw.png "Here you can add your replacements")  


## License
[![FOSSA Status](https://app.fossa.io/api/projects/git%2Bgithub.com%2FBenTearzz%2FRubyTwitchChatbot.svg?type=large)](https://app.fossa.io/projects/git%2Bgithub.com%2FBenTearzz%2FRubyTwitchChatbot?ref=badge_large)
