# VSCode setup

### Theme

I use the `Oceanic Next` theme with the dimmed bg option. [Link &rarr;](https://marketplace.visualstudio.com/items?itemName=naumovs.theme-oceanicnext)

### Extensions used

For each of the extensions, read the overview page in order to learn how to use it.

`Auto Close Tag` to automatically close HTML tags. [Link &rarr;](https://marketplace.visualstudio.com/items?itemName=formulahendry.auto-close-tag)

`Auto Rename Tag` to automatically change matching HTML tags. [Link &rarr;](https://marketplace.visualstudio.com/items?itemName=formulahendry.auto-rename-tag)

`Color Highlight` to, as the name says, highlight colors in CSS. [Link &rarr;](https://marketplace.visualstudio.com/items?itemName=naumovs.color-highlight)

`Paste and Indent` to automatically indent pasted code. [Link &rarr;](https://marketplace.visualstudio.com/items?itemName=Rubymaniac.vscode-paste-and-indent)

`Path Intellisense` to autocomplete filenames. [Link &rarr;](https://marketplace.visualstudio.com/items?itemName=christian-kohler.path-intellisense)

`Prettier` to automatically format code. [Link &rarr;](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode)

### Other extensions 

`Project Manager` to easily switch between projects. One of the most useful extensions. [Link &rarr;](https://marketplace.visualstudio.com/items?itemName=alefragnani.project-manager)

### Settings


```
{
  "workbench.colorTheme": "Oceanic Next (dimmed bg)",
  "files.autoSave": "onFocusChange",
  "editor.minimap.enabled": true,
  "workbench.statusBar.visible": true,
  "workbench.activityBar.visible": true,
  "editor.formatOnSave": false,

  "workbench.colorCustomizations": {
    "statusBar.background": "#333333",
    "statusBar.noFolderBackground": "#333333",
    "statusBar.debuggingBackground": "#263238"
  },
  "editor.fontSize": 16,

  "css.validate": false,
  "scss.validate": false,
  "less.validate": false,
  "editor.wordWrap": "on"
}
```