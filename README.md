# FSW-TRAVEL
这是关于方便做旅行攻略的网页，只需要打开网页并编辑即可
<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>XX旅游攻略</title>
    <style>
        * {
            box-sizing: border-box;
            font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
        }
        body {
            margin: 0;
            padding: 15px;
            background: #f7f8fa;
            padding-bottom: 100px;
        }
        .container {
            max-width: 800px;
            margin: 0 auto;
            background: white;
            padding: 20px;
            border-radius: 12px;
            box-shadow: 0 2px 10px rgba(0,0,0,0.08);
        }
        h1 {
            text-align: center;
            color: #2d3748;
            font-size: 22px;
            margin-bottom: 20px;
        }
        .food-top-wrap {
            border-left: 4px solid #67c23a;
            padding: 12px 15px;
            margin-bottom: 20px;
            background: #f2fbf2;
            border-radius: 8px;
        }
        .food-top-wrap h3 {
            margin: 0 0 10px 0;
            color: #2f855a;
            font-size: 18px;
        }
        .day {
            border-left: 4px solid #4299e1;
            padding: 12px 15px;
            margin-bottom: 15px;
            background: #f0f7ff;
            border-radius: 8px;
            position: relative;
        }
        .day h3 {
            margin: 0 0 8px 0;
            color: #2b6cb0;
            font-size: 18px;
            padding-right: 60px;
        }
        .item-row {
            margin: 6px 0;
            font-size: 16px;
            line-height: 1.5;
            display: flex;
            align-items: center;
            gap: 6px;
        }
        .static-label {
            font-weight: bold;
            color: #4a5568;
            width: 70px;
            display: inline-block;
            border-bottom: 1px dashed #ccc;
            padding: 2px 4px;
            outline: none;
            flex-shrink: 0;
        }
        .edit-text {
            border-bottom: 1px dashed #ccc;
            padding: 2px 4px;
            flex: 1;
            outline: none;
            min-width: 50px;
        }
        .add-row-btn {
            background: #909399;
            color: #fff;
            border: none;
            border-radius: 4px;
            padding: 2px 6px;
            font-size: 14px;
            cursor: pointer;
            flex-shrink: 0;
        }
        .food-list {
            display: flex;
            flex-wrap: wrap;
            gap: 10px;
            margin-top: 10px;
            margin-bottom: 10px;
        }
        .food-item {
            background: #fef5f7;
            padding: 6px 10px;
            border-radius: 6px;
            font-size: 15px;
            white-space: nowrap;
            display: flex;
            align-items: center;
            gap:6px;
        }
        .food-text {
            border-bottom: 1px dashed #ccc;
            outline: none;
        }
        input[type="checkbox"] {
            width: 18px;
            height: 18px;
        }
        .del-food-btn {
            color:#f56c6c;
            border:none;
            background:none;
            font-size:16px;
            cursor:pointer;
            padding:0 4px;
        }
        .del-day-btn {
            position:absolute;
            top:12px;
            right:12px;
            color:#f56c6c;
            border:1px solid #f56c6c;
            background:#fff;
            border-radius:4px;
            padding:2px 6px;
            font-size:13px;
            cursor:pointer;
        }
        .add-food-btn {
            background: #67c23a;
            color: #fff;
            border: none;
            border-radius: 6px;
            padding: 4px 10px;
            font-size: 14px;
            cursor: pointer;
            margin-bottom: 10px;
        }
        .add-day-btn {
            position: fixed;
            bottom: 20px;
            left: 50%;
            transform: translateX(-50%);
            width: 60px;
            height: 60px;
            border-radius: 50%;
            background: #4299e1;
            color: white;
            font-size: 30px;
            border: none;
            box-shadow: 0 2px 10px rgba(0,0,0,0.2);
            cursor: pointer;
            z-index: 999;
        }
        .save-top {
            position: sticky;
            top: 0;
            background: white;
            padding: 10px 0;
            z-index: 100;
            text-align: center;
        }
        .save-btn {
            background: #28a745;
            color: white;
            border: none;
            padding: 8px 16px;
            border-radius: 6px;
            font-size: 16px;
            cursor: pointer;
        }
    </style>

<!-- 百度统计 -->
<script>
var _hmt = _hmt || [];
(function() {
  var hm = document.createElement("script");
  hm.src = "https://hm.baidu.com/hm.js?272119dae6cce7e3ded69c4a57f828d1";
  var s = document.getElementsByTagName("script")[0]; 
  s.parentNode.insertBefore(hm, s);
})();
</script>

<!-- Google tag (gtag.js) -->
<script async src="https://www.googletagmanager.com/gtag/js?id=G-N13ZH72VV9"></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());

  gtag('config', 'G-N13ZH72VV9');
