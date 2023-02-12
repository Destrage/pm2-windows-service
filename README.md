
# PM2 Win Server
PM2 is a process manager for the JavaScript runtime Node.js. Unfortunately, PM2 has no built-in startup support for Windows. pm2-win-service uses node-windows to create a service that runs PM2.


#### Original docs (Deprecated): [pm2-windows-service](https://www.npmjs.com/package/pm2-windows-service).

## Install Node and Set NPM:
- Create a folder c:/nodejs for all users to access the npm
- After installation change the default location of NPM by entering the following commands in a CMD/Powershell with Admin privilege:
- ``` npm config set prefix "C:\\nodejs\\npm" ```
- ``` npm config set cache "C:\\nodejs\\npm-cache" ```

## System environments
- Add a new entry in system environments **PM2_HOME** and set the value **C:\nodejs\npm**
- Add a new entry in the path with the value **C:\nodejs\npm**

## Install and Set PM2 as a Service
- Run ```npm install pm2 -g``` to install PM2 globally
- Run `npm i pm2-win-service -g` to install the module globally
- Navigate to **C:\nodejs\npm\node_modules\pm2-win-service** 
    - Run ```pm2-service-install -n PM2_STARTUP_SCRIPT``` where **PM2_STARTUP_SCRIPT will be the name of the service**
    - Enter the following information
        - Perform environment setup (recommended). => **Y**
        - Set PM2_HOME? => **n**
        - Set PM2_SERVICE_SCRIPTS => **Y**
        - Set the list of startup scripts/files (semi-colon separated JSON config files or js files)  => **Enter**
        - Set PM2_SERVICE_PM2_DIR (the location of the global pm2 to use with the service). => **Yes**
        - Specify the directory containing the pm2 version to be used by the service. => **Enter**

## Start a new entry in PM2
`pm2 start ./path/[file name].js --name '[App Name]'` 

`pm2 -f save` to make the process persistent.

for more information visit [pm2](https://pm2.keymetrics.io/docs/usage/quick-start/).
