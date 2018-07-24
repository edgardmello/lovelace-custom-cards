# Custom cards development
I use a separate development environment to develop custom cards for lovelace. Please check my repository https://github.com/helto4real/hassio för my Home Assistant configuration

## Setup the dev environment

1. First setup the npm tool that comes with nodejs. You can find it here. https://www.npmjs.com/get-npm by clicking on the "Download Node.js and npm" button.
2. while in git root folder, run `npm i -g webpack-cli` then run `npm i .` to install all dependecies (OBS: NPM DOES NOT SUPPORT UNC PATHS so make sure you are on a normal drive letter)
3. run `npm start` to compile and run the devserver
4. run the components html file in your browser under http://localhost:8081/dist/picture-status-element.html for example. Check your portsetting it might be different from 8081 

if you want to build to production custom-cards.js file, run ```npm run-script prod``` then copy the custom_cards.js file to /www/{your custom card location} at your Home Assistant config folder

5. reference card in `ui-lovelace.yaml` like this:
```resources:
  - url: /local/{your custom card location}/custom-cards.js?v=1.001
    type: module``` The v=1.xxx is so you can make sure the broweser dont cache when you release new versions

## The structure

- webpack.*.js, contains the package information for dev and prod builds for webpack
- package.json, the package information, scripts, etc.
- src/*, here are all the card source files and corresponding test HTML file
- dist/*, here are the built merged source scripts that can be used in Home assistant (if prodbuild)
