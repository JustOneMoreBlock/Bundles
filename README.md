
# 🧩 Initial Enabled Packs Updater

This repository contains an automated GitHub Actions workflow that tracks and updates Minecraft snapshot data — specifically which datapack bundles are enabled by default in the latest snapshot server JAR.

## 🔄 What It Does

- Runs automatically **every 15 minutes** via cron (`*/15 * * * *`)
- Retrieves the **latest Minecraft snapshot version** from Mojang
- Compares it with the current version stored in `data.json`
- If a **new snapshot** is found:
  - Downloads the corresponding Minecraft server JAR
  - Extracts the JAR to locate enabled datapack bundles
  - Updates:
    - `bundles.txt` with a comma-separated list of the enabled datapacks
    - `data.json` with full metadata about the snapshot version, server JAR URL, and bundle list

If there is **no change in snapshot version**, the workflow exits early without performing any additional steps or commits.

## 📁 Files Maintained

### `bundles.txt`
A plain-text, comma-separated list of enabled datapack bundles found in the latest snapshot.

Example:
vanilla,redstone_experiments,trade_rebalance

---

### `data.json`
A JSON file containing metadata about the last snapshot version processed by the workflow.

```json
{
  "snapshot": "25w16a",
  "server_jar": "https://piston-data.mojang.com/v1/objects/3d8223843a659d8ebc33459864ba02b34485ea11/server.jar",
  "bundles": "locator_bar,minecart_improvements,redstone_experiments,trade_rebalance,vanilla"
}
```

⚙️ Technology Stack
- GitHub Actions — CI automation
- curl — for remote data retrieval
- jq — for JSON parsing
- unzip — for server JAR extraction
- actions/github-script — for committing changes to the repository

🧠 Use Cases
- Automatically track snapshot changes from Mojang
- Discover what datapack features Mojang is testing or enabling
- Power Minecraft modding tools, dashboards, or analysis systems
- Generate changelogs or announcements for your Minecraft-focused community

🚀 Future Enhancements
- Support for release, pre-release, and experimental versions
- Create GitHub releases or tags for each snapshot
- Store version history for tracking datapack changes over time
- Integration with a front-end dashboard or Minecraft mod API

🤝 Contributing
Pull requests and suggestions are welcome! If you have ideas on improving the workflow or want to integrate other types of metadata, feel free to open an issue or fork this repository.

---

🙃 Original Credit & AI Assistance (Because Redstone is Hard)
This workflow was originally mined and crafted by hand — no AI, just pure pickaxe power.
But like every good redstone contraption, it eventually broke in mysterious and spectacular fashion.

After a few too many failed attempts to debug it (and no diamonds in sight), we rage-quit to creative mode and summoned an AI assistant.

📎 If Microsoft ever brings back Clippy, he’d probably pop up and say:
“It looks like you're trying to fix your broken Minecraft workflow. Need some help?”

Well, we did. And the AI patched things up faster than a villager fleeing a zombie raid.

So now it Just Works™ — and we’ve stashed the original code deep in a chest somewhere… probably behind a piston door that no longer functions.

![Clippy Redstone Helper](assets/clippy-minecraft.png)
