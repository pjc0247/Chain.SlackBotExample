# Chain.SlackBotExample
SlackBotExample w/ Chain

```cs
Config.Set("slack.team", "rinirinihino");
Config.Set("slack.access_token", "ACCESS_TOKEN");

var slackSource = C.EventSource<SlackMessage>();
  
slackSource
  .Filter<MessageRegex>("^Hello")
  .Task<SlackSendMessage>("hi there");
  
slackSource
  .Filter<MessageRegex>("^!Random$")
  .Task<SlackSendMessage>(
      C.Rstr("random number -> {0}", () => {
        return (new Random()).Next();
      });
```
