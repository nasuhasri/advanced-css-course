"watch:sass": "node-sass sass/main.scss css/style.css -w",
"devserver": "live-server",
"start": "npm-run-all --parallel devserver watch:sass",
"compile:sass": "node-sass sass/main.scss css/style.comp.css",
"concat:sass": "concat -o css/style.concat.css css/icon-font.css css/style.comp.css",
"prefix:css": "postcss --use autoprefixer -b 'last 10 versions' css/style.concat.css -o css/style.prefix.css",
"compress:css": "node-sass css/style.prefix.css css/style.css --output-style compressed",
"build:css": "npm-run-all compile:sass concat:sass prefix:css compress:css"

1. For development, use `npm start`.
2. For production, use `npm build:css`.

### Explaination of scripts

1. watch:sass - watch main.scss file and the output file is placed in style.css
2. devserver - get live-server
3. start - run all in parallel
4. compile:sass - compile main.scss into style.comp.css
5. concat:sass - merge icon-font.css file and style.comp.css file into one file --> style.concat.css
6. prefix:css - using postcss cli command with option (--use) of autoprefixer, get last 10 version of browser using option (-b) with input of style.concat.css file and put output into style.prefix.css
7. compress:css - input file from prefix is compressed into style.css file
8. build:css - run all tasks above by sequence
