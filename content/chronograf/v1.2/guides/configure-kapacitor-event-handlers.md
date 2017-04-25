---
title: Configure Kapacitor Event Handlers
menu:
  chronograf_1_2:
    weight: 20
    parent: Guides
---

Chronograf works with [Kapacitor](/kapacitor/v1.2/) to send alert messages to supported event handlers.
Use Chronograf to send alert messages to specific URLs as well as to applications like [Slack](https://slack.com/) and [HipChat](https://www.hipchat.com/).

This guide offers step-by-step instructions for setting up event handlers in Chronograf.
Currently, the guide doesn't cover every supported event handler, but we will continue to add content to this page over time.
See the FAQ page for a complete list of the supported [event handlers](/chronograf/v1.2/troubleshooting/frequently-asked-questions/#what-kapacitor-event-handlers-are-supported-in-chronograf).

### Content

* [Locate Event Handler Configurations](#locate-event-handler-configurations)
* [HipChat](#hipchat)
* [Slack](#slack)
* [Telegram](#telegram)

## Locate Event Handler Configurations

The event handler configurations appear on Chronograf's Configure Kapacitor page.
You must have a connected Kapacitor instance to access the configurations.
See the Getting Started guide for [Kapacitor installation instructions](/chronograf/v1.2/introduction/getting-started/#kapacitor-setup) and how to [connect a Kapacitor instance](/chronograf/v1.2/introduction/getting-started/#4-connect-chronograf-to-kapacitor) to Chronograf.

Note that the configuration options in the `Configure Alert Endpoints` section are not all-inclusive.
Some event handlers allow users to customize event handler configurations per [alert rule](/chronograf/v1.2/guides/create-a-kapacitor-alert/).
For example, Chronograf's Slack integration allows users to specify a default channel in the `Configure Alert Endpoints` section and a different channel for individual alert rules.

## HipChat

[HipChat](https://www.hipchat.com/) is Atlassian's web service for group chat, video chat, and screen
sharing.
Configure Chronograf to send alert messages to a HipChat room.
The sections below describe each configuration option.

![HipChat configuration](/img/chronograf/v1.2/g-eventhandlers-hipchat.png)

### Subdomain

The HipChat subdomain name.
Identify the subdomain in your HipChat URL;
for example, the subdomain in the Hipchat URL `https://example-hi.hipchat.com/home` is `example-hi`.

### Room

The HipChat room name.
Chronograf sends alert messages to this room.

### Token

A HipChat API access token for sending notifications.
The following steps describe how to create the API access token:

**1.** From the HipChat home page (`https://<your-subdomain>.hipchat.com/home`), access `Account settings` by clicking on the
person icon in the top right corner.

**2.** Select `API access` from the items in the left menu sidebar.

**3.** Under `Create new token`, enter a label for your token (it can be anything).

**4.** Under `Create new token`, select `Send Notification` as the Scope.

**5.** Click `Create`.

Your token appears in the table just above the `Create new token` section:

![HipChat token](/img/chronograf/v1.2/g-eventhandlers-hipchattoken.png)

## Slack

[Slack](https://slack.com/) is a messaging app for teams.
Configure Chronograf to send alerts to an existing Slack channel or as a [direct message (DM)](https://get.slack.help/hc/en-us/articles/201925108-About-channels-and-direct-messages).
The sections below describe each configuration option.

![Slack configuration](/img/chronograf/v1.2/g-eventhandlers-slack.png)

### Slack WebHook URL

The Slack WebHook URL allows you to post messages from Chronograf to Slack.
The following steps describe how to create a Slack WebHook URL:

**1.** Visit https://api.slack.com/incoming-webhooks

**2.** Click the link at `incoming webhook integration`

**3.** Select a channel or DM in the `Post to Channel` section

This step is necessary for creating the WebHook; note that you can configure Chronograf to send messages to a different Slack channel or DM later.

**4.** Click `Add Incoming WebHooks integration`

Your Slack WebHook URL appears next to `Webhook URL`:

![Slack WebHook](/img/chronograf/v1.2/g-eventhandlers-slackwebhook.png)

### Slack Channel

Chronograf sends alert messages to this channel or DM by default.
The channel or DM must already exist in Slack.
Prefix a channel with `#` and a DM with `@`; for example, `#chronocats` is a channel and `@chronothan` is a DM.

If you do not specify a channel or DM, Chronograf sends alert messages to the channel or DM that you selected for the WebHook URL or to the channel or DM specified in the [alert rule](/chronograf/v1.2/guides/create-a-kapacitor-alert/).
The channel or DM specified in the alert rule takes precedence over both the `Slack Channel` configuration option and the WebHook URL configuration.

## Telegram

[Telegram](https://telegram.org/) is a messaging app.
Configure Chronograf to send alert messages to an existing Telegram bot.
The sections below describe each configuration option.

![Telegram configuration](/img/chronograf/v1.2/g-eventhandlers-telegram.png)

### Telegram Bot

Chronograf sends alerts to an existing Telegram bot.
The following steps describe how to create a new Telegram bot:

**1.** Search for the `@BotFather` username in your Telegram application

**2.** Click `Start` to begin a conversation with `@BotFather`

**3.** Send `/newbot` to `@BotFather`

`@BotFather` responds:

    Alright, a new bot. How are we going to call it? Please choose a name for your bot.

`@BotFather` will prompt you through the rest of the bot-creation process; feel
free to follow his directions or continue with our version of the steps below.
Both setups result in success!

**4.** Send your bot's name to `@BotFather`

Your bot's name can be anything.
Note that this is not your bot's Telegram `@username`; you'll create the username
in step 5.

`@BotFather` responds:

    Good. Now let's choose a username for your bot. It must end in `bot`. Like this, for example: TetrisBot or tetris_bot.

**5.** Send your bot's username to `@BotFather`

Your bot's username must end in `bot`.
For example: `mushroomKap_bot`.

`BotFather` responds:

    Done! Congratulations on your new bot. You will find it at t.me/<bot-username>. You can now add a description, about section and profile picture for your bot, see /help for a list of commands. By the way, when you've finished creating your cool bot, ping our Bot Support if you want a better username for it. Just make sure the bot is fully operational before you do this.

    Use this token to access the HTTP API:
    <API-access-token>

    For a description of the Bot API, see this page: https://core.telegram.org/bots/api

**6.** Begin a conversation with your bot

Click on the `t.me/<bot-username>` link in `@BotFather`'s response
and click `Start` at the bottom of your Telegram application.

Your newly-created bot will appear in the chat list on the left side of the application.

### Token

The Telegram API access token.
The following section describes how to identify or create the API access token.

Telegram's `@BotFather` bot sent you an API access token when you created your bot.
See the `@BotFather` response in step 5 of the previous section for where to find your token.

If you can't find the API access token, create a new token with the steps
below:

**1.** Send `/token` to `@BotFather`

**2.** Select the relevant bot at the bottom of your Telegram application

`@BotFather` responds with a new API access token:

    You can use this token to access HTTP API:
    <API-access-token>

    For a description of the Bot API, see this page: https://core.telegram.org/bots/api

### Chat ID

The Telegram chat id.
The following steps describe how to identify your chat id:

**1.** Paste the following link in your browser
Replace `<API-access-token>` with the API access token that you identified or created in the previous section:

    https://api.telegram.org/bot<API-access-token>/getUpdates?offset=0

**2.** Send a message to your bot

Send a message to your bot in the Telegram application.
The message text can be anything; your chat history must include at least one message to get your chat id.

**3.** Refresh your browser

**4.** Identify the chat id

Identify the numerical chat id in the browser.
In the example below, the chat id is `123456789`.

    {"ok":true,"result":[{"update_id":XXXXXXXXX,
    "message":{"message_id":2,"from":{"id":123456789,"first_name":"Mushroom","last_name":"Kap"},"chat":{"id":123456789,"first_name":"Mushroom","last_name":"Kap","type":"private"},"date":1487183963,"text":"hi"}}]}

### Select the Alert Message Format

Select `Markdown` or `HTML` for markdown-formatted or HTML-formatted alert messages.
The default message format is `Markdown`.

### Disable Link Previews

Select this option to disable [link previews](https://telegram.org/blog/link-preview) in alert messages.

### Disable Notifications

Select this option to disable notifications on iOS Devices and sounds on Android devices.
Android users will continue to receive notifications.