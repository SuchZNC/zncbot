# SuchZNC - ZNC Bot
A ZNC bot capable of handling registeration requests of new ZNC accounts, and more.

## Features
* The ability to request for a ZNC account (!request)
* The ability to approve or deny new ZNC account requests (!approve or !deny)
* A complete, email-less, system. Instead of requiring a provided email to signup, the system works by setting new users' bindhost to 8.8.8.8, to prevent them connecting, until an admin approves.
* The ability to delete ZNC accounts in the IRC channel.
* Muti-language support, including the ability to set the specified language for each indiviual user (!userlang for indiviual language)

## Setup requirements
* Python 3.6 or newer (ANYTHING OLDER THAN PYTHON 3.6 WILL NOT WORK)
* Administrator access to a functional ZNC server
* Make sure to create a "cloneuser" account, this account will be used for the bot to clone for each new user, that way, you can specify certain stuff for each new user, like a custom realname, or quit message, or whatever the case may be.
* Make sure every ZNC user have "DenySetBindHost" enabled, otherwise approving would be useless.
* Make sure the ZNC bot have Admin privileges on the ZNC server (Duh)
* In order for the bot to even work...at all, it requires the controlpanel module to be enabled. This will be used to basically do everything it needs to do, like create new accounts, set bindhosts, etc.

## List of admin commands, and what they do
**!approve** - Approves the specified ZNC username; This will set their bindhost to the proper bindhost in the config, and allow them to connect to their IRC networks.
<br>
**!deny** - Denies the request of a ZNC username; Once denied, this will instantly delete their ZNC account.
<br>
**!userinfo** - Lists the information about the ZNC user, usually information about registeration, including when did they register, what host did they use, etc.
<br>
**!deluser** - Deletes the ZNC user from the bot's database, as well from the ZNC server.
<br>
**!adduser** - Manually adds the ZNC username to the bot's database; Useful if you created an account on the ZNC server, and not through !request, and prevents from other users to request that username.
<br>
**!restart** - This will restart the bot. (Note: Sometimes, this *might* fail, for some reason, and requires you start the bot manually again.)
<br>
**!timereset** - If ZNC username is specified, it will reset the request timer using the last known host that was used by the user. If the host was specified instead, it will reset the request timer for the specified host.

## Configuration help
**zncuser** - The username of the ZNC account for the bot to use.
<br>
**server** - The ZNC server the bot will be connecting to.
<br>
**port** - The IRC port the ZNC server is using (Add a + for SSL, something like +6697, as an example.)
<br>
**admins** - The list of user@host that are granted admin privileges on the bot, such as ["example@foobar.net", "quack@ducks.net"]
<br>
**network** - Used for specifying which network will the bot use, when it authenticates itself to the ZNC.
<br>
**zncpass** - The ZNC Bot's account password.
<br>
**language** - The default language the bot will speak in, on IRC. (Enter "en" for English, LOOKING FOR TRANSLATORS FOR MORE LANGUAGES)
<br>
**webpanel** - Where the ZNC webpanel is located, so they will know when they request for an account.
<br>
**znchost** - The ZNC bindhost to set when the user gets approved, set it to an asterisk if you don't have a specific IP or host to use, or if you are not sure.
<br>
**torhs** - The ZNC's Tor Hidden Service Address, leave blank if you don't have one.
<br>
**zncircserver** - The ZNC address your users will connect to, this will be given to them when they register.
<br>
**zncssl** - The SSL IRC port for ZNC, incase you have a configuration where you splitted the SSL and non-SSL ports (like how 6667 isn't SSL, but 6697 is), otherwise, leave blank.
<br>
**zncstandard** - Same thing as the zncssl config, but this time, for the standard ZNC irc port, without SSL. If you left zncssl blank, then you probably should have this blank too.
<br>
**zncircport** - The ZNC IRC port that your users will be using, do not use this if you have SSL and non-SSL seperated, but instead, instead use zncssl and zncstandard.
<br>
**zncircportisssl** - States if the port supports SSL connections, Put in "True" if so, "False" if not (Make sure you keep the quotes with it too.)
<br>
**use_identify-msg** - (Requires the IRC network to support it, and the bot to have send_raw module enabled) If set to "True" (Including the quotes), the bot will require users to be identified to services.

**reqchan** - Specifies the channel the bot will be using to receive ZNC requests.

**disableapproval** - (NOT RECOMMENDED TO ENABLE, UNLESS YOU HAVE SOMETHING ELSE TO REPLACE THIS) Disables the requirement for an account to be approved. Set to "True" if you really need to disable it, but it's best to leave it to "False".

**znchostmasks** - A list of hostmasks that your ZNC service will use on IRC. Prevents ZNC users from re-requesting another account. Use * for wildcards.

**linktotos** - A link to your ToS, this gets shown to those who requests an account. If you don't have one, then leave blank.

## Roadmap/To-do List (Always looking for contributors and help!)
* Create a pending command, which would list accounts that are still "pending" or waiting for their account to be approved or denied.
* A better online/offline tracker, this is useful to check if a user is online or connected to their account, in !userinfo.
* MORE LANGUAGES! (Including replacing the poorly translated spanish version.)

## Still need help? Need to contact?
Join the IRC channel #SuchZNC @ freenode for help, bug reporting, or contributions, or whatever the case may be.
