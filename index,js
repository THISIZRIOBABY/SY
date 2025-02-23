const { Client, GatewayIntentBits, EmbedBuilder } = require('discord.js');
const { joinVoiceChannel, createAudioPlayer, createAudioResource, AudioPlayerStatus, VoiceConnectionStatus } = require('@discordjs/voice');
const play = require('play-dl'); 
require('dotenv').config();
const fs = require('fs');
const client = new Client({
  intents: [GatewayIntentBits.Guilds, GatewayIntentBits.GuildVoiceStates, GatewayIntentBits.GuildMessages, GatewayIntentBits.MessageContent]
});
const express = require("express")
const app = express();
var listener = app.listen(process.env.PORT || 2000, function () {
  console.log('Your app is listening on port ' + listener.address().port);
});
app.listen(() => console.log("I'm Ready To Work..! 24H"));
app.get('/', (req, res) => {
  res.send(`
  <body>
  <center><h1>Bot 24H ON!</h1></center
  </body>`)
});
client.on('ready', () => {
  console.log(`✅ | Logged in as ${client.user.tag}`);
});


const voiceChannelId = '1321172630757310516';
const staffChannelID = '1339207954360172575';
const staffRoleID = '1323676350644621396';
const audioFilePath = './support.mp3'; 


client.on('voiceStateUpdate', (oldState, newState) => {
  if(newState.member.user.bot) return;
  if (newState.channelId === voiceChannelId && oldState.channelId !== voiceChannelId) {
    const channel = newState.channel;
    const connection = joinVoiceChannel({
      channelId: channel.id,
      guildId: channel.guild.id,
      adapterCreator: channel.guild.voiceAdapterCreator,
    });
    const player = createAudioPlayer();
    const resource = createAudioResource(fs.createReadStream(audioFilePath));
    player.play(resource);
    connection.subscribe(player);
    const staffChannel = newState.guild.channels.cache.get(staffChannelID);
    
    if(staffChannel) {
        staffChannel.send(`**fama chkoun fi waiting** \n<@&${staffRoleID}>`);
    } else {
        console.log('1339207954360172575');
    }
  }
});
client.login(process.env.TOKEN);
