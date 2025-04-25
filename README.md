<div align="center">
  <img src="assets/github.png" alt="WebHive Logo" width="800">
</div>
<br>
<br/>


[![Discord](https://img.shields.io/badge/Discord-WebHiveOS-blue)](https://discord.com/invite/7kqEFAZc)
[![Documentation](https://img.shields.io/badge/Documentation-📕-blue)](https://webhiveos.xyz/docs)
[![WebHiveOS](https://img.shields.io/twitter/follow/WebHiveOS?style=social)](https://x.com/WebHiveOS)

> **Enhanced Version:** WebHive improves the original browser-use/web-ui project with new features while keeping compatibility. We thank the original creators for their great work.

**WebHive** is a smart browser control center using AI. It works with:
- All major AI models (Google, OpenAI, Anthropic, etc.)
- Your existing browser profiles
- Both simple and advanced tasks

**AI Model Support:** Works with popular AI services

**Use Your Own Browser:** Keep your logins and settings. Works with Chrome/Firefox/Edge. Records HD videos of AI actions.

**Keep Browser Open:** Choose to maintain the browser window between tasks to see full history.

https://github.com/user-attachments/assets/9a9eebfb-02bd-4463-97b2-73c8dec94206

**Coming Soon:**
- 🛒 **Hive Marketplace**: Buy/sell browser automation scripts using $HIVE tokens
- 🤖 **Advanced Automation**: Multi-step workflows (e.g. multi job applications, data collection, automated LinkedIN networking)
- 🔗 **Agent Networks**: Connect with other AI agents for complex tasks
- 🎁 **Early Access**: $HIVE holders get first access to new features

> 💡 **$HIVE Token Utility**:
> - Purchase premium automations
> - Earn by selling your scripts
> - Get voting rights for feature development
> - Stake for passive income
<br>

<img src="https://github.com/user-attachments/assets/8abe3ed3-5b48-4b39-b208-8afcdf3aabaf" width="80%">

<br>

## Installation Guide

### Local Installation

#### 1. Get the Code
```bash
git clone git@github.com:webhiveos/WebHive.git
cd WebHive
```

#### 2. Setup Python
We recommend using [uv](https://docs.astral.sh/uv/) for managing the Python environment.

Using uv (recommended):
```bash
uv venv --python 3.11
```

Activate the virtual environment:
- Windows (Command Prompt):
```cmd
.venv\Scripts\activate
```
- Windows (PowerShell):
```powershell
.\.venv\Scripts\Activate.ps1
```
- macOS/Linux:
```bash
source .venv/bin/activate
```

#### 3. Install Requirements
Install Python packages:
```bash
uv pip install -r requirements.txt
```

Install Playwright:
```bash
playwright install
```

#### 4. Configure Environment
1. Create a copy of the example environment file:
- Windows (Command Prompt):
```bash
copy .env.example .env
```
- macOS/Linux/Windows (PowerShell):
```bash
cp .env.example .env
```
2. Open `.env` in your preferred text editor and add your API keys and other settings

### Docker Installation

#### Prerequisites
- Docker and Docker Compose installed
  - [Docker Desktop](https://www.docker.com/products/docker-desktop/) (For Windows/macOS)
  - [Docker Engine](https://docs.docker.com/engine/install/) and [Docker Compose](https://docs.docker.com/compose/install/) (For Linux)

#### Installation Steps
1. Clone the repository:
```bash
git clone git@github.com:webhiveos/WebHive.git
cd WebHive
```

2. Create and configure environment file:
- Windows (Command Prompt):
```bash
copy .env.example .env
```
- macOS/Linux/Windows (PowerShell):
```bash
cp .env.example .env
```
Edit `.env` with your preferred text editor and add your API keys

feature/arm64-support
4. **Access the Application:**
   - Web Hive Interface: `http://localhost:7788`
   - VNC Viewer (to see browser interactions): `http://localhost:6080/vnc.html`
   - Direct VNC access is available on port 5901 (especially useful for Mac users)
   
   Default VNC password is "vncpassword". You can change it by setting the `VNC_PASSWORD` environment variable in your `.env` file.

3. Run with Docker:
```bash
# Build and start the container with default settings (browser closes after AI tasks)
docker compose up --build
```
```bash
# Or run with persistent browser (browser stays open between AI tasks)
CHROME_PERSISTENT_SESSION=true docker compose up --build
```


4. Access the Application:
- Web Interface: Open `http://localhost:7788` in your browser
- VNC Viewer (for watching browser interactions): Open `http://localhost:6080/vnc.html`
  - Default VNC password: "youvncpassword"
  - Can be changed by setting `VNC_PASSWORD` in your `.env` file
<br>

<img src="https://github.com/user-attachments/assets/b24e3ae8-b7a7-4175-b601-5a0303cd3497" width="80%">

## Usage

### Local Setup
1.  Copy `.env.example` to `.env` and set your environment variables, including API keys for the LLM. `cp .env.example .env`
2.  **Run Web Hive:**
    After completing the installation steps above, start the application:
    ```bash
    python webhive.py --ip 127.0.0.1 --port 7788
    ```
4. Web Hive options:
- `--ip`: Specifies the IP address for binding Web Hive. The default value is `127.0.0.1`.  
- `--port`: Defines the port Web Hive should use. Defaults to `7788`.  
- `--theme`: Sets the user interface theme. The default is `Ocean`.  
  - **Default**: A well-balanced theme with a standard design.  
  - **Soft**: A muted, gentle color palette for a more relaxed viewing experience.  
  - **Monochrome**: A grayscale theme that minimizes color for a clean and focused look.  
  - **Glass**: A sleek, semi-transparent design for a modern aesthetic.  
  - **Origin**: A retro-inspired theme that evokes nostalgia.  
  - **Citrus**: A bright and refreshing palette with citrus-inspired tones.  
  - **Ocean** *(default)*: A calming theme with ocean-inspired shades of blue.  
- `--dark-mode`: Activates dark mode for the user interface.  
3.  **Access Web Hive Interface:** Open your web browser and navigate to `http://127.0.0.1:7788`.
4.  **Using Your Own Browser(Optional):**
    - Set `CHROME_PATH` to the executable path of your browser and `CHROME_USER_DATA` to the user data directory of your browser.
      - Windows
        ```env
         CHROME_PATH="C:\Program Files\Google\Chrome\Application\chrome.exe"
         CHROME_USER_DATA="C:\Users\YourUsername\AppData\Local\Google\Chrome\User Data"
        ```
        > Note: Replace `YourUsername` with your actual Windows username for Windows systems.
      - Mac
        ```env
         CHROME_PATH="/Applications/Google Chrome.app/Contents/MacOS/Google Chrome"
         CHROME_USER_DATA="~/Library/Application Support/Google/Chrome/Profile 1"
        ```
    - Close all Chrome windows
    - Open Web Hive in a non-Chrome browser, such as Firefox or Edge. This is important because the persistent browser context will use the Chrome data when running the agent.
    - Check the "Use Own Browser" option within the Browser Settings.
5. **Keep Browser Open(Optional):**
    - Set `CHROME_PERSISTENT_SESSION=true` in the `.env` file.

### Docker Setup
1. **Environment Variables:**
   - All configuration is done through the `.env` file
   - Available environment variables:
     ```
     # LLM API Keys
     OPENAI_API_KEY=your_key_here
     ANTHROPIC_API_KEY=your_key_here
     GOOGLE_API_KEY=your_key_here

     # Browser Settings
     CHROME_PERSISTENT_SESSION=true  #Keeps the browser open between AI tasks if set to true.
     RESOLUTION=1920x1080x24         # Defines resolution in WIDTHxHEIGHTxDEPTH format.
     RESOLUTION_WIDTH=1920           # Sets the screen width in pixels.
     RESOLUTION_HEIGHT=1080          # Sets the screen height in pixels.

     # VNC Settings
     VNC_PASSWORD=your_vnc_password  # (Optional) Specifies the VNC password. Defaults to "vncpassword" if not provided.
     ```

2. **Platform Support:**
   - Supports both AMD64 and ARM64 architectures
   - For ARM64 systems (e.g., Apple Silicon Macs), the container will automatically use the appropriate image

3. **Browser Persistence Modes:**
   - **Default Mode (CHROME_PERSISTENT_SESSION=false):**
     - The browser opens and closes with each AI task.
     - Provides a clean state for every interaction.
     - Consumes fewer system resources.

   - **Persistent Mode (CHROME_PERSISTENT_SESSION=true):**
     - Keeps the browser open between AI tasks.
     - Retains history and session state.
     - Enables reviewing previous AI interactions.
     - Can be configured in the .env file or set as an environment variable when launching the container.

4. **Viewing Browser Interactions:**
   - Open the noVNC viewer by navigating to: [`http://localhost:6080/vnc.html`](http://localhost:6080/vnc.html)  
   - Enter the VNC password (default: `"vncpassword"` or the value set in `VNC_PASSWORD`).  
   - Direct VNC access is available on port **5900**, mapped to container port **5901**.  
   - This allows you to monitor all browser interactions in real time.

5. **Container Management:**
   ```bash
   # Start with persistent browser
   CHROME_PERSISTENT_SESSION=true docker compose up -d

   # Start with default mode (browser closes after tasks)
   docker compose up -d

   # View logs
   docker compose logs -f

   # Stop the container
   docker compose down
   ```

## Changelog
- [x] **2025/01/26:** Thanks to @tiagonascimento31. Now Web Hive can combine with DeepSeek-r1 for enhanced AI capabilities!
