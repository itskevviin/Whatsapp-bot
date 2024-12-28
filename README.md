# WhatsApp Bot

## Getting Started

### Prerequisites

Ensure you have [Docker](https://www.docker.com/) installed, as it is the only requirement.

### Build the Application

- Execute `bash build.sh` from the project's root directory.

### Launching the Bot

- Run `bash run.sh` in the project's root directory.
- For the initial setup, you will need to scan the QR code displayed in the terminal with your WhatsApp.

## Available Plugins

### Mirror

- The bot will respond to any message formatted as `!mirror!<message>` with `<message>`.
- This feature is primarily for fun and can also be used to verify if the bot is active.

### TagEveryone

- The bot will reply to any message containing the word `@all` (case insensitive) by tagging all the group members.
- To prevent spam, this feature is restricted to groups with fewer than 50 members.
- This functionality is not applicable to personal conversations.

### Roles

- Allows the creation of custom roles (similar to Discord) to tag specific groups of members.
- You can list roles, create new ones, delete roles, and add or remove members from roles.
- Send `!role help` to learn how to use these features.
  - You can use `@me` to simulate tagging yourself.
- The bot will respond to any message containing `@<role>` (case insensitive), where `<role>` is any created role, by tagging all members of that role.
- `NOTE`: Roles are shared across groups and chats, so a role can include members from multiple groups (allowing you to tag people in other groups without their knowledge).
  - Anyone who can chat with your bot can modify any role data using the role commands.
  - Consider enhancing this by creating an issue and submitting a PR :)

## Configuration

Certain bot and plugin functionalities can be modified without altering the code through `config.js`.

### Bot Configuration

- `authFolder`: Specifies the directory name (in the project root) containing:
  - Your WhatsApp authentication details (so you don’t need to scan the QR code every time).
  - Information about the last processed message. Upon restarting, the bot will process all messages after the last processed one.
  - `NOTE`: This contains private data, so DO NOT share it.

- `selfReply`: If set to `false`, the bot will not respond to its own messages.
  - If set to `true`, be cautious as it could lead to the bot sending messages in an endless loop.

- `logMessages`: If set to `true`, each message received by your bot will be logged to the console.
  - This can also help you read messages without triggering the Blue Tick ;)

### Plugin Configuration

- Mirror
  - `prefix`: Only mirror messages that start with the specified prefix.

- Tag Everyone
  - `membersLimit`: To prevent spamming, the plugin will not trigger if the group has more members than the specified limit.
  - `trigger`: The bot will tag everyone when the specified trigger keyword (@<trigger>) is mentioned.

- Roles
  - `dataFiles`: Specifies the file name (in the project root) to store all role-related data.
  - `prefix`: All role commands (except for role tagging) must start with the specified prefix.
  - `updateOnAdd`: If set to `true`, the bot will send a message (in the chat where the command is given) whenever a member is added to any role.
  - `updateOnRemove`: If set to `true`, the bot will send a message (in the chat where the command is given) whenever a member is removed from any role.


