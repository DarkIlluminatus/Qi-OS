# These are the original readme files. They'll remain like this until I have time to finish working on the code.  **
** TODO: Refine config prompt if needed.  ** 
**       Locate API URL and change it to a BLOOM API (and maybe program in a swapping code for it to ease end-user experiences)  **
**       Comment ALL Code thoroughly so people know what they're looking at, we want to make this as easy to implement as possible.  **
**       Deploy and test.   **
**       Rinse and repeat.  **


# If you believe there is something you can accomplish from those above tasks, or have any other ideas feel free to offer a suggestion for implementation of the aforementioned TODOs or the following Feature list

# The Qi OS is a Natural Language Model Operating System that has the ability to program itself for any text based OS function (and possibly more, depending on how much ability we add in during this alpha coding phase)

# Features: 
# Fully Interactive user experience, user can create commands and files of any type with good enough documentation in the LLM used for the training data.
# NLP Chat based operations
# Fully customizable - (depending on where it is deployed, accessed, and the capabilities of the access point, on Discord for example, it is fully customizable within the natural limitations of Discord message boards and bot functions.
# Scaleable - You will be able to scale up performance as you and the OS come up with your own compression, encryption and storage methods.  We'll be working on NLP Prompt based plugins on this repository that you can use to "upgrade" your OS more easily.
# The only limitations are your combined imaginations, that is, yours and your OS. You OS can come up with ideas and implement them on it's virtual system.

# Additional Features suggested by the OS itself.

# - Natural language processing and machine learning capabilities
# - Automated responses to user input
# - Ability to detect user intent and provide relevant responses
# - Voice recognition and synthesis capabilities
# - Ability to integrate with other APIs to access external data
# - Ability to detect and respond to user sentiment
# - Automated scheduling and task management
# - Ability to create and run scripts
# - Ability to interact with cloud services and the internet
# - Ability to integrate with other devices and services
# - Ability to access and analyze data from external sources
# - Ability to monitor system performance and detect anomalies
# - Security and privacy features to protect user data

# Now, if you wanna do some alpha testing, all you have to do to deploy this is enter this information into a prompt to an AI Chat interface and suggest that this is what it is.
# It may ask some questions. Further define what you mean and help it find virtual methods to accomplish the goals, such as when it produces output of challenges to overcome say something like "Great! You're already writing your own documentation!" It will usually at this point be even more motivated to help, even if it isn't sure what it is supposed to be doing, once it associates what it wrote as it's documentation it will assume the feature is implemented and act accordingly.  Yes it's virtual, but it's also procedurally generated, which saves on token usage and helps with it's ram and disk space.
# Sometimes, all you'll need (provided you have enough tokens on your API) is this document alone, however for security and privacy I highly recommend that you compile from source after inspecting each file manually.




# All that is below here may work, but may not.  This will be modified from it's original version and these texts are from that original version and are being left here simply for historical archiving purposes. So we may always remember how this all began.


# Please read!


**For any problems running this specific bot:** [Discord Project Post](https://discord.com/channels/974519864045756446/1055336272543092757)

**For general OpenAI API problems or questions:** [Discord API Discussions](https://discord.com/channels/974519864045756446/1037561178286739466)

**For bugs in the template code:** create an Issue

**For feature requests:** this repo is not accepting feature requests, you can discuss potential features in [Discord Project Post](https://discord.com/channels/974519864045756446/1055336272543092757)

**For PRs:** only bug fix PRs wil be accepted. If you are implementing a new feature, please fork this repo.

Thank you!

---
# GPT Discord Bot

Example Discord bot written in Python that uses the [completions API](https://beta.openai.com/docs/api-reference/completions) to have conversations with the `text-davinci-003` model, and the [moderations API](https://beta.openai.com/docs/api-reference/moderations) to filter the messages.

**THIS IS NOT CHATGPT.**

This bot uses the [OpenAI Python Library](https://github.com/openai/openai-python) and [discord.py](https://discordpy.readthedocs.io/).


# Features

- `/chat` starts a public thread, with a `message` argument which is the first user message passed to the bot
- The model will generate a reply for every user message in any threads started with `/chat`
- The entire thread will be passed to the model for each request, so the model will remember previous messages in the thread
- when the context limit is reached, or a max message count is reached in the thread, bot will close the thread
- you can customize the bot instructions by modifying `config.yaml`
- you can change the model, the hardcoded value is `text-davinci-003`

# Setup

1. Copy `.env.example` to `.env` and start filling in the values as detailed below
1. Go to https://beta.openai.com/account/api-keys, create a new API key, and fill in `OPENAI_API_KEY`
1. Create your own Discord application at https://discord.com/developers/applications
1. Go to the Bot tab and click "Add Bot"
    - Click "Reset Token" and fill in `DISCORD_BOT_TOKEN`
    - Disable "Public Bot" unless you want your bot to be visible to everyone
    - Enable "Message Content Intent" under "Privileged Gateway Intents"
1. Go to the OAuth2 tab, copy your "Client ID", and fill in `DISCORD_CLIENT_ID`
1. Copy the ID the server you want to allow your bot to be used in by right clicking the server icon and clicking "Copy ID". Fill in `ALLOWED_SERVER_IDS`. If you want to allow multiple servers, separate the IDs by "," like `server_id_1,server_id_2`
1. Install dependencies and run the bot
    ```
    pip install -r requirements.txt
    python -m src.main
    ```
    You should see an invite URL in the console. Copy and paste it into your browser to add the bot to your server.
    Note: make sure you are using Python 3.9+ (check with python --version)

# Optional configuration

1. If you want moderation messages, create and copy the channel id for each server that you want the moderation messages to send to in `SERVER_TO_MODERATION_CHANNEL`. This should be of the format: `server_id:channel_id,server_id_2:channel_id_2`
1. If you want to change the personality of the bot, go to `src/config.yaml` and edit the instructions
1. If you want to change the moderation settings for which messages get flagged or blocked, edit the values in `src/constants.py`. A lower value means less chance of it triggering.

# FAQ

> Why isn't my bot responding to commands?

Ensure that the channels your bots have access to allow the bot to have these permissions.
- Send Messages
- Send Messages in Threads
- Create Public Threads
- Manage Messages (only for moderation to delete blocked messages)
- Manage Threads
- Read Message History
- Use Application Commands
