
How to create a Telegram Bot using only a Chromebook.

By Julio Camacho [@p92camcj](mailto:p92camcj@gmail.com)

14 August, 2015

----------

How to create a Telegram Bot using only a Chromebook.
===================

This tutorial helps you to create a new Telegram<sup>[1](#^1)</sup> bot<sup>[2](#^2)</sup> using only a Chromebook PC<sup>[3](#^3)</sup> or a web browser (Google Chrome). We are going to use the tool Codenvy<sup>[4](#^4)</sup>, Google App Engine<sup>[5](#^5)</sup> and a [Python Telegram Bot](https://github.com/leandrotoledo/python-telegram-bot)

I have to thank [Leandro Toledo](https://github.com/leandrotoledo/) for having helped me in this process.

Thanks to [Yukuku](https://github.com/yukuku/) for doing the tutorial that I followed and which I have used to do this one.

Thanks to [Soo Y. Hwang](https://github.com/sooyhwang/Simple-Echo-Telegram-Bot) for let me use her code base.


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

16. Type whatever name you want for the project. For example: `tutorial telegram bot p92camcj`. Make sure the Project ID is also the same and **note down it**, this is YOUR GOOGLE APP ENGINE PROJECT ID. For exampl, my  Google App Project ID is *tutorial-telegram-bot-p92camcj*![Creation Tutorial Telegram Bot p92camcj](http://i.imgur.com/lbLUnWw.png "Creation Tutorial Telegram Bot p92camcj")

17. Create an account in [Codenvy.com](https://codenvy.com)

18. Create a new project. Using `blank` option, type the name and description of your project and press `next`.![Create new Codenvy Project](http://i.imgur.com/9WU7KNq.png "Create new Codenvy Project")

19. This step is very important. In the `Select Runner environment` you have to choose `Python/web/python27_gae1914_ext_libs`. Then press `Create`.![Select Runner environment](http://i.imgur.com/v42f6MP.png "Select Runner environment")

20. Now you have to import a `test bot`. I have created one to do this tutorial. You can [use it](https://github.com/p92camcj/Tutorial-telegram-bot). 

21. So go to `menu/file/Import Project/Import From Location...` like it appears in this image:![Import folder from location](http://i.imgur.com/ojUSTBz.png "Import folder location")

22. You have to choose in `Source Control` option `GitHub` and then paste this link on URL field like it appears in this image: ![Import from GitHub](http://i.imgur.com/x3VzbEC.png "Import from GitHub")

23. Edit the first line of `app.yaml` file and type **YOUR GOOGLE APP ENGINE PROJECT ID** (step 16).  ![Modify app.yaml](http://i.imgur.com/0sdImIh.png "Modify app.yaml")

24. After that, you have to modify bot_gae.py file, in lines 13 and 32. ![Modify bot_gae.py](http://i.imgur.com/Pqx9nYK.png "Modify bot_gae.py") 
>- Line 13 should be edited to include your token bot (BotFather gave you in step 1)  
`bot = telegram.Bot(token='114313687:AAFbt4jveB_hhT-UhMBO1vnjZNruS0Mg1Z4')`
>- Line 32 should be edited to include **YOUR GOOGLE APP ENGINE PROJECT ID**
`    s = bot.setWebhook('https://tutorial-telegram-bot-p92camcj.appspot.com/HOOK')`

25. Now everything is ready to work, so `Run` your project using the menu and submenu option.
![Run Project](http://i.imgur.com/Kta36qt.png "Run Project")
26. You must see a `runner panel` below, you have to wait until the whole proccess have finished, and then open the `terminal` tab (near `console` active tab)
![Console tab in runner panel](http://i.imgur.com/io3okP8.png "Console tab in runner panel")
27. Finally, you have to deploy it typing next command line on the `terminal`: `google_appengine/appcfg.py update /home/user/application/`. It will ask for your Google Account credential (email and pass), so you have to ingress them.
28. If you have had some problems with the previous step and Google sends you an email about your security account, try the next method. Type the next command line on the `terminal`: `google_appengine/appcfg.py update /home/user/application --oauth2 --noauth_local_webserver`. It will print a link. Copy the code and return to terminal codenvy. Right-click on the terminal, select Paste from Browser and paste the code. Be happy :) ![Problems Google?](http://i.imgur.com/lr9xRRT.png "Problems Google?")
29. Now, try to navegate to [https://tutorial-telegram-bot-p92camcj.appspot.com/set_webhook](https://tutorial-telegram-bot-p92camcj.appspot.com/set_webhook) and if all is correct, you must read "`webhook setup ok`"
30. Now you speak to your bot in telegram, and if it repeats like a parrot everything you write, you will have successfully completed this tutorial.

![Like a Parrot](http://i.imgur.com/sROL1xI.png "Like a Parrot")


----------


<a name="^1">1</a>: Telegram is a cloud-based mobile and desktop messaging app with a focus on security and speed. More info: [telegram.org](http://telegram.org/).

<a name="^2">2</a>:  Bots are simply Telegram accounts operated by software – not people – and they'll often have AI features. They can do anything – teach, play, search, broadcast, remind, connect, integrate with other services, or even pass commands to the Internet of Things. [More info in his blog](https://telegram.org/blog/bot-revolution).

<a name="^3">3</a>:  A Chromebook is a laptop running Chrome OS as its operating system. The devices are designed to be used primarily while connected to the Internet, with most applications and data residing "in the cloud". A Chromebook is an example of a thin client. More info: [google.com/chromebook](https://www.google.com/chromebook/)

<a name="^4">4</a>:  Codenvy provides a container-based development environment whose goal is to remove the need for developers to configure or maintain local or VM-based developer environments for their projects. More info: [codenvy.com](http://www.codenvy.com/)

<a name="^5">5</a>:  Google App Engine (often referred to as GAE or simply App Engine) is a platform as a service (PaaS) cloud computing platform for developing and hosting web applications in Google-managed data centers. More info: [appengine.google.com](https://appengine.google.com/)
