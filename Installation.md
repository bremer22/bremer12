#### Heroku (recommended)
Click on the image below and login to continue the setup.<br>
[![Deploy](https://www.herokucdn.com/deploy/button.svg)](https://heroku.com/deploy?template=https://github.com/slow/nitro-sniper/tree/main)  
Make sure you go to your app -> Configure dynos/Resources and turn off `web` and start `worker`.<br>
You can then see logs by clicking on `More` (top right) and then `View logs`.<br>

#### Local
- Make sure [Node](https://nodejs.org/en/) is installed on your system and open a command prompt/terminal.
- Run `git clone https://github.com/slow/nitro-sniper nitro-sniper`
- Run `cd nitro-sniper`
- Run `npm install`
- Edit the .env file.
- Run `node .`