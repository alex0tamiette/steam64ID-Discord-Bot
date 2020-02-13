# steam64ID-Discord-Bot

#Briefing
This is my first project in Node.js
The idea is a simple bot that takes usernames on a Discord message and reply with the Steam64ID found
Im not a developer, so my code can be improved a lot, I just wanted this and I got it!
So far it works so I'm happy about it \O/

#What I used
Node.js > https://nodejs.org/en/ \n
Discord.js > https://discord.js.org
axios > https://github.com/axios/axios
Steam API > https://steamcommunity.com/dev
Sublime > www.sublimetext.com

#How
The bot works in these steps:

>Detects a message on Discord
>Verify for the command we set (In this case !64id)
>Verify that the user is allowed to use the bot
>Look for a valid steam64ID inside the message (Some people already have the id on the profile url)

>If found we can already get what we want. If not it uses the message as a search query to find the ID.
We have to requests to the Steam API.

First case is that we already have a Steam64ID, so we can get the data from this link:
https://api.steampowered.com/ISteamUser/GetPlayerSummaries/v2/?key=YOURSTEAMAPIKEY&steamids=STEAM64ID

Second case we got a possible username, so we use another link:
http://api.steampowered.com/ISteamUser/ResolveVanityURL/v0001/?key=YOURSTEAMAPIKEY&vanityurl=USERNAMETOLOOK

>--------------------------

>Check for the profile privacy status

If Public we will get:
Steam64ID
Real name
Nickname
Profile pic
Country
Date/time created

If private, we only get:
Steam64ID
Nickname
Profile pic

>Even public profiles may not have some info, so we check and replace some fields with "Not Found" if that's the case

>We make a embed for the bot to reply on the same channel

>---------------------------------------------------------------------------------------------------------

#Notes

>The data/time field from Steam is on Unix format, like this > 1378747359
So I had to convert the date, then to a string and finally cut it down to get this > Tue Oct 11 2005 13:07:48

>This bot was created for admins/moderators, if you use it right there's only 2 scenarios for the error function to be called
The ID provided is wrong or the Username provided wasn't found. (Assuming Steam API is working of course)

>---------------------------------------------------------------------------------------------------------

Thanks for checking this out, and feel free to improve this bot =D

>---------------------------------------------------------------------------------------------------------
