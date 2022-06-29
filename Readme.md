# Github Action Example

## Pipeline


Here is the List of pipeline file example which has some basic experimentation.

- Master pipeline
- Sandbox piepleine


- ✨Semantic pipeline ✨
- Slack Notfication

## Master pipeline

- Trigger the master pipeline on push and pullrequest merge on ** Master **
- Runing the basic Shell Command to check the shell scripts

## Sandbox piepleine

- Trigger the sandbox pipeline on push and pullrequest merge of ** Sandbox **
- Runing the basic Shell Command to check the shell scripts

## Semantic Versioning

- Checking the Automation of the version handling to test the basic version on the tagging and automaticaly incrementing the version
- This might help to get Automatiing the version tagging and other usual stuff its uses enviroment variable

## Slack Notfication

* [Create a Slack App][apps] for your workspace (alternatively use an existing app you have already created and installed).
* Add the [`chat.write`](https://api.slack.com/scopes/chat:write) bot scope under **OAuth & Permissions**.
* Install the app to your workspace.
* Copy the app's Bot Token from the **OAuth & Permissions** page and [add it as a secret in your repo settings][repo-secret] named `SLACK_BOT_TOKEN`.
* Invite the bot user: how to invite a Bot to the channel. Way that was proposed by Caleb and Keet was not clear for me or not working. From my side, 'invite' work after

> open channel
> in Details tab, choose a 'More'clause
> in dropdown menu, chouse an 'add app'in pop-up look for you app (bot)
> Also i was use Bot User OAuth Access Token, because i need this functionality in private channel (additionaly, you should add for bot groups:history scope)

Add this Action as a [step][job-step] to your project's GitHub Action Workflow file:

```yaml
- name: Post to a Slack channel
  id: slack
  uses: slackapi/slack-github-action@v1.19.0
  with:
    # Slack channel id, channel name, or user id to post message.
    # See also: https://api.slack.com/methods/chat.postMessage#channels
    channel-id: 'CHANNEL_ID'
    # For posting a simple plain text message
    slack-message: "GitHub build result: ${{ job.status }}\n${{ github.event.pull_request.html_url || github.event.head_commit.url }}"
  env:
    SLACK_BOT_TOKEN: ${{ secrets.SLACK_BOT_TOKEN }}
