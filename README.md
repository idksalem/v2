# SalemMP
### SalemMP is a modified fork of LawinServerV2 MASSIVE Credits to Milxnor and Lawin


## How to host SalemMP
1) Install [NodeJS](https://nodejs.org/en/) and [MongoDB](https://www.mongodb.com/try/download/community).
2) Download and Extract LawinServerV2 to a safe location.
3) Run "install_packages.bat" to install all the required modules.
4) Go to Config/config.json in the directory you extracted LawinServerV2 into.
5) Open it, set your discord bot token (DO NOT SHARE THIS TOKEN) and save it. The discord bot will be used for creating accounts and managing your account.
6) Set your ip and port information aswell I strongly reccomend putting 127.0.0.1 as your ip as some internet providers block self connection.
7) Run "start.bat", if there is no errors, it should work. It should display

----------------------------------------------------------------------

1) BACKEND: App started listening on port 3551
2) XMPP: XMPP and Matchmaker started listening on port 80
3) BACKEND: App successfully connected to MongoDB!
4) BOT: Bot is up and running!

----------------------------------------------------------------------

8) Use something to redirect the Fortnite servers to localhost:3551. (I reccomend Fiddler, Below the instrusctions i will provide the command to do this. You can also use a ssl bypass that redirects servers, or somthing like craniun)
9) Go to the discord and create TWO accounts one for you and one for the server when launching the server whether it be manually or with a launcher PLEASE make sure its logged into a REAL account.
10) When Fortnite launches and is connected to the backend, enter your email and password (or launch with an exchange code) then press login. It should let you in and everything should be working fine.

## Fiddler Command

import System;
import System.IO;
import System.Threading;
import System.Web;
import System.Windows.Forms;
import Fiddler;

class Handlers
{
    static function OnBeforeRequest(oSession: Session) {
        if (oSession.hostname.Contains(".ol.epicgames.com"))
        {
            if (oSession.HTTPMethodIs("CONNECT"))
            {
                // This is just a fake tunnel for CONNECT requests
                oSession["x-replywithtunnel"] = "FortniteTunnel";
                return;
            }

            oSession.fullUrl = "http://127.0.0.1:3551" + oSession.PathAndQuery;
        }
    }
}


### How to set up moderators?
1) Go to Config/config.json in the directory you extracted LawinServerV2 into.
2) Open it, you should see a "moderators" section in the file.
3) You have to get your discord id and replace discordId with it.
4) You can set multiple moderators like this `["discordId","discordId2"]`

## Features
### LawinServer V2
- CloudStorage and ClientSettings (Settings Saving)
- Changing items in locker and all skins (changing skins does not work in ch2)
- Changing banner icon and banner color
- Changing item edit styles
- Favoriting items
- Marking items as seen
- Managing friends (e.g. adding friends)
### XMPP Features
- Parties (builds 3.5 to 14.50)
- Chat (whispering, global chat, party chat)
- Friends
