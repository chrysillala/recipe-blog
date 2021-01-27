# Default starter for Gridsome

This is the project you get when you run `gridsome create new-project`.

### 1. Install Gridsome CLI tool if you don't have

`npm install --global @gridsome/cli`

### 2. Create a Gridsome project

1. `gridsome create my-gridsome-site` to install default starter
2. `cd my-gridsome-site` to open the folder
3. `gridsome develop` to start a local dev server at `http://localhost:8080`
4. Happy coding 🎉🙌

### Install source filesystem
transform files into content that can be fetched with GraphQL in your components
```
yarn add @gridsome/source-filesystem
```

```
yarn add @gridsome/transformer-remark
```


plugin
https://gridsome.org/plugins/gridsome-plugin-tailwindcss

or manual
for this site i will go manual


### Install tailwind css
install TailwindCSS
yarn add -D tailwindcss


install PostCSS-PurgeCSS:
yarn add -D @fullhuman/postcss-purgecss


src/assets/css/tailwind.css
@tailwind base;

@tailwind components;

@tailwind utilities;


main.js
// Import global styles
require('~/main.css')


Optionally, if you would like to customize your TailwindCSS installation
npx tailwindcss init


gridsome.config.js needs to be updated to add our TailwindCSS and PurgeCSS configuration
const tailwind = require('tailwindcss')
const purgecss = require('@fullhuman/postcss-purgecss')

const postcssPlugins = [
	tailwind(),
]

if (process.env.NODE_ENV === 'production') postcssPlugins.push(purgecss(require('./purgecss.config.js')))

module.exports = {
    siteName: 'Gridsome',
    plugins: [],
    css: {
        loaderOptions: {
            postcss: {
                plugins: postcssPlugins,
            },
        },
    },
}


create a purgecss.config.js file in the root of your project
module.exports = {
    content: [
        './src/**/*.vue',
        './src/**/*.js',
        './src/**/*.jsx',
        './src/**/*.html',
        './src/**/*.pug',
        './src/**/*.md',
    ],
    whitelist: [
        'body',
        'html',
        'img',
        'a',
        'g-image',
        'g-image--lazy',
        'g-image--loaded',
    ],
    extractors: [
        {
            extractor: content => content.match(/[A-z0-9-:\\/]+/g),
            extensions: ['vue', 'js', 'jsx', 'md', 'html', 'pug'],
        },
    ],
}


Make sure to restart the gridsome develop command to ensure the changes are compiled in the current build.

### Install netlify cms
yarn add netlify-cms gridsome-plugin-netlify-cms

