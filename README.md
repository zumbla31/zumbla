{"name": "Zumbla Hunt", "channel_id": "502863265223933970", "token": "xEdjV6Zph5yWmhj_P3A0-_hc5r028Zp1TlwAlFl06ydAn0vEV8N_SA122tDdI-7WVMCO", "avatar": "f6e77572ae8dfe30ecbd63de68b75774", "guild_id": "502863264670023691", "id": "502937372305129483"}
node bot.js
var Discord = require('discord.io');
var logger = require('winston');
var auth = require('./auth.json');
// Configure logger settings
logger.remove(logger.transports.Console);
logger.add(logger.transports.Console, {
    colorize: true
});
logger.level = 'debug';
// Initialize Discord Bot
var bot = new Discord.Client({
   token: auth.token,
   autorun: true
});
bot.on('ready', function (evt) {
    logger.info('Connected');
    logger.info('Logged in as: ');
    logger.info(bot.username + ' - (' + bot.id + ')');
});
bot.on('message', function (user, userID, channelID, message, evt) {
    // Our bot needs to know if it will execute a command
    // It will listen for messages that will start with `!`
    if (message.substring(0, 1) == '!') {
        var args = message.substring(1).split(' ');
        var cmd = args[0];
       
        args = args.splice(1);
        switch(cmd) {
            // !ping
            case 'ping':
                bot.sendMessage({
                    to: channelID,
                    message: 'Pong!'
                });
            break;
            // Just add any case commands if you want to..
         }
     }
});
{
   "token": "YOUR-BOT-TOKEN"
}
{
  "name": "greeter-bot",
  "version": "1.0.0",
  "description": "My own Discord bot",
  "main": "bot.js",
  "author": "YOUR-NAME-HERE",
  "dependencies": {}
}
