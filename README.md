<!DOCTYPE html>
<html>
<head>
	<title>情侣生活记录</title>
</head>
<body>
	<h1>情侣生活记录</h1>
	<form>
		<label for="date">日期：</label>
		<input type="date" id="date" name="date"><br>

		<label for="event">事件：</label>
		<textarea id="event" name="event"></textarea><br>

		<button type="button" onclick="addRecord()">添加记录</button>
	</form>

	<h2>历史记录</h2>
	<ul id="records">
		<!-- 历史记录会在这里动态添加 -->
	</ul>

	<script>
		// 定义一个记录数组
		var records = [];

		// 获取表单元素
		var dateInput = document.getElementById("date");
		var eventInput = document.getElementById("event");
		var recordsList = document.getElementById("records");

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

			// 动态生成记录列表
			var recordItem = document.createElement("li");
			recordItem.textContent = date + "：" + event;
			recordsList.appendChild(recordItem);

			// 清空表单
			dateInput.value = "";
			eventInput.value = "";
		}
	</script>
</body>
</html>
