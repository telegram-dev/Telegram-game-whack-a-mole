# Telegram Whack-a-mole Game Bot

[Try it on Telegram][].

This [Telegram bot][] is an example game made by combining the [Botgram Explode Game][] and
this existing [Whack-a-mole game][].

The example demostrates how to use [Botgram][]'s API for the gaming platform,
and the deployment needed for Telegram games in general.

<img src="https://i.imgur.com/r9rN5Xi.png" width="300">

There's a Telegram bot and a webserver working in unison. The webserver
needs to be reachable under some public URL so that users can open the game,
see below.

## Install

This assumes you already have a Telegram bot created, with the corresponding auth token.
First, you should create a game in your bot, by saying `/newgame` to the BotFather.
You may enter the following details when asked:

**Name:** Particle Explode  
**Description:** Try to wipe everything by starting a chain reaction  
**Photo:** send `photo.png`  
**Short game name:** explode

Note that if you supply a short game name other than `explode`, you need to modify it in `server.js` too.

The second part is the webserver: when run `server.js` creates an HTTP server
listening at port 3103. You need to somehow make this accessible from anywhere,
for example by running `server.js` on a server with a public IP, or opening that
port from your firewall...

At the end you should note the **base URL**, which in my case was `https://jmendeth.com`,
meaning that `https://jmendeth.com/telegramBot/game.html` acessed
`http://localhost:3103/telegramBot/game.html`, and so on.

Once this is setup, install dependencies as usual:

    npm install

And run the server, passing in your auth token and the base URL:

    node server <auth token> <base URL>

Then you're ready to play your game.


## Enhancements

Interesting things to implement:

 - Bot command to query the number of people playing or (global) top score.
 - Manually editing the message and calling `getGameHighScores` to build a score table.
 - Displaying the user's name and realtime (local) score table in the game itself.
 - Adding a share button in the game itself.



[Telegram bot]: https://core.telegram.org/bots
[Botgram]: https://botgram.js.org
[gaming platform]: https://core.telegram.org/bots/games
[Whack-a-mole game]: https://github.com/alekseylovchikov/whack-a-mole
[Botgram Explode Game]: https://github.com/botgram/explode-game-bot
[Try it on Telegram]: http://t.me/gamergurlbot
