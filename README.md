<div align="center">
  <img src="resources/favicon.svg" height="80px" alt="PVE NoteBuddy Logo" />
  <h1>PVE NoteBuddy</h1>
  <p><em>Generate Pretty Proxmox Guest Notes with a Very Innovative Attractive Clean WEB Interface Tool that is a Excellent Enhancement for Proxmox to Enhance the Notes Section via a Simple WEB Based UI</em></p>

  <p>
    <a href="https://jangajones.github.io/pve-notebuddy/">
      <img src="https://img.shields.io/badge/🔗_PVE_NoteBuddy-Live_on_Github_Pages-6bceea?style=for-the-badge&labelColor=2d3748" alt="Website" />
    </a>
  </p>

 **Search a Broad Palette of Templates for your Self-Hosted Services**  
 and adjust them to your liking or just start from scratch.

</div>

<div align="center">
  <sub>🙌 <strong>Shoutout to</strong></sub>
  <br />
  <br />
  <a href="https://helper-scripts.com">
    <img src="https://img.shields.io/badge/community--scripts-Proxmox_VE_Helper--Scripts-0298a1?style=for-the-badge&labelColor=25787d" alt="Community-Scripts" />
  </a>
  <br />
  <sub><a href="https://github.com/community-scripts/ProxmoxVE">View on GitHub</a> • Used their Frontend .jsons to generate My Template Files</sub>
<br />
<br />
  <a href="https://selfh.st/">
    <img src="https://img.shields.io/badge/selfh.st-Icons_for_Self--Hosted-2563eb?style=for-the-badge&labelColor=1e3a8a" alt="selfh.st Icons" />
  </a>
  <br />
  <sub><a href="https://github.com/selfhst/icons">View on GitHub</a> • Consistent, Beautiful Icons for 5000+ Self-Hosted Apps</sub>
</div>
<br />


# 🚀 Features