</script>
</head>
<body>
    <div class="save-top">
        <button class="save-btn" onclick="saveToFile()">保存文件</button>
    </div>
    <div class="container">
        <h1 class="edit-text" contenteditable>XX旅游攻略</h1>

        <div class="food-top-wrap">
            <h3>美食清单</h3>
            <button class="add-food-btn" onclick="addFood(this)">+ 添加美食</button>
            <div class="food-list">
                <div class="food-item"><input type="checkbox"><span class="food-text" contenteditable>栖风渡鱼粉</span><button class="del-food-btn" onclick="delFood(this)">×</button></div>
                <div class="food-item"><input type="checkbox"><span class="food-text" contenteditable>豆米火锅</span><button class="del-food-btn" onclick="delFood(this)">×</button></div>
                <div class="food-item"><input type="checkbox"><span class="food-text" contenteditable>酸汤火锅</span><button class="del-food-btn" onclick="delFood(this)">×</button></div>
            </div>
        </div>

        <div id="days-container">
            <div class="day">
                <button class="del-day-btn" onclick="delDay(this)">删除本日</button>
                <h3 class="edit-text" contenteditable>D1：抵达XX入住</h3>
                <div class="item-row">
                    <span class="static-label" contenteditable>自驾</span>
                    <span class="edit-text" contenteditable></span>
                    <button class="add-row-btn" onclick="addItemRow(this)">+</button>
                </div>
                <div class="item-row">
                    <span class="static-label" contenteditable>住宿</span>
                    <span class="edit-text" contenteditable>1晚</span>
                    <button class="add-row-btn" onclick="addItemRow(this)">+</button>
                </div>
            </div>

            <div class="day">
                <button class="del-day-btn" onclick="delDay(this)">删除本日</button>
                <h3 class="edit-text" contenteditable>D2：A→B</h3>
                <div class="item-row">
                    <span class="static-label" contenteditable>自驾</span>
                    <span class="edit-text" contenteditable>租车，路程约2h</span>
                    <button class="add-row-btn" onclick="addItemRow(this)">+</button>
                </div>
                <div class="item-row">
                    <span class="static-label" contenteditable>住宿</span>
                    <span class="edit-text" contenteditable>XX民宿2晚</span>
                    <button class="add-row-btn" onclick="addItemRow(this)">+</button>
                </div>
            </div>
        </div>
    </div>

    <button class="add-day-btn" onclick="addNewDay()">+</button>

    <script>
        const STORAGE_KEY = 'travel_plan_data';
        window.onload = function () {
            const saveData = localStorage.getItem(STORAGE_KEY);
            if (saveData) {
                document.getElementById('days-container').innerHTML = saveData;
            }
            document.addEventListener('input', autoSaveData);
            document.addEventListener('click', autoSaveData);
        };
        function autoSaveData() {
            localStorage.setItem(STORAGE_KEY, document.getElementById('days-container').innerHTML);
        }

        function addItemRow(btn){
            const row = btn.closest('.item-row');
            const label = row.querySelector('.static-label').innerText;
            const newRow = document.createElement('div');
            newRow.className = 'item-row';
            newRow.innerHTML = `<span class="static-label" contenteditable>${label}</span><span class="edit-text" contenteditable></span><button class="add-row-btn" onclick="addItemRow(this)">+</button>`;
            row.after(newRow);
            autoSaveData();
        }

        function delFood(btn){
            btn.parentElement.remove();
            autoSaveData();
        }
        function delDay(btn){
            if(confirm('确定删除这一天？')){
                btn.parentElement.remove();
                autoSaveData();
            }
        }
        function addFood(btn) {
            const list = btn.nextElementSibling;
            const newFood = document.createElement('div');
            newFood.className = 'food-item';
            newFood.innerHTML = `<input type="checkbox"><span class="food-text" contenteditable>新美食</span><button class="del-food-btn" onclick="delFood(this)">×</button>`;
            list.appendChild(newFood);
            autoSaveData();
        }
        // 新增一天
        function addNewDay() {
            const container = document.getElementById('days-container');
            const newDay = document.createElement('div');
            newDay.className = 'day';
            newDay.innerHTML = `
                <button class="del-day-btn" onclick="delDay(this)">删除本日</button>
                <h3 class="edit-text" contenteditable>新的一天</h3>
                <div class="item-row">
                    <span class="static-label" contenteditable>自驾</span>
                    <span class="edit-text" contenteditable></span>
                    <button class="add-row-btn" onclick="addItemRow(this)">+</button>
                </div>
                <div class="item-row">
                    <span class="static-label" contenteditable>住宿</span>
                    <span class="edit-text" contenteditable></span>
                    <button class="add-row-btn" onclick="addItemRow(this)">+</button>
                </div>
            `;
            container.appendChild(newDay);
            autoSaveData();
        }
        function saveToFile() {
            const fullHtml = document.documentElement.outerHTML;
            const blob = new Blob([fullHtml], { type: 'text/html' });
            const url = URL.createObjectURL(blob);
            const a = document.createElement('a');
            a.href = url;
            a.download = '自驾攻略.html';
            document.body.appendChild(a);
            a.click();
            document.body.removeChild(a);
            URL.revokeObjectURL(url);
        }
    </script>
</body>
</html>
