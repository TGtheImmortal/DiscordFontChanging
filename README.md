Mirror from [https://www.reddit.com/r/pcgaming/comments/zb5783/guide\_changing\_discords\_font/](https://www.reddit.com/r/pcgaming/comments/zb5783/guide_changing_discords_font/) while I await reinstatement from the automod.

J/K: Reddit sucks, https://imgur.com/a/vGuZUNs. This post will now live here and [https://www.reddit.com/r/redditModPowerTrip/comments/zcduf9/guide_changing_discords_fonts/?sort=new](https://www.reddit.com/r/redditModPowerTrip/comments/zcduf9/guide_changing_discords_fonts/?sort=new). You can message me for help at u/TGtheImmortal on Reddit or here.

Note: This is more or less a cross-post for visibility since discordapp mods were removing my posts. I've included some Info on BetterDiscord here as well, since that is banned in that subreddit.

First and foremost, big thanks to  [u/nice\_\_username](https://www.reddit.com/user/nice__username/) for their [post yesterday](https://www.reddit.com/r/discordapp/comments/z9v2c2/how_to_change_the_font_back/).

I thought I wanted to make a video, but I'm too damn lazy for that.. instead I just learned just enough HTML/CSS/JS to fix this on most platforms. I'll probably end up looking into an Android fix once that rolls out, or just never update the app.

Warning: I am a stranger; I am not a developer; I just like to solve problems. The new font is a problem for me. Use any of this at your own risk. Do research like I did to determine if you trust this.

There are a couple of approaches to this and hopefully I can break them all down in a clear and (relatively) concise manner. I am a Windows users and as such have not tested these steps on any other platform, but considering it's a web program it should mostly be the same.

Note: All of the below methods utilize a web-hosted version of Whitney. There are methods to use local copies, but that will not be covered.

# Method 1: Desktop Client

Prerequisites: Modify your settings file to allow access to the chromium dev tools. Discord is built on Electron, which is essentially just Chromium + Node JS.

1. Press (WIN + R) to open run.
2. Paste the following and hit enter.
```  
%AppData%/Discord/settings.json
```
3. This will bring up selection for editing files. You can use any text editor.
4. Add the following line exactly... It should end up looking something like this, making sure the new line is within the first left curly bracket ( { ), but before the second. [https://imgur.com/a/ALwoG7P](https://imgur.com/a/ALwoG7P)
```  
 "DANGEROUS\_ENABLE\_DEVTOOLS\_ONLY\_ENABLE\_IF\_YOU\_KNOW\_WHAT\_YOURE\_DOING": true,
```
5. Save the file. Close and reopen Discord completely. (Aka, make sure you close it out of your tray.)
6. Dev tools should now load when you press (Ctrl + Shift  + I) in Discord. If it doesn't, you did something wrong.

# 1A. Manual (Apply at every start of Discord)

1. Press (Ctrl + Shift + I) to open dev tools.
2. Press the Console tab at the top, or press (Ctrl + \` ).
3. Paste the following code into console. Change "Whitney Book" to any [safe web font](https://www.cssfontstack.com/) you'd like. YMMV.
```
document.head.insertAdjacentHTML('beforeend','<link href="https://fonts.cdnfonts.com/css/whitney-2" rel="stylesheet">');
let whitneyLove = document.createElement('style');
whitneyLove.innerHTML = 'body{ font-family: "Whitney Book"}'
document.head.appendChild(whitneyLove);
```

&#x200B;

# 1B. Semi-automated (Apply at every start of Discord)

1. Download [AutoHotKey](https://www.autohotkey.com/download/ahk-install.exe) (direct exe link to right version) and install.
2. Make a new text file and paste the following code into it.  
```
^+p::
	changeFont(){
		WinActivate, ahk_exe Discord.exe
		SendInput ^+i
		Sleep 3000
		Send {ctrl down}``{ctrl up}
		Sleep 3000
		Send {text}document.head.insertAdjacentHTML('beforeend','<link href="https://fonts.cdnfonts.com/css/whitney-2" rel="stylesheet">');
		Send +{enter}
		Send {text}let whitneyLove = document.createElement('style');
		Send +{enter}
		Send {text}whitneyLove.innerHTML = 'body{ font-family: "Whitney Book"}'
		Send +{enter}
		Send {text}document.head.appendChild(whitneyLove);`n
		SendInput ^+i
}
```
3. File -> Save As , change the "Save as type" to "All files (\*.\*)".

4. Type something fun for the name and end it with ".ahk" instead of .txt.

5. Run the .ahk script by double clicking on it.

6. With Discord open, press (Ctrl + Shift + P} to trigger an automated method of using the manual method.

&#x200B;

# Method 2: Web Client 

# 2A. Manual (Apply at every start of Discord's web client)

This is the same as the manual desktop client method, except you don't have to go enable the tools, they're just on by default. Follow "1A. Manual".

# 2B. Automatic (Permanent)

1. Install [Stylus for Firefox](https://addons.mozilla.org/en-US/firefox/addon/styl-us/) or [Stylus for Chromium-based browsers](https://chrome.google.com/webstore/detail/stylus/clngdbkpkpeebahjckkjfobafhncgmne).
2. Open Stylus and click "Manage".
3. On the left side under "Actions", click "Write new style".
4. Paste the following starting at line 9, give it a name and hit "Save". You can toggle this on or off from the Stylus extension, or make your own.
```
@-moz-document url-prefix("https://discord.com/channels/") {
    @import url('https://fonts.cdnfonts.com/css/whitney-2');
    body {
        font-family: 'whitney-2', 'Whitney Book';
        font-weight: normal;
    }
}
```
&#x200B;

# Method 3: BetterDiscord (Permanent)

BetterDiscord allows a lot of things. Check out the link below for more information. The primary usage here is to change the CSS on load without having to do anything.

1. Install [Better Discord](https://betterdiscord.app/)
2. Open Discord and go to Settings -> Custom CSS.
3. Paste the following and press save.
```
@import url('https://fonts.cdnfonts.com/css/whitney-2');
    body {
        font-family: 'whitney-2', 'Whitney Book';
        font-weight: normal;
    }
```

Everything in this post is free to use or modify... let me know how to make it better!

Edit: I added some descriptions on the methods to better indicate how they have to be applied and if they're permanent or not. Changed some formatting.