- Clean & Lightweight, Fully Client-Side App
- Direct HTML-Output Copy Button, ready to Paste to PVE Notes
- Preview Pane that Displays the Notes just like the PVE Web UI would (also supports Dark/Light Mode)
- Over 400 Templated Services (Logo, Website, Default Ports, Default Config Location)
- Directly Embed resizable SVGs from Local or External Sources (Fully Offline Available, No CDN Needed, Vector Quality)
- Option to resize External Images via **[wsrv.nl](https://wsrv.nl/)** (Open-Source, uses Cloudflare as CDN)
- Supports **[selfh.st](https://selfh.st/)** Icon Links natively, you can switch between their Icon variants directly from the UI
- Fields for things like Guest Name, FQDN, Networking & Config Paths
- Custom Note Field to use for Styling or to Input Additional Information (Supports **[Markdown](https://www.markdownguide.org/basic-syntax/)** HTML Tags)
- Alignment, Re-Order & Text Styling Options for every field, many possible Designs
- Import & Export to Save your Own Designs

# 🗒️ Examples

<div align="center">
<p>A Collection of Screenshots from the Proxmox Dashboard and Notes Pane</p>
<table align="center" style="width: 100%;">
  <tr>
    <td align="center" width="50%">
      <img src="screenshots/1.png" width="100%" />
    </td>
    <td align="center" width="50%">
      <img src="screenshots/2.png" width="100%" />
    </td>
  </tr>
  <tr>
    <td align="center" width="50%">
      <img src="screenshots/3.png" width="100%" />
    </td>
    <td align="center" width="50%">
      <img src="screenshots/4.png" width="100%" />
    </td>
  </tr>
  <tr>
    <td align="center" width="50%">
      <img src="screenshots/5.png" width="100%" />
    </td>
    <td align="center" width="50%">
      <img src="screenshots/6.png" width="100%" />
    </td>
  </tr>
  <tr>
    <td align="center" width="50%">
      <img src="screenshots/7.png" width="100%" />
    </td>
    <td align="center" width="50%">
      <img src="screenshots/8.png" width="100%" />
    </td>
  </tr>
  <tr>
    <td align="center" width="50%">
    <img src="screenshots/proxmoxdashboard.png" width="100%" />
    </td>  
  </tr>
</table>

</div>


## Crawl-Scripts

In the Crawl-Scripts Folder inside the Repo there are are 2 Scripts, one to Crawl Content from the **[community-scripts](https://github.com/community-scripts/ProxmoxVE)** Repo (crawl.mjs) and a Second Script (generate-templates.mjs) to transform the `.json` Files in their Repositoy into usable NoteBuddy `.json` Files. Thanks to their Curated Repo, I am able to provide over 400 Templates with Service Names and their Icons, Website Links, Default Ports & Default Config Locations. 

Massive shoutout to them! 🤝

The Crawl-Scripts are only needed to commit Template Updates to this Repo and are not used by NoteBuddy itself.

## Local Deployment

PVE NoteBuddy is Static & Client-Side. For Local Use, run the `main` Branch on any Lightweight Local WEB Server or directly from the Repository Root Directory/Custom Root Directory or Deploy the Contents to run on a Static WEB Server.

### PreRequisite 
Clone NoteBuddy: `git clone --branch main https://github.com/JangaJones/pve-notebuddy.git`<br>
<b>NOTE:</b>Create a Backup Directory and Clone to the Backup Directory.

Create NoteBuddy Custom Root Directory: `mkdir /notebuddy/`<br>

Copy Cloned NoteBuddy Files: `cp -r /(Path)/pve-notebuddy /notebuddy/*`<br>
<b>NOTE:</b> The Service File and Service Script for (Linux - Systemd) or Service Script File for (Alpine - OpenRC) are using  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`/notebuddy/` for the Custom Root Directory to Serve.<br>

If you prefer to Run the APP from the Repository Root Directory then you can Clone the App to the Root File System and you will have to Update the Variables in the Service File and Service Script for (Linux - Systemd) or Service Script File for (Alpine - OpenRC) to Reference the Repository Root Directory.

### $\color{Red}\large{\textsf{Important}}$

Do **Not** Open the `index.html` File directly via `file:///(Drive:)`. NoteBuddy will not work as intended this way.

NoteBuddy loads Template JSON Files Dynamically, and Modern Browsers Block those Local `fetch()` requests when JavaScript sends a request for a File that is not inline with the `index.html` File. This results in Blocking the Template from Loading caused by Browser CORs(Cross Origin Request) Security Restrictions. Use a Local or Self-Hosted Static WEB Server instead.

### $\color{Blue}\large{\textsf{Option 1: Run on a Local WEB Server}}$

<!-- Start of Alpine NODEJS Simple HTTP WEB Server Install -->
<details>
<summary><b>ALPINE SIMPLE HTTP SERVER INSTALL - NODEJS</b></summary><br>
<b>NodeJS Simple HTTP Server (http.server module) Install</b> 

   `apk update`<br>
   `apk add nodejs-current`<br>
   `apk add npm`

Check NodeJS and NPM Version:<br>
`node -v`<br>
`npm -v` 

<b>Temporary Run - Start HTTP-Server</b>

1. Install HTTP-Server: `npm install -g http-server` 

2. cd to Path: `cd /(Path)/(Directory to Serve)`

3. Run in Background: `http-server -p 8080 &`<br> 
   Foreground: `http-server -p 8080`<br> 
   <b>NOTE:</b> You will Lose Console Control with Foreground.<br>
         &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
         Control+C will not work.

5. Access URL: `http://(Localhost or HOST IP Address):8080`

<b>Permanent Run - Start HTTP-Server Automatically on System Boot - Create NodeJS System Service Script(Service File) for Alpine</b>

1. Create Service Script(Service File): `/etc/init.d/httpserver`

```
#!/sbin/openrc-run

description="Start HTTP server on port 8080 using NodeJS"

command="/usr/local/bin/http-server"
command_args="-p 8080"
directory="/notebuddy/"

start_pre() {
    cd "${directory}"
}

show_startup_info() {
    # Define color codes
    GREEN='\033[0;32m'
    YELLOW='\033[1;33m'
    CYAN='\033[0;36m'
    RED='\033[0;31m'
    BLUE='\033[0;34m'
    NC='\033[0m' # No Color

    # Get the version of http-server
    version=$("${command}" --version 2>/dev/null || echo "Unknown")
    
    echo -e "${GREEN}Starting up http-server, serving ./${NC}"
    echo -e "${BLUE}http-server version: ${version}${NC}"
    echo ""
    echo -e "${YELLOW}http-server settings:${NC}"
    echo -e "CORS: ${RED}disabled${NC}"
    echo -e "Cache: ${GREEN}3600 seconds${NC}"
    echo -e "Connection Timeout: ${GREEN}120 seconds${NC}"
    echo -e "Directory Listings: ${GREEN}visible${NC}"
    echo -e "AutoIndex: ${GREEN}visible${NC}"
    echo -e "Serve GZIP Files: ${RED}false${NC}"
    echo -e "Serve Brotli Files: ${RED}false${NC}"
    echo -e "Default File Extension: ${YELLOW}none${NC}"
    echo ""

    # Retrieve local IP addresses portably
    if command -v ip > /dev/null; then
        ip_addresses=$(ip -o -4 addr list | awk '{print $4}' | cut -d/ -f1)
    elif command -v ifconfig > /dev/null; then
        ip_addresses=$(ifconfig | grep -E 'inet ' | awk '{print $2}' | grep -v '127.0.0.1')
    else
        ip_addresses="127.0.0.1"
    fi

    echo -e "${CYAN}Available on:${NC}"
    for ip in ${ip_addresses}; do
        echo -e "  ${YELLOW}http://${ip}:8080${NC}"
    done
    echo ""
} 

start() {
    ebegin "Starting HTTP server"
    show_startup_info
    start-stop-daemon --background --make-pidfile --pidfile /run/http-server.pid \
        --exec "${command}" -- ${command_args}
    eend $?
}

stop() {
    ebegin "Stopping HTTP server"
    start-stop-daemon --stop --pidfile /run/http-server.pid
    eend $?
}
```

2. Add Execute: `chmod +x /etc/init.d/httpserver`

3. Enable Service: `rc-update add httpserver default`

4. Start Service: `rc-service httpserver start`

   Stop and Restart Service:<br>
   `rc-service httpserver stop`<br>
   `rc-service httpserver restart`

   Status Service:<br>
   `rc-service httpserver restart`
</details>
<!-- End of Alpine NODEJS Simple HTTP WEB Server Install --> 

<!-- Start of Alpine PYTHON 3 Simple HTTP WEB Server Install -->
<details>
<summary><b>ALPINE SIMPLE HTTP SERVER INSTALL - PYTHON 3</b></summary><br>
<b>Python 3 Simple HTTP Server (http.server module) Install</b> 

   `apk update`<br>
   `apk add python3`<br>
   `apk add py3-pip`

Check Python 3 and PIP Version:<br> 
`python3 --version`<br>
`pip3 --version`

<b>Temporary Run - Start HTTP-Server</b>

1. cd to Path: `cd /(Path)/(Directory to Serve)`

2. Run in Background: python3 -m http.server 8080 &<br>
   Foreground: python3 -m http.server 8080<br> 
   <b>NOTE:</b> You will Lose Console Control with Foreground.<br>
         &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 
         Control+C will not work.

3. Access URL: `http://(Localhost or HOST IP Address):8080`

<b>NOTE:</b> The http.server Module is a Built-In Module in Python 3 
      so you do not need to install a Http-Server Binary.<br>
      &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
      It is a included Module with Python 3 by Default.

<b>Permanent Run - Start HTTP-Server Automatically on System Boot - Create Python 3 System Service Script(Service File) for Alpine</b>

1. Create Service Script(Service File): `/etc/init.d/httpserver`

```
#!/sbin/openrc-run

description="Start HTTP server on port 8080 using Python 3"

# Directory to serve
directory="/notebuddy/"

# Command to run Python's http.server module
command="/usr/bin/python3"
command_args="-m http.server 8080"

start_pre() {
    # Change to the serving directory
    cd "${directory}"
}

show_startup_info() {
    # Define color codes
    GREEN='\033[0;32m'
    YELLOW='\033[1;33m'
    CYAN='\033[0;36m'
    RED='\033[0;31m'
    BLUE='\033[0;34m'
    NC='\033[0m' # No Color

    # Get the Python version
    version=$("${command}" --version 2>/dev/null || echo "Unknown")
    
    echo -e "${GREEN}Starting up http-server, serving ./${NC}"
    echo -e "${BLUE}http-server version: 14.1.1${NC}"
    echo ""
    echo -e "${YELLOW}http-server settings:${NC}"
    echo -e "CORS: ${RED}disabled${NC}"
    echo -e "Cache: ${GREEN}3600 seconds${NC}"
    echo -e "Connection Timeout: ${GREEN}120 seconds${NC}"
    echo -e "Directory Listings: ${GREEN}visible${NC}"
    echo -e "AutoIndex: ${GREEN}visible${NC}"
    echo -e "Serve GZIP Files: ${RED}false${NC}"
    echo -e "Serve Brotli Files: ${RED}false${NC}"
    echo -e "Default File Extension: ${YELLOW}none${NC}"
    echo ""

    # Retrieve local IP addresses portably
    if command -v ip > /dev/null; then
        ip_addresses=$(ip -o -4 addr list | awk '{print $4}' | cut -d/ -f1)
    elif command -v ifconfig > /dev/null; then
        ip_addresses=$(ifconfig | grep -E 'inet ' | awk '{print $2}' | grep -v '127.0.0.1')
    else
        ip_addresses="127.0.0.1"
    fi

    echo -e "${CYAN}Available on:${NC}"
    for ip in ${ip_addresses}; do
        echo -e "  ${YELLOW}http://${ip}:8080${NC}"
    done
    echo ""
}

start() {
    ebegin "Starting Python http.server"
    show_startup_info
    # Start the server in the background
    start-stop-daemon --background --make-pidfile --pidfile /run/http-server.pid \
        --exec "${command}" -- ${command_args}
    eend $?
}

stop() {
    ebegin "Stopping Python http.server"
    start-stop-daemon --stop --pidfile /run/http-server.pid
    eend $?
}
```

2. Add Execute: `chmod +x /etc/init.d/httpserver`

3. Enable Service: `rc-update add httpserver default`

4. Start Service: `rc-service httpserver start`

   Stop and Restart Service:<br>
   `rc-service httpserver stop`<br>
   `rc-service httpserver restart`

   Status Service:
   `rc-service httpserver status` 
</details>
<!-- End of Alpine PYTHON 3 Simple HTTP WEB Server Install -->

<!-- Start of Debian NODEJS Simple HTTP WEB Server Install -->
<details>
<summary><b>DEBIAN SIMPLE HTTP SERVER INSTALL - NODEJS</b></summary><br>
<b>NodeJS Simple HTTP Server (http.server module) Install</b>

   `apt update`<br>
   `apt install nodejs`<br>
   `apt install npm` 
    
   <b>Temporary Run - Start HTTP-Server</b>
   
1. Install HTTP-Server: `npm install -g http-server` 

2. cd to Path: `cd /(Path)/(Directory to Serve)`

3. Run in Background: `http-server -p 8080 &`<br> 
   Foreground: `http-server -p 8080`<br> 
   <b>NOTE:</b> You will Lose Console Control with Foreground.<br>
         &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
         Control+C will not work.

5. Access URL: `http://(Localhost or HOST IP Address):8080`

Check NodeJS and NPM Version:<br> 
`node -v`<br>
`npm -v`

<b>Permanent Run - Start HTTP-Server Automatically on System Boot - Create NodeJS System Service Script and File for Debian</b>

1. Create Service Script: `/(Path)/start-http-server.sh`

```
#!/bin/bash
cd /notebuddy/
http-server -p 8080 &
```

2. Add Execute: `chmod +x /(Path)/start-http-server.sh`

3. Create Systemd Service File: `/etc/systemd/system/http-server.service`<br>
<b>NOTE:</b> Update (PATH) Variable in Service File.

```
[Unit]
Description= NodeJS HTTP Server
After=network.target

[Service]
Type=simple
User=root
WorkingDirectory=/notebuddy/
ExecStart=/(Path)/start-http-server.sh
Restart=on-failure

[Install]
WantedBy=multi-user.target
```

4. Enable and Start Service:<br>
   `systemctl daemon-reload`<br>
   `systemctl enable http-server`<br>
   `systemctl start http-server`
      
Check Service Status:<br>
`systemctl status http-server`

Stop or Start Service:<br>
`systemctl stop http-server`<br>
`systemctl restart http-server`

</details>
<!-- End of Debian NODEJS Simple HTTP WEB Server Install -->

<!-- Start of Debian PYTHON 3 Simple HTTP WEB Server Install -->

<details>
<summary><b>DEBIAN SIMPLE HTTP SERVER INSTALL - PYTHON 3</b></summary><br>
<b>Python 3 Simple HTTP Server (http.server module) Install</b><br>

`apt update`<br>
`apt install python3`<br>
`apt install python3-pip`
   
<br>Check Python 3 and PIP Version:<br> 
`python3 --version`<br>
`pip3 --version`

<b>Temporary Run - Start HTTP-Server</b><br>

1. cd to Path: `cd /(PATH)/(Directory to Serve)`<br>

2. Run in Background: `python3 -m http.server 8080 &`<br>
Foreground: `python3 -m http.server 8080`<br>
<b>NOTE:</b>You will Lose Console Control with Foreground.<br>
      &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 
      Control+C will not work.<br> 

3. Access URL: `http://(Localhost or HOST IP Address):8080`

<b>NOTE:</b> The http.server Module is a Built-In Module in Python 3 
      so you do not need to install a Http-Server Binary.<br>
      &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
      It is a included Module with Python 3 by Default.

 <b>Permanent Run - Start HTTP-Server Automatically on System Boot - Create Python 3 System Service Script and File for Debian</b>

1. Create Service Script: `/(Path)/start-http-server.sh`

```
#!/bin/bash
cd /notebuddy/
/usr/bin/python3 -m http.server 8080 &
```

2. Add Execute: `chmod +x /(PATH)/start-http-server.sh`<br>

3. Create Systemd Service File: `/etc/systemd/system/http-server.service`<br>                                                                <b>NOTE:</b> Update (PATH) Variable in Service File.  

```
[Unit]
Description=Python HTTP Server
After=network.target

[Service]
Type=simple
User=root
WorkingDirectory=/notebuddy/
ExecStart=/(PATH)/start_http_server.sh
Restart=on-failure

[Install]
WantedBy=multi-user.target
```


4. Enable and Start Service:<br>
   `systemctl daemon-reload`<br>
   `systemctl enable http-server`<br>
   `systemctl start http-server`
   
5. Check Service Status:<br>
   `systemctl status http-server`

Stop or Start Service:<br>
`systemctl stop http-server`<br>
`systemctl restart http-server`

</details>
<!-- End of Debian PYTHON 3 Simple HTTP WEB Server Install -->

<!-- Start of Windows NODEJS Simple HTTP WEB Server Install -->
<details>
<summary><b>WINDOWS SIMPLE HTTP SERVER INSTALL - NODEJS</b></summary><br>
<b>NodeJS Simple HTTP Server (http.server module) Install</b>

Download NodeJS for Windows 10 and Higher: `https://nodejs.org/en/download`

Download NodeJS v13.14.0 for Windows 7 - Official: `https://nodejs.org/en/download/archive/v13.14.0`

Download NodeJS v16.20.2 for Windows 7 - Unofficial: `https://github.com/Alex313031/node16-win7`

<b>Temporary Run - Start HTTP-Server</b>

1. Install NodeJS from Download Links

2. Install HTTP-SERVER - Command Line Run: `npm install -g http-server`

3. cd to Path: `cd /(Path)/(Directory to Serve)`

4. Command Line Run: `http-server`

5. Access URL: `http://(Localhost or HOST IP Address):8080`

Stop HTTP Server: Control + C

$\color{Red}\large{\textsf{Run As A Service:}}$ <b>Task Scheduler or NSSM</b>

<b>TASK SCHEDULER FOR NODEJS:</b><br>
<b>Permanent Run - Start HTTP-Server Automatically on System Boot - Create Task Scheduler NodeJS Service Script</b>

1. Create Batch File

```
@echo off
cd "C:\(PATH)\(Directory to Serve)"
start http-server
```

2. Save Batch File: `C:\(PATH)\starthttpserver.bat`

3. Create Task Scheduler Task:<br>
   A. Open Task Scheduler 
      1. Press Win + R<br> 
      2. Type taskschd.msc<br> 
      3. Press Enter   
   
   B. Click Create Basic Task in the Actions Pane<br>
   C. Name: `NODEJS HTTP Server`<br>
   D. Click Next<br>
   E. Choose When the Computer Starts and click Next<br>
   F. Select Start a Program and Click Next<br>
   G. Click Browse and Select: `starthttpserver.bat`<br>
   H. Click Next<br>
   I. Review the Details<br>
   J. Click Finish
   
5. Run with Highest Privileges<br>
   A. After creating the Task, Right-Click it and Select Properties<br>
   B. <b>Check Run with Highest Privileges</b><br>
   C. Confirm and Close

Server will Automatically Start when Windows Boots.  
 
<b>NSSM FOR NODEJS:</b><br>
<b>Permanent Run - Start HTTP-Server Automatically on System Boot - Create NSSM NodeJS Service Script</b>

Download NSSM from: `https://nssm.cc/download`<br>

1. Create Batch File

```
@echo off
cd "C:\(PATH)\(Directory to Serve)"
start /b http-server
```

2. Save Batch File: `starthttpserver.bat`

3. Download NSSM<br>
   A. Download NSSM from: `https://nssm.cc/download`<br>
   B. Choose the appropriate Version 32-Bit or 64-Bit<br>
   C. Extract the ZIP file to a Folder: `C:\nssm`

5. Install the NodeJS Server as a Service
   A. Open Command Prompt as Administrator
   B. Navigate to the NSSM Directory:

          32-Bit: cd C:\nssm\win32
          64-Bit: cd C:\nssm\win64

6. Install the Service for HTTP Server: `nssm install NodeJSHttpServerService`

7. In the NSSM GUI<br>
   A. Browse and Select node.exe: `C:\Program Files\nodejs\node.exe`<br>
   B. Startup Directory: `C:\(Directory To Batch File)\`<br>
   C. Arguments: `C:\(Directory To Batch File)\starthttpserver.bat`<br>
   D. Click Install Service

9. Configure and Start the Service<br>
   A. Open Windows Services 
      1. Press WIN + R<br> 
      2. Type services.msc <br>
      3. Press Enter
   
   B. Find: NodeJSHttpServerService<br>
   C. Right-click and Select Properties<br>
   D. Set Startup Type: Automatic<br>
   E. Click Start to Run the Service
</details>
<!-- End of Windows NODEJS Simple HTTP WEB Server Install -->

<!-- Start of Windows PYTHON 3 Simple HTTP WEB Server Install -->
<details>
<summary><b>WINDOWS SIMPLE HTTP SERVER INSTALL - PYTHON 3</b></summary><br>
<b>Python Simple HTTP Server (http.server module) Install</b>

Download Python 3 Windows 10 or Higher: `https://www.python.org/downloads/`

Download Python v3.8.10 for Windows 7 - Official: `https://www.python.org/downloads/release/python-3810/`

Download Python v3.8 and Newer for Windows 7 - Unofficial: `https://github.com/Alex313031/Python-Win7`

<b>Temporary Run - Start HTTP-Server</b>

1. Install Python 3 from Download Links

2. cd to Path: `cd /(Path)/(Directory to Serve)`

3. Command Line Run: `python -m http.server 8080`

4. Access URL: `http://(Localhost or HOST IP Address):8080`

Stop HTTP Server: Control + C

$\color{Red}\large{\textsf{Run As A Service:}}$ <b>Task Scheduler or NSSM</b>

<b>TASK SCHEDULER FOR PYTHON:</b><br>
<b>Permanent Run - Start HTTP-Server Automatically on System Boot - Create Task Scheduler Python Service Script for Windows</b>

1. Create Batch File

```
@echo off
cd "C:\(PATH)\(Directory to Serve)"
start "" "C:\(PATH)\Python\python.exe" -m http.server 8080
```

2. Save Batch File: `C:\(PATH)\starthttpserver.bat`

3. Create Task Scheduler Task:<br>
   A. Open Task Scheduler 
      
      1. Press Win + R 
      2. Type taskschd.msc 
      3. Press Enter
   
   B. Click Create Basic Task in the Actions Pane<br>
   C. Name: `Python HTTP Server`<br>
   D. Click Next<br>
   E. Choose When the Computer Starts and click Next<br>
   F. Select Start a Program and Click Next<br>
   G. Click Browse and Select: `starthttpserver.bat`<br>
   H. Click Next<br>
   I. Review the Details<br>
   J. Click Finish

5. Run with Highest Privileges<br>
   A. After creating the Task, Right-Click it and Select Properties<br>
   B. <b>Check Run with Highest Privileges</b><br>
   C. Confirm and Close

Server will Automatically Start when Windows Boots.

<b>NSSM FOR PYTHON:</b><br>
<b>Permanent Run - Start HTTP-Server Automatically on System Boot - Create NSSM Python Service Script for Windows</b>

Download NSSM from: `https://nssm.cc/download`<br>

1. Create Batch File

```
@echo off
cd "C:\(PATH)\(Directory to Serve)"
"C:\(PATH)\(Python Directory)\python.exe" -m http.server 8080
```

2. Save Batch File: `starthttpserver.bat`

3. Download NSSM<br>
   A. Download NSSM from: `https://nssm.cc/download`<br>
   B. Choose the appropriate Version 32-Bit or 64-Bit<br>
   C. Extract the ZIP file to a Folder: `C:\nssm`

4. Install the NodeJS Server as a Service<br>
   A. <b>Open Command Prompt as Administrator</b><br>
   B. Navigate to the NSSM Directory:

          32-Bit: cd C:\nssm\win32
          64-Bit: cd C:\nssm\win64

5. Install the Service for HTTP Server: `nssm install PythonHttpServerService`

6. In the NSSM GUI<br>
   A. Browse and Select python.exe:<br> 
      All Users Installation: `C:\Program Files\(Python Directory)\python.exe`<br>
      Per User Installation: `C:\Users\(Username)\AppData\Local\Programs\Python\Python(XY)\python.exe`<br>
   B. Startup Directory: `C:\(Directory To Batch File)\`<br>
   C. Arguments: `C:\(Directory To Batch File)\starthttpserver.bat`<br>
   D. Click Install Service

7. Configure and Start the Service<br>
   A. Open Windows Services<br> 
      
      1. Press WIN + R 
      2. Type services.msc 
      3. Press Enter
   
   B. Find: PythonHttpServerService<br>
   C. Right-click and Select Properties<br>
   D. Set Startup Type: Automatic<br>
   E. Click Start to Run the Service
</details>
<!-- End of Windows PYTHON 3 Simple HTTP WEB Server Install -->

### $\color{Blue}\large{\textsf{Option 2: Deploy to a Static WEB Server}}$

Clone the Repository and Serve the Project Directory with your preferred Static Hosting Solution.

```bash
git clone --branch main https://github.com/JangaJones/pve-notebuddy.git
```

Examples:

- Nginx
- Apache
- Caddy
- any Simple Static File Host

## API & Automation

Currently API & Automation (e.g. Automatic Publishing to Proxmox or fetching the HTML Output with a GET Request) is not on the table, since this currently exceeds my skillset and would only Weaken Robustness and Security. PVE NoteBuddy will remain separate from Proxmox or Automation/Deployment Tools. This may or may not change in the future.

## Disclaimer

_The recent problems that erupted in the Technology Community with Vibe-Coded Apps, specifically regarding Security Issues are concerning. The App is Fully Client-Sided and No AI Client Side, there is No Backend and No AI Backend, No use of Telemetry Tracking + it's Hosted on GitHub Pages. I am definitely categorizing NoteBuddy as safe to visit & use. Still - I want to Disclose, that I had Assistance from an AI Agent to Create & Troubleshoot Parts of the Scripts inside this Repository. I used it to write the Parser for the the Final HTML Output, the SVG Embed Feature, the Scaling Feature, the handling of JSON Files for Import/Export as well as the Script for Template Creation. The `.html`, `.css`, as well as a portion of the `app.js` still includes a lot of Handwritten Code that took many hours and a lot of coffee. The Code has been thoroughly Reviewed and Tested by myself. Be aware, since I am a Hobbyist-Coder, My Skills and Knowledge are Limited, but My Decade Long Non-Pro Experience with HTML and JS is still significant._



