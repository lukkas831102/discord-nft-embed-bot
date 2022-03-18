# discord-nft-bot

A [discord.js](https://discord.js.org/) bot that listens to messages in channels and replies with items from an nft collection.

Originally developed for [@dutchtide](https://twitter.com/dutchtide)'s [𝕄𝕚𝕕𝕟𝕚𝕘𝕙𝕥 夏季 𝔹𝕣𝕖𝕖𝕫𝕖](https://opensea.io/collection/midnightbreeze) collection.

An OpenSea API key is needed - [request one here](https://docs.opensea.io/reference/request-an-api-key).

To run multiple instances of this bot at once check out [bot-runner](https://github.com/ryanio/bot-runner). Also check out [opensea-activity-bot](https://github.com/ryanio/opensea-activity-bot).

## Supported syntax

- `#1234`
- `#ensname.eth`
- `#openseaUsername`
- `#random` or `#rand` or `#?`

Example reply:

![Example bot reply](./example.png)

Example console output:

```
------------------------------------------------------------
Logged in as Dutchtide Listen Bot#8486!
Listening for messages...
------------------------------------------------------------
Message from ryanio in #🌴🎐view-the-breeze🎐🌴:
> #random
Fetching #2248...
Replied with #2248
------------------------------------------------------------
```

Provided metadata fields:

- Owner
- Last sale
- Listed for
- Highest offer

You can add specific properties of the nft by formatting `asset.traits` and adding to the `fields` array.

## Setup

### Env

Please define the following env variables for the repository to work as intended.

#### APIs

- `DISCORD_TOKEN`
- `OPENSEA_API_TOKEN`
- `INFURA_PROJECT_ID`

#### Project-specific

- `TOKEN_NAME`
- `TOKEN_ADDRESS`
- `MIN_TOKEN_ID`
- `MAX_TOKEN_ID`

### Bot

To get your `DISCORD_TOKEN`, [create a Discord app](https://discord.com/developers/applications). Create a bot with the permissions: `Read Messages/View Channels`, `Send Messages`, and `Embed Links`. Then [add your bot to your server](https://discordjs.guide/preparations/adding-your-bot-to-servers.html#bot-invite-links). The bot will listen and reply to messages in all of the channels it has access to.

The `DISCORD_TOKEN` looks like this: `OTE5MzY5ODIyNzEyNzc5NzUz.YBuz2g.x1rGh4zx_XlSNj43oreukvlwsfw`

If your discord bot is not able to post messages ensure it is added to the channels you've specified and it has the permissions to `Read Messages/View Channels`, `Send Messages` and `Embed Links`, and that you have also enabled `Message Content Intent` on your bot page.

### Run

`yarn start`

#### Running on a server

It is recommended to use a DigitalOcean Droplet over Heroku for improved stability.

Support this repository by using the referral badge below:

[![DigitalOcean Referral Badge](https://web-platforms.sfo2.cdn.digitaloceanspaces.com/WWW/Badge%201.svg)](https://www.digitalocean.com/?refcode=3f8c76216510&utm_campaign=Referral_Invite&utm_medium=Referral_Program&utm_source=badge)

##### Heroku

A `Procfile` is included for easy use.

Clone this repo, push it to heroku, set up the environment variables above, and spin up a worker with `heroku ps:scale web=0 worker=1`

Then watch the logs with `heroku logs --tail`
