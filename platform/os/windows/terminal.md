## 配置文件

```Settings
// To view the default settings, hold "alt" while clicking on the "Settings" button.
// For documentation on these settings, see: https://aka.ms/terminal-documentation

{
    "$schema": "https://aka.ms/terminal-profiles-schema",

    "defaultProfile": "{58ad8b0c-3ef8-5f4d-bc6f-13e4c00f2530}",

    "profiles":
    [
        {
            // Make changes here to the powershell.exe profile
            "guid": "{61c54bbd-c2c6-5271-96e7-009a87ff44bf}",
            "name": "Windows PowerShell",
            "commandline": "powershell.exe",
            "hidden": false
        },
        {
            // Make changes here to the cmd.exe profile
            "guid": "{0caa0dad-35be-5f56-a8ff-afceeeaa6101}",
            "name": "cmd",
            "commandline": "cmd.exe",
            "hidden": true
        },
        {
            "guid": "{b453ae62-4e3d-5e58-b989-0a998ec441b8}",
            "hidden": true,
            "name": "Azure Cloud Shell",
            "source": "Windows.Terminal.Azure"
        },
        {
            "guid": "{58ad8b0c-3ef8-5f4d-bc6f-13e4c00f2530}",
            "hidden": false,
            "name": "Debian",
            "commandline": "bash.exe ~",
            "fontFace": "Fira Code Retina",
            "fontSize": 18,
            "source": "Windows.Terminal.Wsl"
        }
    ],

    // Add custom color schemes to this array
    "schemes": [
        {
        }
    ],

    // Add any keybinding overrides to this array.
    // To unbind a default keybinding, set the command to "unbound"
    "keybindings": [
		{
			"command": "newTab",
			"keys": [
				"ctrl+n"
			]
		},
		{
			"command": "closeTab",
			"keys": [
				"ctrl+w"
			]
		},
		{
			"command": "copy",
			"keys": [
				"ctrl+insert"
			]
		},
		{
			"command": "paste",
			"keys": [
				"shift+insert"
			]
		},
		{
			"command": "increaseFontSize",
			"keys": [
				"ctrl+="
			]
		},
		{
			"command": "decreaseFontSize",
			"keys": [
				"ctrl+-"
			]
		}
    ]
}

```

### 参考

- [配置文件声明](https://raw.githubusercontent.com/microsoft/terminal/master/doc/cascadia/profiles.schema.json)