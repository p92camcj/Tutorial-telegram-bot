
How to create a Telegram Bot using only a Chromebook.

By Julio Camacho [@p92camcj](mailto:p92camcj@gmail.com)

14 August, 2015

----------

How to create a Telegram Bot using only a Chromebook.
===================

This tutorial helps you to create a new Telegram [^1] bot[^2] using only a Chromebook PC[^3] or a web browser (Google Chrome). We are going to use the tool Codenvy[^4], Google App Engine[^5] and a [Python Telegram Bot](https://github.com/leandrotoledo/python-telegram-bot)

I have to thank [Leandro Toledo](https://github.com/leandrotoledo/) for having helped me in this process.

Thanks to [Yukuku](https://github.com/yukuku/) for doing the tutorial that I followed and which I have used to do this one.

----------

Now, knowing which will be our tools, go on!

1. Message @botfather https://telegram.me/botfather with the following text: `/newbot`
   If you don't know how to message by username, click the search field on your Telegram app and type `@botfather`. You should be able to initiate a conversation. Be careful not to send it to the wrong contact, because some users has similar usernames to `botfather`.
   
   ![botfather initial conversation](http://i.imgur.com/pGOtOcj.png)

2. @botfather replies with `Alright, a new bot. How are we going to call it? Please choose a name for your bot.`

3. Type whatever name you want for your bot.

4. @botfather replies with `Good. Now let's choose a username for your bot. It must end in `bot`. Like this, for example: TetrisBot or tetris_bot.`

5. Type whatever username you want for your bot, minimum 5 characters, and must end with `bot`. For example: `whateversamplebot` 

6. @botfather replies with:

    Done! Congratulations on your new bot. You will find it at telegram.me/whateversamplebot. You can now add a description, about section and profile picture for your bot, see /help for a list of commands.

    Use this token to access the HTTP API:
    <b>123456789:AAG90e14-0f8-40183D-18491dDE</b>

    For a description of the Bot API, see this page: https://core.telegram.org/bots/api
    
7. Note down the 'token' mentioned above.

8. Type `/setprivacy` to @botfather.

   ![botfather later conversation](http://i.imgur.com/ZrRdaa0.png)

9. @botfather replies with `Choose a bot to change group messages settings.`

10. Type `@whateversamplebot` (change to the username you set at step 5 above, but start it with `@`)

11. @botfather replies with

    'Enable' - your bot will only receive messages that either start with the '/' symbol or mention the bot by username.
    'Disable' - your bot will receive all messages that people send to groups.
    Current status is: ENABLED
    
12. Type `Disable` to let your bot receive all messages sent to a group. This step is up to you actually.

13. @botfather replies with `Success! The new status is: DISABLED. /help`

14. Go to https://console.developers.google.com/project

15. Click `Create Project` 

16. Type whatever name you want for the project. For example: `tutorial telegram bot p92camcj`. Make sure the Project ID is also the same.![Creation Tutorial Telegram Bot p92camcj](https://lh4.googleusercontent.com/W02O10AeDahFG6LqeROkgO2aymJnC-plu6p6rXT7hI9_IrK0f-8RB6mKpaa4tf36T3W4VqVl84FG6pg=w1342-h513)

17. Create an account in [Codenvy.com](https://codenvy.com)

18. Create a new project. Using `blank` option, type the name and description of your project and press `next`.![enter image description here](https://lh5.googleusercontent.com/M9rzGaO8FeibmXpoTSKaih69LhIjLD4g0LWHvpAjBmdrfRN6m07O5x3aEIYycmOPi-BGrSp9QEi-vCg=w1342-h513 "Create new Codenvy Project")

19. This step is very important. In the `Select Runner environment` you have to choose `Python/web/python27_gae1914_ext_libs`. Then press `Create`.![enter image description here](https://lh3.googleusercontent.com/FEYf9dtCi5LPGI3_BgaeE_FGEmqhSrYNScT8pGBZkFlZD07-FUs9-QDb4p0dMUoSOQjqAgwfOqV4tgg=w1342-h513 "Select Runner environment")

20. Now you have to download a `test bot`. I have created one to do this tutorial. You can [use it](https://github.com/p92camcj/Tutorial-telegram-bot). 

21. Next step is Upload Folder from a zip, go to `menu/file/upload folder from zip` like appear in this image![enter image description here](https://lh6.googleusercontent.com/rdbk7I2S-nA9I78auqlS52rloLp9OryvOm8D2abThVKhOFdycEYB7Xdol1hDAn-jd-FpQwLObD9nx7w=w1342-h513 "Import folder from zip")

21. Select the test bot zip and upload it.

22. Edit the first line of `app.yaml` file and type your Google App Engine project ID (step 16).  ![enter image description here](https://lh4.googleusercontent.com/7VasLUL0LFKNC58O12hEvXgVavD8KoB7A4-OcvU2k9sQUpG7UHsw6840N7xPxZmKwCuQMlCQ8QKQ2-Y=w1342-h513-rw "Modify app.yaml")

23. After that, you have to modify bot_gae.py file, in lines 13 and 32. ![enter image description here](https://lh3.googleusercontent.com/Hab4vuAWdftS8pmFryoGPaN5aZwnpNU9tAT2P40tlvTdXr-whR-p6J7N9_QfemYt8nom8TG0RmcCtWk=w1342-h513-rw "Modify bot_gae.py") 
>- Line 13 should be edited to include your token bot (BotFather gave you in step 1)  
`bot = telegram.Bot(token='114313687:AAFbt4jveB_hhT-UhMBO1vnjZNruS0Mg1Z4')`
>- Line 32 should be edited to include your ID project from GAE (Google App Engine)
`    s = bot.setWebhook('https://tutorial-telegram-bot-p92camcj.appspot.com/HOOK')`

24. Now everything are ready to work, so `Run` your project using the menu and submenu option.
![enter image description here](https://lh3.googleusercontent.com/eD-ufk3pI5bVgV9OK3HmnlHUDnwFsMgDCCfjiINoTpZYyKhmGA8pTt8-y2qnhJwwIlC-xTUCNPjqP8Y=w1342-h513 "Run Project")
25. You must see a `runner panel` below, you have to wait until all proccess have finished, and then open the `terminal` tab (near `console` active tab) 
![enter link description here](https://lh4.googleusercontent.com/wN2WgB8VcZeXcaLoY-WfoZvep5Jq8Prjfc-7S8ZhEBpXz1PX5NZLtCKuoTmI0SK8qYYuDisDvvcT--8=w1342-h513-rw "Console tab in runner panel")
26. Finally, you have to deploy it typing next command line on the `terminal`: `google_appengine/appcfg.py update /home/user/application/`. It ask for you your Google Account credential (email and pass), so you have to ingress them.
27. If you have had some problems with the previous step and Google sends you an email about your security account, try the next method. Type the next command line on the `terminal`: `google_appengine/appcfg.py update /home/user/application --oauth2 --noauth_local_webserver`. It will print a link. Copy the code and return to terminal codenvy. Right-click on the terminal, select Paste from Browser and paste the code. Be happy :) ![enter image description here](https://lh4.googleusercontent.com/lQMeneNDCQtwYNGY0YsZk23A4co_3jZSGE4T2x0SmB8kdgOX4FYNgFdD8zMex1S3mwJjJiJO0gvWCSg=w1342-h513-rw "Problems Google?")
28. Now, try to navegate to [https://tutorial-telegram-bot-p92camcj.appspot.com/set_webhook](https://tutorial-telegram-bot-p92camcj.appspot.com/set_webhook) and if all is correct, you must read "`webhook setup ok`"
29. Now you speak to your bot in telegram, and if it repeats like a parrot everything you write, you will have successfully completed this tutorial. ![enter image description here](https://drive.google.com/file/d/0B05KqB61aXlWQjkxR3BYZzUxQkk "Like a Parrot")



[^1]: Telegram is a cloud-based mobile and desktop messaging app with a focus on security and speed. More info: [telegram.org](http://telegram.org/).

[^2]: Bots are simply Telegram accounts operated by software – not people – and they'll often have AI features. They can do anything – teach, play, search, broadcast, remind, connect, integrate with other services, or even pass commands to the Internet of Things. [More info in his blog](https://telegram.org/blog/bot-revolution).

[^3]: A Chromebook is a laptop running Chrome OS as its operating system. The devices are designed to be used primarily while connected to the Internet, with most applications and data residing "in the cloud". A Chromebook is an example of a thin client. More info: [google.com/chromebook](https://www.google.com/chromebook/)

[^4]: Codenvy provides a container-based development environment whose goal is to remove the need for developers to configure or maintain local or VM-based developer environments for their projects. More info: [codenvy.com](http://www.codenvy.com/)

[^5]: Google App Engine (often referred to as GAE or simply App Engine) is a platform as a service (PaaS) cloud computing platform for developing and hosting web applications in Google-managed data centers. 
