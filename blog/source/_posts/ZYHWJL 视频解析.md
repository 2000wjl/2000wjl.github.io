---
title: ZYHWJL 视频解析
date: 2021-04-15 14:53:43
tags: 测试
categories: [测试,视频解析]
---
<script src="https://v.zyhwjl.tk/js/index.js" type="text/javascript" charset="utf-8"></script>
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap@3.3.7/dist/css/bootstrap.min.css" integrity="sha384-BVYiiSIFeK1dGmJRAkycuHAHRg32OmUcww7on3RYdg4Va+PmSTsz/K68vbdEjh4u" crossorigin="anonymous">
<body style="background-color: #F7F7F7">
	<iframe src="https://v.zyhwjl.tk/files/sp.html" id="player" width="100%" height="500px" allowfullscreen="true" allowtransparency="true" frameborder="0" scrolling="no"></iframe>

<form style="line-height: 15px;">
	<div class="input-group" style="width: 100%;">
		<span class="input-group-addon input-lg" style="width: 80px; color:red;">不能播放换接口</span>
		<select class="form-control input-lg" id="jk" name="a">
			<option value="https://v.zyhwjl.cn/jiexi/?url=">ZYHWJL</option>
			<option value="https://www.8090g.cn/jiexi/?url=">1号默认解析接口</option>
			<option value="https://z1.m1907.cn/?a=1&amp;jx=">2号解接口(能搜索)</option>
			<option value="https://okjx.cc/?url=">3号解接口(备用)</option>
			<option value="https://17kyun.com/api.php?url=">4号解接口(备用)</option>
			<option value="https://2.08bk.com/?url=">5号解接口(备用)</option>
			<option value="https://www.administratorw.com/admin.php?url=">6号解接口(备用)</option>
			<option value="https://jsap.attakids.com/?url=">7号解接口(备用)</option>
			<option value="https://api.52jiexi.top/analysis.php?v=">8号解接口(备用)</option>
		</select>
	</div><br>
	<div class="input-group" style="width: 100%;">
        <span class="input-group-addon input-lg" style="width: 80px;">需要解析视频网址</span>
        <input class="form-control input-lg" type="text" name="url" autocomplete="off" placeholder="粘贴视频网址" id="url">
	</div><br>
	<button type="button" id="bf" value="解析播放" class="btn btn-success btn-lg btn-block" onclick="bfjx()">Go-点击开始解析</button>
</form>
</body>

