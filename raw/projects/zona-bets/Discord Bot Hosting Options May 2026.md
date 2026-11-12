# Discord Bot Hosting Options

---

**Gemini**

Setting up your bot on Synology using Docker (Container Manager) is a solid weekend project. By following these steps, you’ll ensure the bot is stable and your photos remain isolated.

### Step 1: Create a Restricted User

Before touching Docker, create a user that has zero access to your sensitive folders.

1. Open **Control Panel** > **User & Group** > **Create**.
2. Name it something like `botuser`. Give it a strong password (though you won't use it to log in).
3. **Permissions:** Under the permissions tab, set every folder (especially `/photos`) to **No Access**.
4. **Applications:** Set everything to **Deny**.
5. Finish the wizard.

### Step 2: Find your PUID and PGID

Docker needs to know which user it is "acting" as.

1. Go to **Control Panel** > **Terminal & SNMP** and temporarily enable **SSH**.
2. Open your computer's terminal (PowerShell or Terminal.app) and type: `ssh your_admin_username@your_nas_ip`.
3. Type: `id botuser`.
4. Note the `uid` (likely 1026 or similar) and `gid` (likely 100).
5. **Turn off SSH** in the Control Panel when you're done.

### Step 3: Prepare the Folder Structure

1. Open **File Station**.
2. Inside your `docker` shared folder, create a folder named `zonabets`.
3. Inside `zonabets`, create a folder named `data`.
4. Upload your `main.py` and `requirements.txt` into the `zonabets` folder.
5. **Crucial:** Right-click the `data` folder > **Properties** > **Permission**. Ensure `botuser` has "Read & Write" access to this specific folder.

### Step 4: Create the Configuration

We will use **Docker Compose**. It’s much cleaner than the manual GUI setup.

1. Open **Container Manager** (formerly Docker).
2. Go to **Project** > **Create**.
3. **Project Name:** `zonabets-bot`.
4. **Path:** Select the `/docker/zonabets` folder.
5. **Source:** Choose "Create docker-compose.yaml" and paste the following:

YAML```
version: '3.8'
services:
  discord-bot:
    build: .
    container_name: zonabets-bot
    restart: always
    user: "${PUID}:${PGID}"
    volumes:
      - ./data:/app/data
    environment:
      - DISCORD_TOKEN=your_token_here
      - DATABASE_PATH=/app/data/zonabets.db

```

### Step 5: The Dockerfile

In the same project creation screen, or via File Station, ensure your `Dockerfile` looks like this to match your Synology paths:

Dockerfile```
FROM python:3.11-slim
WORKDIR /app
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt
COPY . .
# The /app/data folder is linked to your NAS folder in the compose file
CMD ["python", "main.py"]

```

### Step 6: Deploy and Verify

1. Click **Next** in the Container Manager wizard. It will build the image (this takes a minute).
2. Once it says "Running," go to the **Container** tab.
3. Click on `zonabets-bot` > **Log**.
4. If you see your "Bot is online" message, you’re good to go!

---

### How this protects your photos:

- **No Access:** Because you set the `botuser` to "No Access" for your photos, even if the Python script is hacked, the "user" running that script is physically blocked by the Synology OS from looking at other folders.
- **Path Restriction:** The line `./data:/app/data` in the configuration acts like a tunnel. The bot can only see inside that specific `data` folder. To the bot, the rest of your NAS hard drive literally does not exist.

Does your current `main.py` use `os.getenv` for the token, or should we update that script together first?

---
