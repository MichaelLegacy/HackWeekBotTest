# Discord Hack Week Event Reminder Bot
Simple bot for Discord Hack Week that will remind users of an event.

Set up and tested on Ubuntu 16.04.
It should work on other Ubuntu versions, similar linux distros or anywhere node runs at this point.
Requires a mysqlDB. May add DB setup steps in the future if needed.

1. Install Nodejs
 - I followed a guide and installed version 8.12.0, and npm 6.4.1
    ```
    cd ~
    curl -sL https://deb.nodesource.com/setup_8.x -o nodesource_setup.sh
    sudo apt-get install -y nodejs
    ```
  - Then confirm versions of node and npm with `node -v` and `npm -v`. 

  2. Clone the Repository
  
  3. `npm install`
  
  4. Get your bot token from your application on https://discordapp.com/developers/applications/ and add it into token.js
  
  5. Rename the \_config.json file to config.json and edit the database information to match your settings
  
  6. Run `sequelize db:migrate` or `node_modules/.bin/sequelize db:migrate` to setup the tables.
  
  6. Run bot with `node start.js`

Don't have a better place to put this yet so saving it here for now as well.
Run the following command to ensure token.js with added API token does not get added to repo.
`git update-index --skip-worktree token.js`

## Commands

**Creating an Event**

To create an event, you must have a role named `eventbotplanner` or have the default `Administrator` role.

`.createevent "[event title]" [days]-[hours]-[minutes]`

Example command for a WoW Raid that is happening in 2 hours and 20 minutes from now:

`.createevent "Wow Raid" 0-2-20`

**Deleting an Event**

To delete an event, you must be the event creator or have the Discord `Administrator` role. The event message should have the command in it, but just incase, you can perform this:

`.deleteevent [eventMessageID]`

**Signing Up For Event**

To sign-up for the event, all you need to to is react to the "✅" emoji. This will assign you an event role that is used for notifying. To cancel the sign-up, just unreact with the message. All other reactions with emojis will not change your sign-up status
