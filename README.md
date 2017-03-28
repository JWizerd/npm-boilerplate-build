# NPM Boilerplate Build

## use npm as a taskrunner using scripts in package.json

### dependencies
1. **node-sass** for sass,
2. **nodemon** for watch changes
3. **postcss-cli** dependency for autoprefixer
4. **autoprefixer** inject vendor prefixes into css
5. **cssnano** minify css for production
6. **uglifyjs** minify js for production
7. **concat** concatenate files together

### install script
```
npm install
```
install all globally required packages for CLI
```
npm run preinstall
```

### scripts: paths will need to be changed relative to your project
```
"scripts": {
  "preinstall": "npm install --global postcss-cli autoprefixer cssnano-cli uglify-js concat",
  "build-css": "concat -o ./assets/scss/main.scss ./assets/scss/*.scss && node-sass --include-path scss assets/scss/main.scss assets/css/main.css && postcss --use autoprefixer -r ./assets/css/main.css",
  "watch-css": "nodemon -e scss -x \"npm run build-css\"",
  "production": "concat -o ./assets/js/dist/main.js ./assets/js/*.js && uglifyjs ./assets/js/dist/main.js --compress --output ./assets/js/dist/main.min.js && cssnano ./assets/css/main.css ./assets/css/main.min.css"
}
```

### CLI Commands
**compile sass to css and and add vendor prefixes**
```
npm run build-css
```
**watch for sass changes and if changes run build-css**
```
npm run watch-css
```
**minify css and js and create new .min.css & .min.js files**

```
npm run production
```
**concat and minify css and js files. NOTE: for proper functionality make sure to create a dist/ folder inside of asset folders for you sass and js. js/dist and scss/dist. This makes that concat output file isn't also concatenated on production.**
