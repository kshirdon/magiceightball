# Lab - Watson Conversation Service

## Architecture
Below is the architecture overview of the Watson Conversation (WCS) Lab.  This architecture
is consistent with the reference implementations of WCS for cloud native applications using microservices.
![Architecture Overview](/images/wk2-arch-overview.png)


## Application Overview
This lab is intended to help you understand the basics of the Watson Conversation Service (WCS)
as part of the Watson API's. WCS is a question and answer system that focuses on providing
a dialog type of experience between the user and the conversation system. This style of interaction
is commonly called a bot.  Though the example is simple, it will provide you with a
solid understanding of the core pieces of WCS.

### Terminology
WCS has a couple of terms that need to be understood. This will allow for an easier time with
creating an application (i.e. Dialog) in WCS

**Intent:** An intent is the intention of the command or question given by the user to WCS.
	It is common to think of intents as the verbs or actions that need to occur. An Example of
	an Intent is "Tell me the temperature" or "I want to know the current temperature". In both
	cases, though the sentences are different they both as asking WCS for temperature information.
	It should be noted that WCS can only support a single Intent per interaction with WCS. So
	asking questions with multiple intents will produce unreliable ordering of answers to the question.

**Entities:** An entity is the object that intents use to help narrow the scope of the request.
	It is common to think of entities as nouns or objects. The nice thing about entities, compared to
	intents, is that you can have multiple entities per interaction. This is very helpful when trying
	to narrow down the answers to a question.

**Dialog:** The conversation that is created within WCS, is called a dialog. A dialog is
	composed of creating a flow between intents and entities. The combination of flows and
	subFlows allows WCS to provide mult-layered conversation based on multiple interactions,
	instead of a single question and answer.


## Create Watson Conversation Service

1. Logon to BlueMix and go to your dashboard
2. Create a new space for the services and applications you are using in this lab.  Click on your name then create space.

![Architecture Overview](/images/basicWCS_createspace.png)

3. Call the space basicWCSLab and click Create
4. Click on the catalog button at the top navigation on the right
5. Select "Watson" on the left navigation under the Services menu
4. Click on "Conversation"

![Architecture Overview](/images/basicWCS_catalog.png)	 

5. In the service name basicWCSlab-WCSservice.  You can leave credential name as is, if you like.
6. Click on the create in the lower right corner. You should now see the following

![Architecture Overview](/images/basicWCS_manage.png)

7. You will need to cut and paste your service credentials. Click on "Service Credentials"
on the left navigation, right under "Manage". Once the page has loaded, click on "View Credentials" on the right side of the screen.
A drop down will show with your specific credentials

![Architecture Overview](/images/basicWCS_credentials.png)
Your values for username and password will be different than shown.

8. Click the copy icon to copy the values to your clipboard. Paste the values in a text file for later use. Make sure you get both:

- username
- password

9. Go back to the manage page, by clicking on the manage link on the left side navigation. This will take you back to the manage page.

You have now completed the first step in creating the WCS service instance.

## Launch WCS tooling
1. Click on the "Launch tool" icon to take you to the WCS workspace

![Architecture Overview](/images/basicWCS_manage_launch.png)

2. This will open another browser window and you should now be on the Watson Conversation Workspace page

![Architecture Overview](/images/basicWCS_workspaces.png)

3. You are going to create a new workspace. Click on the ***"Create a new workspace"*** tile.
4. Enter a workspace name i.e. basicWCS_WCSworkspace.

![Architecture Overview](/images/basicWCS_workspaces_create_popup.png)


5. Click the last icon (Back to workspaces) on the left navigation. It should look like

![Architecture Overview](/images/basicWCS_conversation_workspaces_small.png)

or

![Architecture Overview](/images/basicWCS_conversation_workspaces_large.png)

You should now see:

![Architecture Overview](/images/basicWCS_workspaces_dash.png)

6. Click on the **three green buttons** in the upper right corner of your workspace tile.

![Architecture Overview](/images/basicWCS_workspace_tile.png)

You should now see

![Architecture Overview](/images/basicWCS_workspace_tile_submenu.png)

