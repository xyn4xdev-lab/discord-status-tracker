````markdown
# Discord Status & Activity Tracker Bot

## Overview

This bot tracks **all user statuses** (`online`, `idle`, `dnd`, `offline`) in your Discord server and logs **status durations**, **messages sent**, and **voice activity**.  
It also provides a `/statusstats` slash command to show total activity for a user.  

This project demonstrates:  
- Discord.js usage with **presence, message, and voice events**  
- SQLite for **persistent tracking**  
- Slash commands using **Discord API v10**  
- Logging user activity via **embeds**  

## Features

1. **Status Tracking**  
   - Tracks when a user goes `online`, `idle`, `dnd`, or `offline`.  
   - Measures how long a user stays in each status.  

2. **Message Tracking**  
   - Counts the number of messages sent by a user.  
   - Only counts messages from users already tracked in the database.  

3. **Voice Activity Tracking**  
   - Tracks total time spent in voice channels per user.  
   - Only counts time for users who are tracked.  

4. **Logging**  
   - Sends embed messages to a designated log channel for each status change.  
   - Includes previous status and duration spent.  

5. **Slash Command `/statusstats`**  
   - Shows total time spent in each status.  
   - Shows total messages sent and total voice time.  

## Installation

1. Clone the repository:
```bash
git clone https://github.com/xyn4xdev-lab/discord-status-tracker.git
cd discord-status-bot
````

2. Install dependencies:

```bash
npm install discord.js sqlite3
```

3. Set up your environment:

* Replace `token` with your bot token.
* Replace `LOG_CHANNEL_ID` with the channel ID where status changes will be logged.
* Replace `CLIENT_ID` with your bot’s application ID.

4. Start the bot:

```bash
node index.js
```

## Usage

* The bot will automatically start tracking all server members on startup.
* Status changes, messages, and voice activity will be logged.
* Use the slash command:

```
/statusstats [target]
```

to see a user’s total activity. If no user is specified, it defaults to yourself.

## Database

* Uses **SQLite** for persistence (`status.db`).

* Stores per-user data:

  * `onlineSeconds`, `idleSeconds`, `dndSeconds`, `offlineSeconds`
  * `messages`
  * `voiceSeconds`

* On bot startup, all members are initialized to ensure accurate tracking.

## Contributing

Feel free to fork and improve the bot:

* Add per-guild tracking
* Add more detailed analytics per status
* Improve logging formatting

## License

This project is open source and available under the [Creative Commons Attribution-NonCommercial 4.0 International License](./LICENSE).
