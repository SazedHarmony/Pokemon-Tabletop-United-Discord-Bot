# Pokemon-Tabletop-United-Discord-Bot

This Discord bot allows for quick access to Pokemon, moves, power, etc. for the Pokemon Tabletop United tabletop RPG system.

## Setup:
  - Create an application at https://discordapp.com/developers/applications/me
  - Click on the Bots tab and add a Bot
  - Name it PTU Helper Bot
  - Copy the generated token into your auth.json file
  - Go back to the General Information tab and copy the client ID
  - Replace CLIENT_ID with your client ID in the following url: https://discordapp.com/oauth2/authorize?&client_id=CLIENT_ID_HERE&scope=bot&permissions=0
  - Paste that link into your browser and when prompted, select the server for your bot to be placed in and authorize
  - Go back to your Discord browser tab with the bot, click on OAuth2
  - Under scopes, click the bot checkbox, then check the Send Messages and Read Message History checkboxes
  - Scroll back up to scopes, and copy the generated url
  - Paste that link into your browser, and authorize the bot for your server
  - Download and install Node.js at https://nodejs.org/en/download/ if you don't have it installed already
  - If you are on a Windows machine, open up Windows PowerShell, if you are on Mac or Linux, open the terminal
  - Navigate to your bot.js file
  - Run node bot.js
  - You should receive three lines of messages, your bot will then come online
	
	**NOTE**: This bot will only run as long as you have the terminal or Powershell session up, to have it perpetually up, see below
	
## Setup on AWS for perpetual online activity:
* Go to https://aws.amazon.com/ and create an account/login
* Select EC2 in the AWS Management Console
* Launch an Instance and select a Free Tier Amazon Linux AMI
* The Instance Type should automatically be the free tier, but if not select the free tier option, then click the Review and Launch button
* Click the Launch button, and Create a new key pair
* Input a name for the key pair and download & save the file, then Launch the Instance
* Go back and view your instances, it may take a bit for AWS to get it up and running
* When it is ready, click Connect and select EC2 Instance Connect
* Update the AMI by typing 'sudo yum update'
* When prompted, type 'y' to allow downloading to take place
* After downloading and updating is completed, download and open a SFTP program such as Cyberduck
* Click Open Connection
* In the server box, copy a url that looks like this ec2-##-###-##-##.us-west-2.compute.amazonaws.com from the instance in the AWS console (labeled Public DNS (IPv4))
* The username will be ec2-user and there will be no password
* In the SSH Private Key section, click choose and navigate to the .pem file you downloaded earlier, then click Connect
* Allow the Unknown fingerprint
* Click and drag the Discord bot folder into the center, it will copy it all over
* After it is copied over, you may close out of your SFTP program
* Switch back to the Linux AMI window
* Paste 'wget -qO- https://raw.githubusercontent.com/nvm-sh/nvm/v0.35.0/install.sh | bash' into the shell
* Close and restart the window
* Type 'nvm install node'
* Navigate into the Bot folder using 'cd Bot_folder'
* Type 'node bot.js & disown'
* The bot will now run as long as the EC2 instance is running
	
	**NOTE: You may be charged even on the free tier level, depending on usage!**
	
## Commands (case-sensitive)
- Capture Rate: '!capture'  Presents the Capture Rate formula
- Pokemon Info: '!pokemon Pikachu' Lists the Pokemon's Pokedex information
- Keywords: '!keyword Keyword' The following keywords are valid, Class, Bind, Bound, +Stat, Ranked, Order, Orders, Training, and Strategem
- Move: '!move Move' Details relevant information for Pokemon moves
- Ability: '!ability Ability' Lists the Effects of a given Ability
- Experience: '!exp' Lists the formula for Experience '!exp TotalLevelOfEnemiesAsANumber SignificanceIntegerAsDecidedByTheGM NumberOfPlayers' for an automatic calculation of experience
- Combat Stages: '!cs UnmodifiedStat CombatStage' Calculates the current Stat value at a given Combat Stage
- Damage Base: '!db DamageBase' Provides the amount of damage at a given Damage Base
