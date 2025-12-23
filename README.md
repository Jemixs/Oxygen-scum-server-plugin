# Hello SCUM Server Owners and Players!

I am currently developing **Oxygen** — a new **server-side plugin** designed to change the game.

At the moment, SCUM lacks a proper **RCON protocol**, forcing admins to rely on external bots that simulate a game client and emulate key presses. This approach is slow, unstable, and inefficient.

**Oxygen** works **directly inside the server process**, providing:

- Zero latency  
- No running game client required  
- No extra Steam account needed  
- Access to internal server data previously unavailable  

---

## C# Scripting API (The Game Changer)

Oxygen turns your server into a **true sandbox**.  
You can write your own plugins using **C# (.NET 8.0)**.

### Features
- Create custom commands (e.g. `/kit start`)
- Handle game events:
  - `OnPlayerLogin`
  - `OnDeath`
  - `OnChat`
  - and many more
- Hot-reload scripts **without restarting the server**

---

## Example 1 — Simple Welcome Script

```csharp
using System;
using System.Collections.Generic;
using Oxygen.csharp.API;

namespace Oxygen.Plugins
{
    [Info("testPlug", "jemixs", "0.1")]
    [Description("Test plugin showing the new architecture")]
    public class MyFirstPlugin : OxygenPlugin 
    {
        // This hook fires when a player finishes connecting
        public override void OnPlayerConnecting(PlayerBase player)
        {
            ReplyPlayer(player, $"Welcome player {playerId.nickname}!");
        }
    }
}
```

## Example 2:
Custom Commands (Starter Kit) Implementation of a custom /kit start command for issuing gear.

```csharp
using System;
using System.Collections.Generic;
using Oxygen.csharp.API;


namespace Oxygen.Plugins
{
    [Info("testPlug", "jemixs", "0.1")]
    [Description("Test plugin showing kits and chat commands")]
    public class MyFirstPlugin : OxygenPlugin 
    {
        [Command("kit")] // prefix /kit or !kit
        [Permission("*")] // all players can use this command
        private void KitCommand(PlayerBase player, string[] args){
            ProcessCommand(player, "SpawnItem Weapon_M9");
            ReplyPlayer(player, "u receive gun");
        }
    }
}
```

## Web Panel Functionality

All server management is performed through a **unified web interface** with **real-time data access**.

### Servers Tab
- Central control console
- Monitor server status
- Execute any console commands directly, bypassing standard input limitations
![](https://media.discordapp.net/attachments/1452785146964082763/1452802812621623412/image.png?ex=694b238e&is=6949d20e&hm=266a00e3b5c107bac9377f255d2581b9e9795f8e50b33fe92f589b173e072469&=&format=webp&quality=lossless&width=2512&height=477)

### Players Tab
- Advanced online monitoring
- **Full statistics:**
  - SteamID
  - Ping
  - IP address
- **Live Loadout** — view the equipment currently worn by the player in real time
- **Management tools:**
  - Ban
  - Kick
  - Teleport
  ![](https://cdn.discordapp.com/attachments/1452785146964082763/1452803066238599188/image.png?ex=694b23ca&is=6949d24a&hm=465f3ad83d406a7795679e6b114a99f07204849c3e4c03cac2380e2c8abab1f0&)
- **Spawn Menu** — spawn items directly to a specific player
![](https://cdn.discordapp.com/attachments/1452785146964082763/1452803442975440916/image.png?ex=694b2424&is=6949d2a4&hm=e0430d32c08f8b05c11ee26462451578ac90d185c10d01eaee882d7767c2e5d1&)

### Squads Tab
- Social group management
- Full list of squads on the server
- Displays squad leaders and current members
![](https://cdn.discordapp.com/attachments/1452785146964082763/1452803824841396224/image.png?ex=694b247f&is=6949d2ff&hm=8d9ef69e10635a9c3e5485da0cca2d0676317bdde45a676c458341eeb89fc5ee&)

### Chat Tab
- Read all chat channels without latency:
  - Global
  - Local
  - Squad
  - Admin
- Message filtering
- Send announcements as **Server**
![](https://cdn.discordapp.com/attachments/1452785146964082763/1452804298869178574/image.png?ex=694b24f0&is=6949d370&hm=b128f4e2f867568e237e2fc8b800b6626b1d1ff1e5079a8d6bf7ed0563dd4908&)

### Plugins Tab
- Extension management center
- View active scripts
- Core update status

### Downloads Tab
- Product update center
- Latest **stable Oxygen core** always available for download
![](https://cdn.discordapp.com/attachments/1452785146964082763/1452804959518199828/2025-12-23_012630.png?ex=694b258e&is=6949d40e&hm=9b6f9378e17d1b112a946a19fd82943d3b50df6bbb2bd13e558274500ecc591c&)
---

## Project Status

- Primary target: **Dedicated Servers (VDS / DS)**
- Slot hosting support may be added in the future, depending on provider restrictions

**[JOIN OUR DISCORD](https://discord.gg/7h2TD8mMKM)**
