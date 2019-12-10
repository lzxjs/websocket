# 在Vue中的使用教程
公司即时推送消息用的websocket前端demo

如果只是需要使用即时接收，只需要在你的代码中引入如下代码块

```
在vue项目中（其它的环境其实也大致相同）
methods: {
    websock() {
      var websocket = null;
      if ("WebSocket" in window) {
        websocket = new 			
        WebSocket("ws://192.168.100.213:8092/websocket/233");
      }
      websocket.onmessage = this.onMessage;
      websocket.onclose = this.setOncloseMessage
    },
    onMessage(e) {
      this.msg = JSON.parse(e.data);
      this.$notify({
        title: "新消息到啦！",
        message: this.msg.content,
        position: "bottom-right",
        duration: 1500
      });
    }
}
```

