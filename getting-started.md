# Getting Started

## Language Server

We produce a language server for QSS that allows integration with your IDE of choice. It basically boxes the compiler - so errors and warnings are displayed as you type. You can get the language server and TextMate syntax highlighting bundle by installing the QSS support bundle through [itch.io](https://thirds.itch.io/quest-sage).

### JetBrains IDEs \(including IntelliJ IDEA\)

We recommend installing the [LSP plugin](https://plugins.jetbrains.com/plugin/10209-lsp-support) to use the language server. To tell the LSP plugin to use our language server for \*.qss files, go to Settings &gt; Languages & Frameworks &gt; Language Server Protocol &gt; Server Definitions, and make a new "Raw command" definition. Set the extension to `qss` \(not `.qss` or `*.qss`\). Set the command to run the server JAR, for example:

```bash
java -jar C:/quest-sage/qss.ide-1.0.0-SNAPSHOT-ls.jar
```

This should enable error and warning messages when you open `*.qss` files in the editor. Sometimes the LSP plugin doesn't interpret the whole file correctly and you may get nonsensical error messages - just close and re-open the file and it should fix itself. If you can't see any messages \(and you think there should be some\), check to see the coloured circle in the bottom right of the screen to the left of the line number indicator. If the light is red, the language server isn't running. If it's yellow, it's still initialising. If it's green, then the language server is running correctly in the background.

To get syntax highlighting, install the [TextMate Bundles plugin](https://plugins.jetbrains.com/plugin/7221-textmate-bundles). Once it's installed, go to Settings &gt; Editor &gt; TextMate Bundles, and click the + icon in the top right. Select the folder containing the `qss.tmLanguage` file. You should now see correct syntax highlighting in `*.qss` files.

