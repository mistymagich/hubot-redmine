# Hubot Redmine

Light mapping of the Redmine REST API that allows hubot access to some basic redmine tasks. Once you have a redmine
user (preferably one with enough access to modify tickets), add the following to your heroku/etc. config:

    heroku config:add HUBOT_REDMINE_BASE_URL="http://redmine.your-server.com"
    heroku config:add HUBOT_REDMINE_TOKEN="your api token here"

If using over SSL, add the following to your heroku config:

    heroku config:add HUBOT_REDMINE_SSL=1

![screenshot](https://github.com/robhurring/hubot-redmine/blob/master/ss.png?raw=true)

## Showing issue details

* Hubot show me [issue id]
* Hubot redmine me [issue id]

## Showing my issue (or another user's)

* Hubot show my issues
* Hubot show [user]'s issues
** [user] will attempt to match on redmine firstname or login

## Re-Assigning tickets

* Hubot assign [issue id] to [user]

## Leaving notes on tickets

* Hubot update [issue id] with "[comments]"

## Create tickets

* Hubot add issue to "[project]" [traker id] with "[subject]"
** [tracker id] is optional and represent the number matching literal value Bug/Feature/...

## Get a link to an issue

* Hubot link me [issue id]

## Set the percent done of an issue

* Hubot set [issue id] to 100% "[comments]"
* Hubot add [hours] hours to [issue id] "[comments]"

## Showing issue summary

* hubot #[issue id]
  
  response
    ```text
        #[issue id] (tracker name) subject
        issue url
    ```


## install

1. 自分のhubotを作成
    ```bash
        % hubot --create <path>
    ```

2. 移動
    ```bash
        % cd <above path>
    ```

3. package.jsonを編集 （すでにhubotを作成済みの場合はここから）

    ```bash
        "dependencies": {
          :
          :
          "hubot-redmine": "git://github.com/mistymagich/hubot-redmine.git"
        },
    ```

4. npm installしてインストール

5. external-scripts.jsonを編集

    ```json
        [
            "hubot-redmine/src/scripts/redmine.coffee"
        ]
    ```

6. hubotの起動スクリプトに環境変数を追加

    ```bash
        HUBOT_REDMINE_BASE_URL="REDMINEのURL"
        HUBOT_REDMINE_TOKEN="APIアクセスキー（redmine->「個人設定」の右側「APIアクセスキー」の値）"
    ```
