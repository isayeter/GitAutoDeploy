This python script is not coded by me, I couldn't find the original one, so I'm not able to give credits to person who code this.

**In this version, if you write "donotpull" to commit message, auto deploy will not fetch the source.**


## INSTALLATION

Open GitAutoDeploy.conf.json and fill all the necessary fields.


key | value
--- | ---
[LOCAL_IP] | 199.199.199.199 (Your server ip address)
[LOCAL_PORT_TO_LISTEN] | 3434 (You will write ip and port address to Webhook in Gitlab etc.)
[GIT_REPO_URL] | http://blabla.com/bla.git
[BRANCH_NAME_TO_PULL] | Like: "development" , "master"
[REMOTE_NAME] | Like: "development" , "master"
[PROJECT_FOLDER] | "/var/www/html/bla.com/"
[AFTER_COMMANDS] | Like: "cd /var/www/html/bla.com/ && ./vendor/bin/db_migrate migrate"

## START IT

In daemon mode:

```
/usr/bin/python /blabla/GitAutoDeploy.py --config /blabla/GitAutoDeploy.conf.json --daemon-mode --quiet
```

In foreground: (to see logs)

```
/usr/bin/python /blabla/GitAutoDeploy.py --config /blabla/GitAutoDeploy.conf.json
```


## ADD TO STARTUP

```
crontab -e
```

Write this:

```
@reboot /usr/bin/python /blabla/GitAutoDeploy.py --config /blabla/GitAutoDeploy.conf.json --daemon-mode --quiet
```


## ADD WEBHOOK IN GITLAB PROJECT SETTING'S AREA


![alt text](http://i.imgur.com/bfDf72C.png "Webhook in GitLab")



go to your folder on the server
git init
git remote add origin .
git pull master master
