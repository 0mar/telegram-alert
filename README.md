# Teledove

Telegram-based nofitication system from your computer to your phone.

## Use case

Do you have a sensitive system that needs your attention as soon as something goes wrong?
Have a long running process of which you want to do stuff with as soon as your finished?
Want to forward system information to your phone?

Teledove might help you out. It is a simple, minimal command line tool that uses a personal bot to notify you of anything.

## Requirements

The script is written to make use of minimal dependencies. It relies on

 - `bash`
 - `curl`
 - `grep`

all of which should be present on standard Mac/Linux systems, but can otherwise be installed with `brew`/any package manager.

The script also requires a Telegram bot to notify you with. Setting one up is easy and can be done through Telegram itself with the [BotFather](https://telegram.me/botfather) wizard.

## Setup

1. If you haven't already, download [Telegram](https://telegram.org/) on your (mobile) device.
2. [Setup](https://telegram.me/botfather) a Telegram bot.
3. Start a conversation with your new Telegram bot.
4. Clone this repository/copy the file `alert` and put it somewhere in your PATH (like in `~/.local/.bin`)

## Usage

 - `alert` sends a default message
 - `alert custom message` sends `custom message` to the chat

The first time you run alert, it asks for a token. You can find this token in your conversation with the BotFather. It looks like `123456:ABC-DEF1234ghIkl-zyx57W2v1u123ew11` and if you supply it to the script, it will be stored in the file `~/.telegram_token` for future use.

Keep the token private, it acts like a password to your bot.

After obtaining the token, it will fetch the chat ID of the conversation you started with the bot.
Upon success, this ID will be stored in `~/.telegram_chat_id`. If you have not conversed with the bot, it will not be able to find this chat ID.

If something weird happens, deleting/modifying these files manually might help.

## Caveat

No information is stored/transmitted through any other third parties than your own and the Telegram servers. You can examine the script to convince yourself of this.

However, even though communication through between you and a Bot is private and encrypted (as long as you keep you token private), the bots themselves are public.
This means that each time a chat ID is set automatically, it is recommendable to send yourself an alert to convince yourself it is going to the right chat.
Alternatively, you can hardcode/preset the chat ID in `~/.telegram_chat_id`.

## Bugs

Please let me know if you find any bugs.
