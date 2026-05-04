# OpenClaw Channels

Channels are how OpenClaw communicates with you. Each channel connects to a chat service (Discord, Telegram, WhatsApp, etc.) via the Gateway.

## What Channels Are

Channels connect OpenClaw to your preferred chat apps. When you message on any channel, the Gateway routes it to your AI agent and sends responses back through the same channel.

## Supported Channels

### Bundled Plugins (included)

| Channel | Description |
|---------|-------------|
| Discord | Discord Bot API + Gateway; servers, channels, DMs |
| Telegram | Bot API via grammY; supports groups |
| Slack | Bolt SDK; workspace apps |
| Signal | signal-cli; privacy-focused |
| WhatsApp | Baileys; requires QR pairing |
| Microsoft Teams | Bot Framework; enterprise support |
| iMessage (BlueBubbles) | Recommended for iMessage via BlueBubbles macOS server |
| IRC | Classic IRC servers |
| Matrix | Matrix protocol |
| Mattermost | Bot API + WebSocket |
| Nostr | Decentralized DMs via NIP-04 |
| Feishu | Feishu/Lark bot via WebSocket |
| QQ Bot | QQ Bot API |
| Nextcloud Talk | Self-hosted chat |
| Synology Chat | Synology NAS Chat |
| Twitch | Twitch chat via IRC |
| Tlon | Urbit-based messenger |
| Zalo | Vietnam's popular messenger |
| Zalo Personal | Zalo personal account via QR |

### External Plugins (install separately)

| Channel | Description |
|---------|-------------|
| Google Chat | Google Chat API app via HTTP webhook |
| LINE | LINE Messaging API bot |
| WeChat | Tencent iLink Bot via QR login |
| Voice Call | Telephony via Plivo or Twilio |
| WebChat | Gateway WebChat UI over WebSocket |

## Channel Setup

### During Onboarding

```bash
openclaw onboard
```

Onboarding walks you through channel setup.

### Add Channel Later

```bash
openclaw channels add telegram
openclaw channels add discord
```

### Check Channel Status

```bash
openclaw channels status
openclaw channels status --probe
```

## Channel Commands

```bash
openclaw channels list           # List configured channels
openclaw channels status        # Show channel status
openclaw channels add <channel>  # Add a channel
openclaw channels remove <channel> # Remove a channel
```

## Fastest Setup: Telegram

Telegram is the fastest channel to set up—just a bot token:

1. Create a bot via @BotFather on Telegram
2. Get the bot token
3. Configure during onboarding or with `openclaw configure --section channels`

## WhatsApp Setup

WhatsApp requires QR pairing and stores more state:
- Uses Baileys library
- Setup shown during onboarding
- Gateway loads WhatsApp runtime only when channel is active

## Group Chats

Group behavior varies by channel:
- Discord: Full server and channel support
- Telegram: Supports groups
- Slack: MPIM conversations route as group chats
- See [Groups](/channels/groups) for details

## Security: DM Pairing

DM pairing and allowlists are enforced for safety:
- Only paired/allowed users can DM the agent
- Configure during onboarding or see [Security](/gateway/security)
- Telegram and WhatsApp DMs default to allowlist

## Troubleshooting

See [Channel troubleshooting](/channels/troubleshooting) for diagnosis.

## Related

- [Overview](00-overview.md)
- [Gateway](03-gateway.md)
- [Security](09-security.md)