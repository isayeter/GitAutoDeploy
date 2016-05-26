This python script is not coded by me, I couldn't find the original one, so I'm not able to give credits to person who code this.

In this version, if you write "donotpull" to commit message, auto deploy will not fetch the source.


# INSTALLATION

Open GitAutoDeploy.conf.json and fill all the necessary fields.


key | value
--- | ---
[LOCAL_IP] | 199.199.199.199 (Your server ip address)
[LOCAL_PORT_TO_LISTEN] | 3434 (You will write ip and port address to Webhook in Gitlab etc.)
[GIT_REPO_URL] | http://blabla.com/bla.git
[BRANCH_NAME_TO_PULL] | like "development" , "master"
[PROJECT_FOLDER] | "/var/www/html/bla.com/"
[COMMANDS_TO_BE_EXECUTED_AFTER_DEPLOYMENT] | Like: "cd /var/www/html/bla.com/ && ./vendor/bin/db_migrate migrate"

# START IT

```
/usr/bin/python /blabla/GitAutoDeploy.py --config /blabla/GitAutoDeploy.conf.json --daemon-mode --quiet
```


#  Add script to crontab

```
crontab -e
```

Write this:

```
@reboot /usr/bin/python /blabla/GitAutoDeploy.py --config /blabla/GitAutoDeploy.conf.json --daemon-mode --quiet
```