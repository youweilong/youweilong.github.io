<!DOCTYPE html>
<html>
  <head>
    <title>情侣生活记录</title>
  </head>
  <body>
    <h1>情侣生活记录</h1>
    <form>
      <label>日期：</label>
      <input type="text" id="date">
      <br>
      <label>事件：</label>
      <input type="text" id="event">
      <br>
      <button type="button" onclick="addRecord()">添加记录</button>
    </form>
    <ul id="records"></ul>
    <script>
      // 从本地存储中读取记录
      var records = JSON.parse(localStorage.getItem("records")) || [];

      // 获取表单元素
      var dateInput = document.getElementById("date");
      var eventInput = document.getElementById("event");
      var recordsList = document.getElementById("records");

      // 渲染记录列表
      function renderRecords() {
        recordsList.innerHTML = "";
        for (var i = 0; i < records.length; i++) {
          var recordItem = document.createElement("li");
          recordItem.textContent = records[i].date + "：" + records[i].event;
          recordsList.appendChild(recordItem);
        }
      }

      // 添加记录函数
      function addRecord() {
        // 获取输入的日期和事件
        var date = dateInput.value;
        var event = eventInput.value;

        // 将记录添加到数组中
        records.push({
          date: date,
          event: event
        });

        // 保存记录到本地存储
        localStorage.setItem("records", JSON.stringify(records));

        // 渲染记录列表
        renderRecords();

        // 清空表单
        dateInput.value = "";
        eventInput.value = "";
      }

      // 初始化页面，渲染记录列表
      renderRecords();
    </script>
  </body>
</html>
