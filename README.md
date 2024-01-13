# React-setup-using-Webapck-and-Babel
🚀 Master React JS with Webpack and Babel - Comprehensive Tutorial 🚀

📺 Video Overview:
Welcome to this in-depth tutorial on using React JS with Webpack and Babel. In this video, we'll guide you through the process of setting up a React project with the powerful combination of Webpack for bundling and Babel for transpiling.

# Getting started
React JS setup using Webpack and babel
```bash
$ git clone https://github.com/ashishd1123/React-setup-using-Webapck-and-Babel.git
$ cd client
$ git checkout main
```

# Follow Some Steps for setup React JS Project

# 1. Create a root folder to initialize npm in it (optionally, it can also be initialized).
mkdir ReactProject
cd ReactProject

# 2. We need a package.json file to create modules, so we initialize npm
npm init -y
npm install react react-dom –save

# 3. Install webpack We need to install a webpack to create a bundler.
npm i -D webpack webpack-dev-server webpack-cli html-webpack-plugin

# 4. Install Babel Install babel, and its plugins babel-core, babel-loader, babel-preset-env, babel-preset-react, and, HTML-webpack-plugin

npm i -D @babel/core @babel/preset-env @babel/preset-react babel-loader

# 5. To load CSS, you have to install CSS and style-loader.
npm i -D css-loader sass sass-loader style-loader url-loader 

# 6. Create .babelrc file
```bash
{
    "presets": ["@babel/preset-env", "@babel/preset-react"]
}
```

# 7. Create webpack.config.js
```bash
const path = require("path");
const HtmlWebpackPlugin = require("html-webpack-plugin");
module.exports = {
  output: {
    path: path.join(__dirname, "/dist"), // the bundle output path
    filename: "bundle.js", // the name of the bundle
  },
  plugins: [
    new HtmlWebpackPlugin({
      template: "src/index.html", // to import index.html file inside index.js
    }),
  ],
  devServer: {
    port: 3000, // you can change the port
  },
  module: {
    rules: [
      {
        test: /\.(js|jsx)$/, // .js and .jsx files
        exclude: /node_modules/, // excluding the node_modules folder
        use: {
          loader: "babel-loader",
        },
      },
      {
        test: /\.(sa|sc|c)ss$/, // styles files
        use: ["style-loader", "css-loader", "sass-loader"],
      },
      {
        test: /\.(png|woff|woff2|eot|ttf|svg)$/, // to import images and fonts
        loader: "url-loader",
        options: { limit: false },
      },
    ],
  },
};

```