7. Click **View Details**. You should now see something like the following

![Architecture Overview](/images/basicWCS_workspace_tile_viewdetails.png)

8. Copy the **Workplace ID** and paste it somewhere for use later.

9. Click on the **White Back Arrow** in the upper corner of the tile.

![Architecture Overview](/images/basicWCS_workspace_detail_convid.png)

10. Click **Get Started** or anywhere in the tile, to get started.

![Architecture Overview](/images/basicWCS_workspace_tile_getstarted.png)

## Create Intents
You are now ready to create some **Intents**. 

1.  Click on the Intents link. You should now see the following:

![Architecture Overview](/images/basicWCS_workspaces_create_intents.png)

Click the **"Create New"** button in the middle of the page. 

2. Add a new Intent name of **Greeting**.

![Architecture Overview](/images/basicWCS_intent_ex_information.png)


You then need to provide some examples. Copy the samples provided, one at a time, paste each into the tool.

```
good evening
Hello
Hi
Howdy
Good morning
Good afternoon
Yo Yo Yo
Sup dude
```
It should look like the following:

![Architecture Overview](/images/basicWCS_workspaces_intents_greeting.png)

Click **Done** in the upper right corner when finished.

![Architecture Overview](/images//images/basicWCS_workspaces_intents_greeting.png)

3. Add another intent **GoodBye**. Add the following examples also.

```
See ya later
see you later
Talk to you later
Later
Bye
Goodbye
Good-bye
```
![Architecture Overview](/images/basicWCS_workspaces_intents_goodbye.png)
Click **Done** when finished.

4. Add another intent **CanIAskAQuestion** with the following examples:

```
Can I ask a question?
Is it ok if I ask a question?
Are you taking questions?
May I ask a question?
Can you answer my question?

```

![Architecture Overview](/images/basicWCS_workspaces_intents_caniaskaquestion.png)
Click **Done** when finished.

5. Add another intent **AskAQuestion** with the following examples:

```
Will I
Will I lose
Will I win
Will I become a
Are we
Do you

```

![Architecture Overview](/images/basicWCS_workspaces_intents_askaquestion.png)
Click **Done** when finished.

6. Add another intent **Affirmative** with the following examples:

```
Yes
Yah
Absolutely
Sure
Yeah

```

![Architecture Overview](/images/basicWCS_workspaces_intents_affirmative.png)
Click **Done** when finished.

7. Add another intent **Negative** with the following examples:

```
Nah
Huh uh
Probably not
Doubtful
No Way
No
Nope

```

![Architecture Overview](/images/basicWCS_workspaces_intents_negative.png)
Click **Done** when finished.

8. Add one last intent **StateMood** with the following examples:

```
I feel sad
I feel
Irritated
I am feeling happy
I feel excited
Very excited
Excited
Happy
Sad
I am feeling sad
I feel happy

```
![Architecture Overview](/images/basicWCS_workspaces_intents_statemood.png)
Click **Done** when finished.

You have now finished creating all of the intents. (Nice Job!)

## Create Entities
Next we want to create some **Entities**. Click on the "Entities" link at the top of the page.

![Architecture Overview](/images/basicWCS_workspaces_entities-add.png)

1. Click the **"Create New"** button.
2. Type **"Moods"** as the new Entity name.


Now notice, you need to add examples of new "VacationType" entities. So add **"Happy"** as a new entity
but also you need to provide some synonyms to help identify variations of the entity value. Now add **"fantastic"** **great** **wonderful** **peachy**
as a synonyms. You now need to add **"adventure"** and **"spa"** with the corresponding
 synonyms, as shown in the image above. When you add a synonym, hit the **Enter** key from your keyboard to add the next synonym. After you are finished with each set of synonyms click the **Plus** icon to add them.

```
happy				great	fabulous	
sad					bad		horrible	depressed
excited			psyched	thrilled	pumped

```
![Architecture Overview](/images/basicWCS_workspaces-entities-moods.png)

If for some reason you accidentally don't add one of the synonyms, you can add it after you click the done button. You just select the entity and add the appropriate synonyms.

Click **Done** when finished.


Great you now completed the adding of the required entity. (Well done!).

## Create a Dialog
We are now ready to create a dialog. 

1.  Click on the Dialog link at the top of the page.

![Architecture Overview](/images/basicWCS_workspaces-dialog-add.png)

2. Click the **"Create"** button to start to create a dialog. You should now see the following:

![Architecture Overview](/images/basicWCS_workspaces-dialog-start.png)

What you see are two "Dialog Nodes". The first is the standard "Welcome" message and the other
is a catch-all "Anything else" . Remember the way a conversation dialog works is by scanning from the top of the tree
and evaluating every node until a condition is met that satisfies the question being asked. So when the conversation starts
WCS will respond with the "Welcome" Node. If you click on the "Welcome" node you will see that the standard Watson response
is "Hello. How can I help you?" - change that response to:

```
Hello.  Welcome to the Amazing Magical Eight Ball.  How can I help you today?

``` 
![Architecture Overview](/images/basicWCS_workspaces-dialog-click-welcome.png)

Click the green X.

3. We now want to create our own node, based on the "Intents" we create earlier. To add a new node in the tree, click on the "Welcome"
node,  and then click on the **"Add Node"** icon.

![Architecture Overview](/images/basicWCS_workspaces-dialog-newnode.png)

4. Type **Greetings** as the name of the node. If bot recognize should be **"#Greeting"**. The Response condition should be set to "True", by clicking on the **Add response condition** button. Provide the following text.

```
Hello.  Welcome to the Amazing Magical Eight Ball.  How can I help you today?

```

It should look similar to the following:

![Architecture Overview](/images/basicWCS_workspaces-dialog-node-greeting.png)

You can click the **green X** in the upper right to close the dialog node editor.

5. Again create another root node by clicking on the **"Greeting"** node and then clicking **"Add node"**. This will add another node. This node's values are as follows:

![Architecture Overview](/images/basicWCS_workspaces-dialog-node-setmood.png)

You can click the **green X** in the upper right to close the dialog node editor.

6. Again create another root node by clicking on the **"Greeting"** node and then clicking **"Add node"**. This will add another node. This node's values are as follows:

![Architecture Overview](/images/basicWCS_workspaces-dialog-node-showcompassion1.png)
![Architecture Overview](/images/basicWCS_workspaces-dialog-node-showcompassion2.png)

You can click the **green X** in the upper right to close the dialog node editor.

7. Create a new node under the **"Greeting"** node, called **Answer a Question**. Copy and paste the possible responses from the following:

```
As I see it, yes
Ask again later
Better not tell you now
Cannot predict now
Concentrate and ask again
Don’t count on it
It is certain
It is decidedly so
Most likely
My reply is no
My sources say no
Outlook good
Outlook not so good
Reply hazy, try again
Signs point to yes
Very doubtful
Without a doubt
Yes    
Yes, definitely
You may rely on it
```

![Architecture Overview](/images/basicWCS_workspaces-dialog-node-answeraquestion1.png)

![Architecture Overview](/images/basicWCS_workspaces-dialog-node-answeraquestion2.png)

8. Create a node under by clicking on **"Greeting"** called **Ask Another Question**, with the following information:

![Architecture Overview](/images/basicWCS_workspaces-dialog-node-askanotherquestion.png)

At this point your Dialog Tree should look like the following

![Architecture Overview](/images/basicWCS-dialog-tree.png)

9.  Click on the **Answer a Question** Node.  Scroll to the bottom and select **Jump to**

![Architecture Overview](/images/basicWCS-jumptoaskanother.png)

Then click on the **Ask another question** node.

10.  Next click on the **Ask another question** node then click **Add child node**.  Set up the node as follows:

![Architecture Overview](/images/basicWCS-yesanotherquestion.png)

11.  Again, click on the **Ask another question** node then click **Add child node**.  Set up the node as follows:

![Architecture Overview](/images/basicWCS-nomorequestions.png)

We are now finished with the entire Dialog. Congratulations! Now is time to test your code.# magiceightball
