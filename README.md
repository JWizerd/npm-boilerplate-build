# NPM Boilderplate Build

## use npm as a taskrunner using scripts in package.json

### dependencies
1. **node-sass** for sass,
2. **nodemon** for watch changes
3. **postcss-cli** dependency for autoprefixer
4. **autoprefixer** inject vendor prefixes into css
5. **cssnano** minify css for production
6. **uglifyjs** minify js for production

### install script
```
npm install
npm run preinstall /* install all globally required packages for CLI */
```

### scripts: paths following *--include-path will need to be changed for your project*
```
"scripts": {
  "preinstall": "npm install --global postcss-cli autoprefixer cssnano-cli uglify-js",
  "build-css": "node-sass --include-path scss assets/scss/main.scss assets/css/main.css && postcss --use autoprefixer -r ./assets/css/main.css",
  "watch-css": "nodemon -e scss -x \"npm run build-css\"",
  "production": "cssnano ./assets/css/main.css ./assets/css/main.min.css && uglifyjs ./assets/js/main.js --compress --output ./assets/js/main.min.js"
}
```

### CLI Commands
```
npm run build-css /* compile sass to css and and add vendor prefixes */

npm run watch-css /* watch for sass changes and if changes run build-css */

npm run production /* minify css and js and create new *.min.css & *.min.js files
```
