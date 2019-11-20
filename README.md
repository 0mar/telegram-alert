# Telegram-alert

Telegram-based nofitication system for the command line with minimal configuration or dependencies.

## Use case

 - Do you have a long running process that requires immediate attention when it finishes?
 - Would you like to be notified of rare events on your computer as they happen?
 - Interested in being alerted when your job on a remote machine is done running?

Telegram-alert might be able to help you out. It is a simple, minimal command line tool that uses a personal Telegram bot to notify you of anything you'd like.

## Requirements

The tool is designed to have minimal external dependencies. It requires only

 - `bash`
 - `curl` or `wget`
 - `grep`

all of which should be present on standard Mac and Linux systems, but can otherwise be installed with `brew`/any package manager.

The script also requires a Telegram bot to notify you with. Setting one up is easy and can be done through Telegram itself with the [BotFather](https://telegram.me/botfather) wizard.

## Setup

1. If you haven't already, download [Telegram](https://telegram.org/) on your (mobile) device.
2. [Setup](https://telegram.me/botfather) a Telegram bot. Pick any name you like.
3. Start a conversation with your new Telegram bot.
4. Clone this repository or download the file `alert` and put it somewhere in your PATH (like in `~/.local/.bin`).

## Usage

 - `alert` sends a default message.
 - `alert custom message` sends `custom message`.

The first time you run alert, it asks for a token. You can find this token in your conversation with the BotFather. It looks like `123456:ABC-DEF1234ghIkl-zyx57W2v1u123ew11` and if you supply it to the script, it will be stored in the file `~/.telegram_alert.conf` for future use.

Keep the token private, it acts like a password to your bot.

After obtaining the token, it will fetch the chat ID of the conversation you started with the bot.
Upon success, this ID will also be stored in `~/.telegram_alert.conf`. If you have not conversed with the bot, it will not be able to find this chat ID.

If something weird happens, deleting/modifying the configuration file might help.

## Security

No information is stored/transmitted through any other third parties than your own and the Telegram servers. You can examine the script to convince yourself of this.

However, even though communication through between you and a Bot is private and encrypted (as long as you keep you token safe), the bots themselves are public, meaning anyone can start a conversation with your bot.
For this reason, the first time after a chat ID is fetched and set, `alert` displays the username with which the connection has been established. Obviously, this will also be confirmed by your bot sending you a message.

Alternatively, you can hardcode/preset the chat ID in `~/.telegram_alert.conf`.

As long as a connection is established and the chat ID is functional, all messages to the bot will be ignored.

## Bugs

Please let me know if you find any bugs.
