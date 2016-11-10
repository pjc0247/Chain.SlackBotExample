# Chain.SlackBotExample
SlackBotExample w/ Chain

```cs
Config.Set("slack.team", "rinirinihino");
Config.Set("slack.access_token", "ACCESS_TOKEN");
```
```cs
var slackSource = C.EventSource<SlackMessage>();
 
// 안녕로봇
slackSource
  .Filter<MessageRegex>("^Hello")
  .Task<SlackSendMessage>("hi there");
  
// 랜덤 넘버 생성
slackSource
  .Filter<MessageRegex>("^!Random$")
  .Task<SlackSendMessage>(
      C.Rstr("random number -> {0}", () => {
        return (new Random()).Next();
      });
```
