# Prettier, ESLint, & the Airbnb Style Guide in VS Code

- #### Install npm

  How to install npm isn't really in the scope of this article. See instructions on [github.com/npm/cli](http://github.com/npm/cli 'github.com/npm/cli') for how to install it for your specific OS.

- #### Install npx globally
  npx is a tool intended to make it really easy to use CLI tools and other executables hosted on the npm registry.

`npm install -g npx`

- #### Install ESLint and Prettier

  `yarn add -D prettier`

- #### install babel/eslint-parser

  `npm install eslint @babel/core @babel/eslint-parser --save-dev `
  or
  `yarn add eslint @babel/core @babel/eslint-parser -D`

- #### Install the Airbnb style config for ESLint, and all dependencies
  `npx install-peerdeps --dev eslint-config-airbnb`

The npx utility automatically detects if you are using yarn or npm to manage your codebase, and runs the appropriate commands. If you do not have npx, you will need to manually install the eslint-config-airbnb-base package and all peer dependencies.

- #### Set up ESLint and Prettier configuration
  For this, your project needs .eslintrc . This is the most basic configuration you can provide:

```json
{
	"extends": [
		"airbnb",
		"airbnb/hooks",
		"eslint:recommended",
		"prettier",
		"plugin:jsx-a11y/recommended"
	],
	"parser": "@babel/eslint-parser",
	"parserOptions": {
		"babelOptions": {
			"presets": ["@babel/preset-react"]
		},
		"ecmaVersion": 8,
		"requireConfigFile": false
	},
	"env": {
		"browser": true,
		"node": true,
		"es6": true,
		"jest": true
	},
	"rules": {
		"react/react-in-jsx-scope": 0,
		"react-hooks/rules-of-hooks": "error",
		"no-console": 0,
		"react/state-in-constructor": 0,
		"indent": 0,
		"linebreak-style": 0,
		"react/prop-types": 0,
		"jsx-a11y/click-events-have-key-events": 0,
		"react/jsx-filename-extension": [
			1,
			{
				"extensions": [".js", ".jsx"]
			}
		],
		"prettier/prettier": [
			"error",
			{
				"trailingComma": "es5",
				"singleQuote": true,
				"printWidth": 100,
				"tabWidth": 4,
				"semi": true,
				"endOfLine": "auto"
			}
		]
	},
	"plugins": ["prettier", "react", "react-hooks"]
}
```

- #### Set up VS Code to format your code automatically on save

```json
{
	// Theme
	"workbench.colorTheme": "Andromeda",

	// config related to code formatting
	"editor.fontSize": 15,
	"editor.defaultFormatter": "esbenp.prettier-vscode",
	"editor.formatOnSave": true,
	"[javascript]": {
		"editor.formatOnSave": false,
		"editor.defaultFormatter": null
	},
	"[javascriptreact]": {
		"editor.formatOnSave": false,
		"editor.defaultFormatter": null
	},
	"javascript.validate.enable": false, //disable all built-in syntax checking
	"editor.codeActionsOnSave": {
		"source.fixAll.eslint": true,
		"source.fixAll.tslint": true,
		"source.organizeImports": true
	},
	"eslint.alwaysShowStatus": true,
	// emmet
	"emmet.triggerExpansionOnTab": true,
	"emmet.includeLanguages": {
		"javascript": "javascriptreact"
	}
}
```

Restart VS Code and watch the magic happen!
