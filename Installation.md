### Repl.it (recommended)

- Visit the [dashboard](https://replit.com/~)
- Click the `New Repl` button as seen below.<br/>
   ![Image](https://media.wtf/21365449)

- Select the `Bash` template as seen below.<br/>
   ![Image](https://media.wtf/75810639)

- After your project gets created, delete everything in `main.sh` and paste this piece of code:
```bash
PACKAGE_VERSION=$(node -p -e "try { require('./nitro-sniper/package.json').version } catch { '0.0.0' }")
LATEST_VERSION=$(curl --silent "https://raw.githubusercontent.com/slow/nitro-sniper/main/package.json" | grep '"version":' | sed -E 's/.*"([^"]+)".*/\1/')

function compareVersions {
   echo "$@" | awk -F. '{ printf("%d%03d%03d%03d\n", $1,$2,$3,$4); }'; 
}

function installAll() {
   echo "$(tput setaf 6)Installing packages, please wait..."
   install-pkg "http://archive.ubuntu.com/ubuntu/pool/main/g/glib2.0/libglib2.0-0_2.56.4-0ubuntu0.18.04.8_amd64.deb" &> /dev/null
   echo "$(tput setaf 2)Installed dependencies."
   echo "$(tput setaf 6)Cloning the latest sniper code..."
   rm -rf nitro-sniper &> /dev/null
   git clone https://github.com/slow/nitro-sniper nitro-sniper &> /dev/null
   cd nitro-sniper
   echo "$(tput setaf 2)Cloned latest version of the sniper."
   echo "$(tput setaf 6)Installing sniper dependencies..."
   npm install &> /dev/null
   echo "$(tput setaf 2)Installed sniper dependencies."
   echo "$(tput setaf 2)Running sniper..."
   npx node ./src/index.js
}

if [ $(compareVersions $PACKAGE_VERSION) -lt $(compareVersions $LATEST_VERSION) ]; then 
   installAll
else
   cd nitro-sniper
   npx node ./src/index.js
fi
```

- The file should now look like this: <br/>
   ![Image](https://media.wtf/68696927)

- Visit the environment variables tab.<br/>
   ![Image](https://media.wtf/52361997)

- Set the key as `settings` and paste [this](#default-configuration) inside the value text box; proceed to edit your configuration.

- After you are done editing your configuration, click `Add new secret`. (You can go back to that tab whenever to change your settings)<br/>
   ![Image](https://media.wtf/49612563)

- You can now use <kbd>CTRL</kbd> + <kbd>ENTER</kbd> or  <kbd>CMD</kbd> + <kbd>ENTER</kbd> to start the sniper or by using the `Run` button at the top of the page.

- Tips:
   - If you want to keep the sniper running 24/7 even when you shut down your PC, use [uptime robot](https://uptimerobot.com/) to ping the repl.it URL as seen here
   ![Image](https://media.wtf/88041379) <br />
   - To see the output of the sniper, go to the `Console` tab. <br />
   ![Image](https://media.wtf/37329719)
   - If you wish to update the sniper when a new version is released you can run `git pull` in the `Shell` tab as seen in this screenshot: <br />
   ![Image](https://media.wtf/81080054)

### Local
- Make sure [Node v14+](https://nodejs.org/en/) is installed on your system and open a command prompt/terminal.
- Run `git clone https://github.com/slow/nitro-sniper nitro-sniper`
- Run `cd nitro-sniper`
- Run `npm install`
- Edit the .env file.
- Run `node .`