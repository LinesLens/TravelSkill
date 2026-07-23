# HTML 输出模板

攻略文件命名：`<目的地>-旅游攻略.html`

## 完整 HTML 模板

```html
<!DOCTYPE html>
<html lang="zh-CN">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title><目的地>旅游攻略</title>
<style>
  :root {
    --primary: #e8724a;
    --primary-dark: #c05a32;
    --bg: #fdf6f0;
    --card-bg: #ffffff;
    --text: #333333;
    --text-secondary: #666666;
    --border: #e8ddd4;
    --accent-gold: #f0c040;
    --tag-bg: #fef3e8;
    --timeline-line: #e0d0c0;
    --shadow: 0 2px 12px rgba(0,0,0,0.06);
    --radius: 12px;
    --max-width: 800px;
  }

  * { margin: 0; padding: 0; box-sizing: border-box; }

  body {
    font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", "PingFang SC", "Hiragino Sans GB", "Microsoft YaHei", sans-serif;
    background: var(--bg);
    color: var(--text);
    line-height: 1.7;
    padding: 0;
  }

  /* ===== Header ===== */
  .header {
    background: linear-gradient(135deg, #e8724a 0%, #d46032 40%, #f0a060 100%);
    color: #fff;
    padding: 32px 20px 28px;
    text-align: center;
    position: relative;
    overflow: hidden;
  }
  .header::after {
    content: "";
    position: absolute;
    bottom: -20px; left: -10%; right: -10%;
    height: 40px;
    background: var(--bg);
    border-radius: 50% 50% 0 0;
  }
  .header h1 { font-size: 2em; margin-bottom: 10px; letter-spacing: 2px; }
  .header .meta-tags {
    display: flex; flex-wrap: wrap; justify-content: center; gap: 8px;
    font-size: 0.9em; opacity: 0.92;
  }
  .header .meta-tags span {
    background: rgba(255,255,255,0.2); padding: 4px 12px; border-radius: 20px;
  }

  /* ===== Container ===== */
  .container { max-width: var(--max-width); margin: 0 auto; padding: 16px 16px 40px; }

  /* ===== TOC ===== */
  .toc {
    background: var(--card-bg); border-radius: var(--radius); padding: 20px 24px;
    box-shadow: var(--shadow); margin-bottom: 20px;
  }
  .toc h2 { font-size: 1.2em; margin-bottom: 10px; color: var(--primary-dark); }
  .toc ol { padding-left: 20px; }
  .toc li { margin: 4px 0; }
  .toc a { color: var(--primary); text-decoration: none; }
  .toc a:hover { text-decoration: underline; }

  /* ===== Section Cards ===== */
  .section {
    background: var(--card-bg); border-radius: var(--radius); padding: 24px;
    box-shadow: var(--shadow); margin-bottom: 20px;
  }
  .section h2 {
    font-size: 1.4em; color: var(--primary-dark);
    border-bottom: 2px solid var(--border); padding-bottom: 8px; margin-bottom: 16px;
  }
  .section h3 { font-size: 1.15em; color: #555; margin: 20px 0 10px; }

  /* ===== Overview Table ===== */
  .overview-table {
    width: 100%; border-collapse: collapse; font-size: 0.92em;
  }
  .overview-table th {
    background: #fef3e8; color: var(--primary-dark); padding: 10px 8px;
    text-align: left; font-weight: 600;
  }
  .overview-table td { padding: 10px 8px; border-bottom: 1px solid var(--border); }

  /* ===== Timeline / Milestones ===== */
  .timeline {
    position: relative; padding-left: 24px; margin: 12px 0;
  }
  .timeline::before {
    content: "";
    position: absolute; left: 8px; top: 4px; bottom: 4px;
    width: 2px; background: var(--timeline-line);
  }
  .tl-item {
    position: relative; margin-bottom: 14px; padding-left: 16px;
    font-size: 0.95em;
  }
  .tl-item::before {
    content: "";
    position: absolute; left: -20px; top: 6px;
    width: 10px; height: 10px;
    background: var(--primary); border-radius: 50%;
    border: 2px solid #fff; box-shadow: 0 0 0 2px var(--primary);
  }
  .tl-time { font-weight: 700; color: var(--primary-dark); margin-right: 6px; }
  .tl-icon { margin-right: 4px; }
  .tl-notes { display: block; font-size: 0.85em; color: var(--text-secondary); margin-top: 2px; }

  /* ===== Day Slots ===== */
  .day-slots { display: grid; gap: 12px; margin: 12px 0; }
  .slot {
    display: flex; gap: 12px; padding: 12px; border-radius: 8px;
    background: #fefaf7; border-left: 4px solid var(--primary);
  }
  .slot-time { font-weight: 700; color: var(--primary-dark); white-space: nowrap; min-width: 90px; }
  .slot-body { flex: 1; }
  .slot-body strong { display: block; margin-bottom: 2px; }

  /* ===== Attraction Cards ===== */
  .attraction-card {
    border: 1px solid var(--border); border-radius: var(--radius); padding: 16px;
    margin: 12px 0; overflow: hidden;
  }
  .attraction-card img {
    width: 100%; height: 200px; object-fit: cover; border-radius: 8px;
    margin-bottom: 12px;
  }
  .attraction-card h4 { color: var(--primary-dark); margin-bottom: 6px; }
  .attraction-meta { display: flex; flex-wrap: wrap; gap: 8px; font-size: 0.88em; color: var(--text-secondary); }
  .attraction-meta span {
    background: var(--tag-bg); padding: 3px 10px; border-radius: 12px;
  }

  /* ===== Tables (Food, Accommodation, Budget, etc.) ===== */
  .data-table {
    width: 100%; border-collapse: collapse; font-size: 0.9em; margin: 12px 0;
  }
  .data-table th {
    background: #fef3e8; color: var(--primary-dark); padding: 10px 8px;
    text-align: left; font-weight: 600; white-space: nowrap;
  }
  .data-table td { padding: 10px 8px; border-bottom: 1px solid var(--border); vertical-align: top; }
  .data-table tr:hover td { background: #fefaf7; }

  /* ===== Star Rating (pure CSS) ===== */
  .rating { color: var(--accent-gold); font-weight: 700; white-space: nowrap; }
  .rating-count { font-size: 0.82em; color: var(--text-secondary); }

  /* ===== Food Image ===== */
  .food-img, .spot-img {
    width: 100%; max-height: 220px; object-fit: cover; border-radius: 8px;
    margin: 8px 0;
  }

  /* ===== Tips List ===== */
  .tips-list { list-style: none; padding: 0; }
  .tips-list li {
    padding: 8px 0; border-bottom: 1px solid var(--border);
  }
  .tips-list li:last-child { border-bottom: none; }

  /* ===== QR Code Section ===== */
  .qr-section {
    text-align: center; padding: 24px; margin-top: 20px;
    background: var(--card-bg); border-radius: var(--radius); box-shadow: var(--shadow);
  }
  .qr-section h3 { color: var(--primary-dark); margin-bottom: 8px; }
  .qr-section p { color: var(--text-secondary); font-size: 0.9em; margin-bottom: 12px; }
  #qrcode { display: inline-block; padding: 12px; background: #fff; border-radius: 8px; }
  #qrcode img { display: block; }

  /* ===== Disclaimer ===== */
  .disclaimer {
    text-align: center; color: var(--text-secondary); font-size: 0.85em;
    padding: 20px; margin-top: 8px;
  }

  /* ===== Responsive ===== */
  @media (max-width: 640px) {
    .header h1 { font-size: 1.5em; }
    .section { padding: 16px; }
    .data-table { font-size: 0.78em; }
    .data-table th, .data-table td { padding: 6px 4px; }
    .slot { flex-direction: column; gap: 4px; }
    .slot-time { min-width: auto; }
    .attraction-card img { height: 160px; }
  }

  /* ===== Print ===== */
  @media print {
    body { background: #fff; }
    .header { background: #e8724a !important; -webkit-print-color-adjust: exact; }
    .section { box-shadow: none; break-inside: avoid; }
    .qr-section { display: none; }
  }
</style>
</head>
<body>

<!-- ====== Header ====== -->
<div class="header">
  <h1><目的地>旅游攻略</h1>
  <div class="meta-tags">
    <span>  <出行日期></span>
    <span>  <天数>天</span>
    <span>  <人数>人</span>
    <span>  <预算类型></span>
  </div>
</div>

<div class="container">

<!-- ====== TOC ====== -->
<div class="toc">
  <h2> 目录</h2>
  <ol>
    <li><a href="#overview">精简概要</a></li>
    <li><a href="#itinerary">详细行程</a></li>
    <li><a href="#accommodation">住宿推荐</a></li>
    <li><a href="#budget">预算估算</a></li>
    <li><a href="#info">实用信息</a></li>
    <li><a href="#tips">旅行小贴士</a></li>
  </ol>
</div>

<!-- ====== Overview ====== -->
<div class="section" id="overview">
  <h2> 精简概要</h2>
  <p><目的地简介，3-5 句话概述城市/地区特色、最佳旅行季节和本次行程亮点。></p>

  <table class="overview-table" style="margin-top:14px;">
    <tr><th>日期</th><th>主题</th><th>核心活动</th><th>天气</th></tr>
    <tr><td>Day 1: <日期></td><td><主题></td><td><核心活动></td><td><天气></td></tr>
    <!-- 每天一行 -->
  </table>
</div>

<!-- ====== Itinerary ====== -->
<div id="itinerary">

<!-- ====== Day N ====== -->
<div class="section">
  <h2> Day <N>: <日期> — <主题></h2>

  <!-- 时段表格 -->
  <h3> 时段安排</h3>
  <div class="day-slots">
    <div class="slot">
      <div class="slot-time">  09:00-12:00</div>
      <div class="slot-body"><strong><活动名></strong><描述，含预估时间和实用提示></div>
    </div>
    <div class="slot">
      <div class="slot-time">  13:00-17:00</div>
      <div class="slot-body"><strong><活动名></strong><描述></div>
    </div>
    <div class="slot">
      <div class="slot-time">  18:00-21:00</div>
      <div class="slot-body"><strong><活动名></strong><描述></div>
    </div>
    <div class="slot">
      <div class="slot-time">  自由时间</div>
      <div class="slot-body"><strong>午餐+自由探索</strong><附近推荐></div>
    </div>
  </div>

  <!-- 重大节点时间轴 -->
  <h3>⏱ 今日重大节点</h3>
  <div class="timeline">
    <div class="tl-item">
      <span class="tl-time">09:00</span><span class="tl-icon"> </span><事件名称>
      <span class="tl-notes">  <实用提示，如"建议提前10分钟到场"></span>
    </div>
    <div class="tl-item">
      <span class="tl-time">10:30</span><span class="tl-icon"> </span><事件名称>
      <span class="tl-notes">  <实用提示></span>
    </div>
    <div class="tl-item">
      <span class="tl-time">12:00</span><span class="tl-icon"> </span>午餐：<餐厅名>（大众点评 <评分>⭐）
      <span class="tl-notes">  <预订提示></span>
    </div>
    <div class="tl-item">
      <span class="tl-time">14:00</span><span class="tl-icon"> </span><事件名称>
      <span class="tl-notes">  <实用提示></span>
    </div>
    <div class="tl-item">
      <span class="tl-time">18:00</span><span class="tl-icon"> </span>晚餐：<餐厅名>（大众点评 <评分>⭐）
      <span class="tl-notes">  <预订提示></span>
    </div>
  </div>

  <!-- 路线地图 -->
  <h3>  路线地图</h3>
  <p><a href="<Google Maps/Amap 短链接>" target="_blank">  查看完整路线地图</a></p>

  <!-- 景点 -->
  <h3>  景点</h3>
  <div class="attraction-card">
    <img src="<Pexels 图片 URL>" alt="<景点名>" loading="lazy">
    <h4><景点名> <small>（<当地语言名>）</small></h4>
    <div class="attraction-meta">
      <span>  门票：<价格></span>
      <span>  开放：<时间></span>
      <span>⏱ 游览：<时长></span>
    </div>
    <p style="margin-top:8px;"><提示></p>
  </div>
  <!-- 多个景点重复 -->

  <!-- 美食 -->
  <h3>  美食推荐</h3>
  <table class="data-table">
    <tr><th>餐厅</th><th>类型</th><th>人均</th><th>评分</th><th>必点</th><th>地址</th><th>预订</th></tr>
    <tr>
      <td><strong><餐厅名称></strong></td>
      <td><类型></td>
      <td><人均价格></td>
      <td><span class="rating"> <评分>⭐</span><br><span class="rating-count"><评论数>评</span></td>
      <td><必点菜品></td>
      <td><地址></td>
      <td><预订提示></td>
    </tr>
    <!-- 多个餐厅重复 -->
  </table>
  <img class="food-img" src="<Pexels 图片 URL>" alt="<美食>" loading="lazy">

  <!-- 交通 -->
  <h3>  交通建议</h3>
  <p><当天交通方式和注意事项></p>

  <!-- 雨天备选 -->
  <h3>  雨天备选</h3>
  <table class="data-table">
    <tr><th>室内活动</th><th>说明</th></tr>
    <tr><td><活动名></td><td><描述></td></tr>
  </table>
</div>
<!-- 每天重复以上结构 -->

</div>

<!-- ====== Accommodation ====== -->
<div class="section" id="accommodation">
  <h2>  住宿推荐</h2>
  <table class="data-table">
    <tr><th>酒店</th><th>区域</th><th>类型</th><th>人均/晚</th><th>评分</th><th>地址</th><th>优势</th></tr>
    <tr>
      <td><strong><酒店名称></strong></td>
      <td><区域></td>
      <td><类型></td>
      <td><人均价格/晚></td>
      <td><span class="rating"> <评分>⭐</span><br><span class="rating-count"><评论数>评</span></td>
      <td><地址></td>
      <td><优势></td>
    </tr>
    <!-- 多个酒店重复 -->
  </table>
  <img class="food-img" src="<Pexels 图片 URL>" alt="<住宿区域>" loading="lazy">
</div>

<!-- ====== Budget ====== -->
<div class="section" id="budget">
  <h2>  预算估算</h2>
  <table class="data-table">
    <tr><th>类别</th><th>预估费用（人均）</th><th>备注</th></tr>
    <tr><td>  大交通</td><td><金额></td><td><机票/火车票说明></td></tr>
    <tr><td>  住宿</td><td><金额></td><td><按 X 晚计算></td></tr>
    <tr><td>  餐饮</td><td><金额></td><td><每日估算></td></tr>
    <tr><td>  门票</td><td><金额></td><td><主要景点门票合计></td></tr>
    <tr><td>  市内交通</td><td><金额></td><td><交通卡/单次票></td></tr>
    <tr><td>  购物</td><td><金额></td><td><酌情预估></td></tr>
    <tr><td>  其他</td><td><金额></td><td><SIM 卡、保险等></td></tr>
    <tr style="font-weight:700;background:#fef3e8;"><td>合计</td><td><strong><总金额></strong></td><td></td></tr>
  </table>
</div>

<!-- ====== Practical Info ====== -->
<div class="section" id="info">
  <h2>  实用信息</h2>

  <h3>  天气与穿衣</h3>
  <ul class="tips-list">
    <li>出行期间天气趋势：<描述></li>
    <li>温度范围：<范围></li>
    <li>穿衣建议：<建议></li>
    <li>必备物品：<列表></li>
  </ul>
  <p style="font-size:0.85em;color:var(--text-secondary);">数据来源：<✅ 实时数据 /  参考数据></p>

  <h3>  交通卡/通票</h3>
  <table class="data-table">
    <tr><th>卡/票名称</th><th>适用范围</th><th>价格</th><th>购买方式</th><th>性价比</th></tr>
    <tr><td><名称></td><td><范围></td><td><价格></td><td><方式></td><td><建议></td></tr>
  </table>

  <h3>  签证信息</h3>
  <ul class="tips-list">
    <li>签证类型：<类型></li>
    <li>办理方式：<方式></li>
    <li>所需材料：<列表></li>
    <li>办理时间：<时长></li>
    <li>注意事项：<提示></li>
  </ul>
  <p style="font-size:0.85em;color:var(--text-secondary);">数据来源：  参考数据，建议出行前向使领馆核实</p>

  <h3>  当地习俗</h3>
  <ul class="tips-list">
    <li><习俗/禁忌></li>
  </ul>

  <h3>  常用语言</h3>
  <table class="data-table">
    <tr><th>中文</th><th>当地语言</th><th>发音</th></tr>
    <tr><td>你好</td><td>...</td><td>...</td></tr>
    <tr><td>谢谢</td><td>...</td><td>...</td></tr>
    <tr><td>多少钱</td><td>...</td><td>...</td></tr>
    <tr><td>在哪里</td><td>...</td><td>...</td></tr>
    <tr><td>救命/帮助</td><td>...</td><td>...</td></tr>
  </table>

  <h3>  紧急联系</h3>
  <table class="data-table">
    <tr><th>类型</th><th>电话</th><th>地址/备注</th></tr>
    <tr><td>报警</td><td><电话></td><td></td></tr>
    <tr><td>急救</td><td><电话></td><td></td></tr>
    <tr><td>中国大使馆</td><td><电话></td><td><地址></td></tr>
    <tr><td>旅游热线</td><td><电话></td><td></td></tr>
  </table>

  <h3>  拍照打卡点</h3>
  <table class="data-table">
    <tr><th>地点</th><th>最佳时间</th><th>拍摄建议</th></tr>
    <tr><td><地点></td><td><时间></td><td><建议></td></tr>
  </table>
  <img class="spot-img" src="<Pexels 图片 URL>" alt="<拍照点>" loading="lazy">
</div>

<!-- ====== Tips ====== -->
<div class="section" id="tips">
  <h2>  旅行小贴士</h2>
  <ol class="tips-list">
    <li><strong><贴士主题></strong>：<内容></li>
    <li><strong><贴士主题></strong>：<内容></li>
  </ol>
</div>

<!-- ====== QR Code ====== -->
<div class="qr-section">
  <h3>  分享给手机</h3>
  <p>扫描二维码，在手机上打开此攻略</p>
  <div id="qrcode"></div>
  <p style="margin-top:8px;font-size:0.8em;">也可用手机浏览器「添加到主屏幕」离线查看</p>
</div>

<!-- ====== Disclaimer ====== -->
<div class="disclaimer">
  <p>  本攻略于 <生成日期> 生成，部分信息可能已有变化，建议出行前核实关键信息（航班、酒店、门票价格等）。</p>
</div>

</div><!-- /container -->

<!-- ====== QR Code Generator (qrcodejs from CDN) ====== -->
<script src="https://cdn.jsdelivr.net/npm/qrcodejs@1.0.0/qrcode.min.js"></script>
<script>
  (function() {
    var qrEl = document.getElementById("qrcode");
    if (!qrEl) return;
    var url = window.location.href;
    new QRCode(qrEl, {
      text: url,
      width: 180,
      height: 180,
      colorDark: "#333333",
      colorLight: "#ffffff",
      correctLevel: QRCode.CorrectLevel.M
    });
  })();
</script>

</body>
</html>
```
