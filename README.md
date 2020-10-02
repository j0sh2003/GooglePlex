# GooglePlex
Cast movies and TV from Plex using Google Assistant with Chromecast

## Pre-requisites:
* .NET Framework 4.7.2 Runtime: https://dotnet.microsoft.com/download/dotnet-framework/net472
* IIS (Internet Information Services) Manager
	1. Open "Turn Windows Features On or Off" in Windows
	2. Locate Internet Information Services and enable it.
* A free IFTTT acount: https://ifttt.com
* Port forwarding enabled at router level
* Any applicable firewall rules
* Your Plex Token (see instructions here: https://support.plex.tv/articles/204059436-finding-an-authentication-token-x-plex-token/)

## Installation:
1. Download this file as a ZIP and save it to C:\inetpub\wwwroot\GooglePlex (or similar).
2. Setup the site in IIS
	* Open IIS
	* Right click "Sites" and click "Add Website"
	* Enter C:\inetpub\wwwroot\GooglePlex (or similar) in the Physical path field
	* Use DefaultAppPool Application pool unless you know what you're doing
	* Test your connection, and click OK
3. Open the local GooglePlex website (e.g. http://localhost:80)
4. Enter your Plex server's IP address (including port) and Plex Token.  Save.
5. Create an IFTTT applet
	* After logging into IFTTT, navigate to https://ifttt.com/create/
	* Click "If This"
	* Find and click "Google Assistant" (connect your Google account if necessary)
	* Click "Say a phrase with a text ingredient"
	* In the "What do you want to say?" type "Plex Play $" or similar
	* Fill in the other fields accordingly, and click "Create trigger"
	* Click "Then That"
	* Find and click "Webhooks"
	* Click "Make a web request"
	* Enter "http://xxx/api/play?cmd={{TextField}}" where xxx is your PUBLIC IP address (and port if necessary)
	* Click "Create action"
	* Click "Continue" and complete the remaining steps to save your webhook

## Usage
- Logs
	- Logs will show the timestamp of any command which failed at the API level, as well as the exception message related to the failure
- Substitutions
	- Substitutions will allow you to substitute a particular word or phrase with another, such as the examples below:
		- Happiness > Happyness
		- Creep Show > Creepshow
		- Series > Season
- Specify video type
	- You can now begin your command with "Movie" or "Show" to differentiate.  For instance, to play the Show "War of the Worlds" and not the movie with the same title, you can tell the Google Assistant "\[Tell Plex to Play\] Show War of the Worlds \[on Living Room TV\]", where the speech in brackets may vary based on your setup.

## YouTube Video
[![Alt text](https://img.youtube.com/vi/8f3mzAZ12Mo/0.jpg)](https://youtu.be/8f3mzAZ12Mo)
