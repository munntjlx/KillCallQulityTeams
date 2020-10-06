# KillCallQulityTeams
How to kill the quality call analytics in teams on MAC. This repo mainly consists of a settings.json file that needs to be placed in your Library in your homedir. It gets rid of the !@#@#$%@##$%^ "How was the call quality" thing in teams which m$ refuses to disable.

## Procedure

First go to the teams directory where the settings.json is stored.  I like to cat the evil messy json into jq (very nice pretty printer of json). MAKE SURE TEAMS IS OFF!

```bash
cd "~/Library/Application Support/Microsoft/Teams"
vi settings.json
cat settings.json | jq > settings.json.new
vi settings.json.new
```

The next parts are very annoying. You will need to go and change every occurrence of 'telemetry' keys to 'false'. There are like 91+ of them. Save the file, backup your old settings.json, and copy your new settings.json over the old one. I would like to put my settings.json file here but it looks like there are confidential things in it so I can't.

## Other things to do

I make settings.json "unchangeable on the Mac'

```shell
chflags uchg ./settings.json
sudo vi /etc/hosts
```

This will make your settings.json unchangeable. Also make sure teams IS NOT running when you copy things over.  The second command will edit the hosts file. I like to black hole telemetry.microsoft.com to localhost. This makes things really airtight (I could go so far as to block all traffic on the firewall but this is corporate so I don't)

Start up teams and NO MORE TELEMETRY. I also make the *settings.json.___ thing immutable as well just for insurance.
