[Uploading Code_20260305.html…]()
<!DOCTYPE html>
<html lang="zh-CN">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width,initial-scale=1.0">
<title>保利升煌艺术中心 - 艺术品收藏、鉴定、备案、展览平台</title>
<link rel="stylesheet" href="https://cdn.bootcdn.net/ajax/libs/font-awesome/6.4.0/css/all.min.css">
<style>
*{margin:0;padding:0;box-sizing:border-box;font-family:Microsoft YaHei,sans-serif}
:root{--main:#b28c5a;--dark:#1a1a1d;--light:#f6f6f8;--transition:all 0.3s cubic-bezier(0.4, 0, 0.2, 1)}
body{color:#333;line-height:1.6;background:#f8f8f8}
.container{width:92%;max-width:480px;margin:0 auto;padding:20px 0}

/* 导航 + LOGO */
header{background:#fff;box-shadow:0 2px 10px rgba(0,0,0,0.05);position:sticky;top:0;z-index:999;transition:var(--transition)}
.nav{display:flex;justify-content:space-between;align-items:center;height:70px}
.logo-area{display:flex;align-items:center;gap:12px}
.logo-box{width:40px;height:40px;background:var(--main);color:#fff;border-radius:4px;display:flex;align-items:center;justify-content:center;font-weight:bold;font-size:18px;transition:var(--transition)}
.logo-box:hover{transform:scale(1.05)}
.logo-text{font-size:20px;font-weight:bold;color:#222}
.menu{display:flex;gap:30px}
.menu a{font-size:15px;color:#333;text-decoration:none;transition:var(--transition);position:relative}
.menu a::after{content:'';position:absolute;bottom:-5px;left:0;width:0;height:2px;background:var(--main);transition:var(--transition)}
.menu a:hover{color:var(--main)}
.menu a:hover::after{width:100%}

/* 页面容器 */
.page{display:none;opacity:0;transform:translateY(10px);transition:var(--transition)}
.page.active{display:block;opacity:1;transform:translateY(0)}
.back-btn{background:#fff;border:none;font-size:18px;padding:10px;cursor:pointer;transition:var(--transition);color:#333}
.back-btn:hover{color:var(--main)}

/* 轮播 */
.swiper{width:100%;height:500px;position:relative;overflow:hidden;border-radius:0 0 20px 20px}
.slide{position:absolute;width:100%;height:100%;background-size:cover;background-position:center;display:flex;align-items:center;justify-content:center;color:#fff;text-align:center;opacity:0;transition:opacity 1s ease-in-out}
.slide.active{opacity:1}
.slide::before{content:'';position:absolute;top:0;left:0;width:100%;height:100%;background:rgba(0,0,0,0.55);transition:var(--transition)}
.slide-content{position:relative;max-width:700px;padding:20px}
.slide h1{font-size:42px;margin-bottom:15px;text-shadow:0 2px 4px rgba(0,0,0,0.3)}
.slide p{font-size:16px;margin-bottom:25px;text-shadow:0 1px 2px rgba(0,0,0,0.3)}
.btn{padding:12px 30px;background:var(--main);color:#fff;border:none;border-radius:30px;cursor:pointer;font-size:15px;text-decoration:none;display:inline-block;transition:var(--transition);box-shadow:0 4px 12px rgba(178, 140, 90, 0.3)}
.btn:hover{transform:translateY(-2px);box-shadow:0 6px 16px rgba(178, 140, 90, 0.4)}
.btn-full{width:100%;height:50px;background:linear-gradient(90deg, #b28c5a, #977446);color:#fff;border:none;border-radius:12px;font-size:16px;font-weight:500;cursor:pointer;transition:var(--transition);box-shadow:0 4px 12px rgba(178, 140, 90, 0.3)}
.btn-full:hover{transform:translateY(-2px);box-shadow:0 6px 16px rgba(178, 140, 90, 0.4)}

/* 板块 */
.section{padding:70px 0}
.title{text-align:center;margin-bottom:50px}
.title h2{font-size:28px;color:#222;position:relative;display:inline-block;padding-bottom:12px}
.title h2::after{content:"";width:60px;height:2px;background:var(--main);position:absolute;bottom:0;left:50%;transform:translateX(-50%);transition:var(--transition)}
.title p{color:#777;margin-top:12px}

/* 核心功能 */
.three-box{display:grid;grid-template-columns:repeat(3,1fr);gap:25px;margin-top:30px}
@media(max-width:768px){.three-box{grid-template-columns:1fr}}
.func-card{background:#fff;border:1px solid #eee;border-radius:16px;padding:30px;box-shadow:0 5px 15px rgba(0,0,0,0.04);transition:var(--transition)}
.func-card:hover{transform:translateY(-5px);box-shadow:0 10px 25px rgba(0,0,0,0.08)}
.func-card h3{font-size:18px;color:#222;margin-bottom:18px;padding-left:10px;border-left:4px solid var(--main)}
.func-card ul{list-style:none}
.func-card li{padding:8px 0;font-size:15px;color:#444;position:relative;padding-left:18px}
.func-card li::before{content:"•";position:absolute;left:0;color:var(--main);font-weight:bold}

/* 服务卡片 */
.card-box{display:grid;grid-template-columns:repeat(auto-fill,minmax(270px,1fr));gap:25px}
.card{background:#fff;border:1px solid #eee;border-radius:16px;padding:30px 25px;text-align:center;transition:var(--transition);box-shadow:0 5px 15px rgba(0,0,0,0.04)}
.card:hover{transform:translateY(-5px);box-shadow:0 10px 25px rgba(0,0,0,0.08)}
.card i{font-size:36px;color:var(--main);margin-bottom:18px}
.card h3{font-size:18px;margin-bottom:10px}
.card p{font-size:14px;color:#666}

/* 备案表单 */
.apply{background:var(--light);padding:60px 0}
.form-box{max-width:600px;margin:0 auto;background:#fff;padding:40px;border-radius:16px;box-shadow:0 5px 20px rgba(0,0,0,0.05);transition:var(--transition)}
.form-item{margin-bottom:20px}
.form-item label{display:block;margin-bottom:8px;font-size:14px;color:#555}
.form-item input,.form-item select,.form-item textarea{width:100%;height:44px;padding:0 12px;border:1px solid #ddd;border-radius:8px;outline:none;transition:var(--transition)}
.form-item input:focus,.form-item select:focus,.form-item textarea:focus{border-color:var(--main);box-shadow:0 0 0 3px rgba(178, 140, 90, 0.1)}
.form-item textarea{height:100px;resize:none;padding:12px}

/* 联系我们 */
.contact{background:#fff;padding:60px 0}
.contact-box{display:grid;grid-template-columns:repeat(auto-fit,minmax(250px,1fr));gap:20px;text-align:center}
.contact-item i{font-size:30px;color:var(--main);margin-bottom:15px;transition:var(--transition)}
.contact-item:hover i{transform:scale(1.1)}
.contact-item h4{margin-bottom:8px}

/* 季度名额页面样式 */
.quota-card{background:linear-gradient(135deg, #6b3c1e, #b28c5a);color:#fff;border-radius:20px;padding:25px 20px;margin-bottom:20px;position:relative;overflow:hidden;transition:var(--transition);box-shadow:0 8px 24px rgba(107, 60, 30, 0.2)}
.quota-card:hover{transform:translateY(-2px);box-shadow:0 12px 32px rgba(107, 60, 30, 0.3)}
.quota-card::before{content:'';position:absolute;top:-50%;right:-20%;width:200px;height:200px;background:rgba(255,255,255,0.1);border-radius:50%;transition:var(--transition)}
.quota-card:hover::before{transform:scale(1.1)}
.quota-top{font-size:15px;opacity:0.9;margin-bottom:20px}
.quota-row{display:flex;justify-content:space-between;margin-bottom:20px}
.quota-col{text-align:center}
.quota-num{font-size:48px;font-weight:bold;line-height:1}
.quota-label{font-size:14px;opacity:0.8;margin-top:5px}
.quota-tag{display:inline-block;padding:4px 10px;border-radius:20px;font-size:12px;margin-top:8px;background:rgba(255,255,255,0.2);transition:var(--transition)}
.quota-tag:hover{background:rgba(255,255,255,0.3)}
.quota-footer{display:flex;justify-content:space-between;font-size:14px;opacity:0.8}
.step-card{background:#fff;border-radius:16px;padding:20px;margin-bottom:15px;transition:var(--transition);box-shadow:0 5px 15px rgba(0,0,0,0.04)}
.step-card:hover{transform:translateY(-2px);box-shadow:0 8px 24px rgba(0,0,0,0.08)}
.step-item{display:flex;gap:15px;margin-bottom:20px}
.step-item:last-child{margin-bottom:0}
.step-icon{width:36px;height:36px;border-radius:50%;background:#f6e9d8;color:#b28c5a;display:flex;align-items:center;justify-content:center;flex-shrink:0;transition:var(--transition)}
.step-item:hover .step-icon{transform:scale(1.1);background:#f0d7b8}
.step-content h4{font-size:16px;margin-bottom:5px}
.step-content .date{color:#b28c5a;font-weight:500}
.step-content p{font-size:14px;color:#666}
.rule-card{background:#fff;border-radius:16px;padding:20px;margin-bottom:15px;transition:var(--transition);box-shadow:0 5px 15px rgba(0,0,0,0.04)}
.rule-card:hover{transform:translateY(-2px);box-shadow:0 8px 24px rgba(0,0,0,0.08)}
.rule-card h4{color:#b28c5a;margin-bottom:10px}
.rule-card p{font-size:14px;color:#666;line-height:1.7}
.list-toggle{background:#fff;border-radius:16px;padding:15px 20px;display:flex;align-items:center;justify-content:space-between;margin-bottom:15px;cursor:pointer;transition:var(--transition);box-shadow:0 5px 15px rgba(0,0,0,0.04)}
.list-toggle:hover{transform:translateY(-2px);box-shadow:0 8px 24px rgba(0,0,0,0.08)}
.list-left{display:flex;align-items:center;gap:10px}
.list-icon{color:#b28c5a;font-size:20px;transition:var(--transition)}
.list-toggle:hover .list-icon{transform:scale(1.1)}
.list-badge{background:#b28c5a;color:#fff;padding:3px 8px;border-radius:12px;font-size:12px;margin-left:8px;transition:var(--transition)}
.list-toggle:hover .list-badge{background:#977446}
.list-table{background:#fff;border-radius:16px;overflow:hidden;margin-bottom:15px;display:none;transition:var(--transition);box-shadow:0 5px 15px rgba(0,0,0,0.04)}
.list-table.show{display:block}
.table-header{background:linear-gradient(90deg, #b28c5a, #977446);color:#fff;display:grid;grid-template-columns:60px 1fr 1fr 80px;padding:12px 15px;font-size:14px;font-weight:500}
.table-row{display:grid;grid-template-columns:60px 1fr 1fr 80px;padding:12px 15px;font-size:14px;border-bottom:1px solid #f5f5f5;transition:var(--transition)}
.table-row:hover{background:#fdf9f3;transform:translateX(2px)}
.table-row:nth-child(even){background:#fdf9f3}
.rank-1,.rank-2,.rank-3{font-weight:bold}
.rank-1{color:#ffd700}
.rank-2{color:#c0c0c0}
.rank-3{color:#cd7f32}
.phone{color:#666}
.count{color:#b28c5a;font-weight:500}
.countdown-card{background:#1a1a1d;color:#fff;border-radius:16px;padding:20px;text-align:center;margin-bottom:15px;transition:var(--transition);box-shadow:0 8px 24px rgba(26, 26, 29, 0.2)}
.countdown-card:hover{transform:translateY(-2px);box-shadow:0 12px 32px rgba(26, 26, 29, 0.3)}
.countdown-title{font-size:14px;opacity:0.7;margin-bottom:15px}
.countdown-row{display:flex;justify-content:center;gap:15px}
.countdown-item{width:60px;height:60px;background:rgba(255,255,255,0.1);border-radius:8px;display:flex;flex-direction:column;align-items:center;justify-content:center;transition:var(--transition)}
.countdown-item:hover{background:rgba(255,255,255,0.15);transform:scale(1.05)}
.countdown-num{font-size:24px;font-weight:bold;color:#f7c968}
.countdown-unit{font-size:12px;opacity:0.7}
.tip-card{background:#fff9e8;border-left:4px solid #b28c5a;padding:15px;border-radius:8px;font-size:14px;color:#666;margin-bottom:20px;transition:var(--transition)}
.tip-card:hover{transform:translateX(2px);box-shadow:0 4px 12px rgba(178, 140, 90, 0.1)}

/* 底部 */
footer{background:#1a1a1d;color:#aaa;padding:45px 0 25px;text-align:center;font-size:14px;transition:var(--transition)}
</style>
</head>
<body>

<!-- 首页 -->
<div class="page active" id="pageHome">
  <header>
    <div class="container nav">
      <div class="logo-area">
        <div class="logo-box">保利</div>
        <div class="logo-text">保利升煌艺术中心</div>
      </div>
      <div class="menu">
        <a href="#home">首页</a>
        <a href="#about">关于我们</a>
        <a href="#core">核心功能</a>
        <a href="#service">服务项目</a>
        <a href="#apply">藏品备案</a>
        <a href="#contact">联系我们</a>
        <a href="javascript:goQuota()">季度名额</a>
      </div>
    </div>
  </header>

  <!-- 轮播图 -->
  <div class="swiper" id="swiper">
    <div class="slide active" style="background-image:url(https://picsum.photos/id/306/1920/1080)">
      <div class="slide-content">
        <h1>保利升煌艺术中心</h1>
        <p>专业艺术品鉴定、备案、展览、数字化服务平台</p>
        <a class="btn" href="javascript:goQuota()">立即抢占季度名额</a>
      </div>
    </div>
    <div class="slide" style="background-image:url(https://picsum.photos/id/1058/1920/1080)">
      <div class="slide-content">
        <h1>权威藏品备案</h1>
        <p>永久存档、官方可查、专业认证</p>
        <a class="btn" href="#apply">我要备案</a>
      </div>
    </div>
    <div class="slide" style="background-image:url(https://picsum.photos/id/175/1920/1080)">
      <div class="slide-content">
        <h1>全国+国际展览</h1>
        <p>国博、联合国、金砖、欧美巡展一站式服务</p>
        <a class="btn" href="#core">查看功能</a>
      </div>
    </div>
  </div>

  <!-- 关于我们 -->
  <section class="section" id="about">
    <div class="container">
      <div class="title">
        <h2>关于保利升煌艺术中心</h2>
        <p>专业、权威、合规的艺术品综合服务机构</p>
      </div>
      <div style="max-width:800px;margin:0 auto;text-align:center;line-height:1.8;color:#555;">
        保利升煌艺术中心专注艺术品收藏、鉴定、评估、备案、展览、数字化与国际文化交流，
        为广大藏家、机构提供安全、正规、高效的艺术品全流程服务。
      </div>
    </div>
  </section>

  <!-- 核心功能 -->
  <section class="section" id="core" style="background:#f9f9f9;">
    <div class="container">
      <div class="title">
        <h2>核心功能</h2>
        <p>藏品服务 · 展览平台 · 国际巡展 全体系支持</p>
      </div>
      <div class="three-box">
        <div class="func-card">
          <h3>藏品服务</h3>
          <ul>
            <li>甄选</li>
            <li>建档</li>
            <li>开户</li>
            <li>银行补贴</li>
            <li>季度名额</li>
          </ul>
        </div>
        <div class="func-card">
          <h3>展览平台</h3>
          <ul>
            <li>市级平台</li>
            <li>省级平台</li>
            <li>国级平台</li>
            <li>国博平台</li>
          </ul>
        </div>
        <div class="func-card">
          <h3>国际巡展</h3>
          <ul>
            <li>金砖巡展</li>
            <li>联合国展</li>
            <li>欧洲巡展</li>
            <li>美洲巡展</li>
          </ul>
        </div>
      </div>
    </div>
  </section>

  <!-- 服务项目 -->
  <section class="section" id="service">
    <div class="container">
      <div class="title"><h2>核心服务</h2><p>为收藏爱好者提供一站式专业服务</p></div>
      <div class="card-box">
        <div class="card"><i class="fa-solid fa-magnifying-glass-chart"></i><h3>鉴定评估</h3><p>专业团队科学鉴定、客观评估</p></div>
        <div class="card"><i class="fa-solid fa-folder-open"></i><h3>建档备案</h3><p>藏品信息永久存档、官方可查</p></div>
        <div class="card"><i class="fa-solid fa-building-columns"></i><h3>展览服务</h3><p>全国及国际正规展览渠道</p></div>
        <div class="card"><i class="fa-solid fa-globe"></i><h3>数字化平台</h3><p>高清数字永久展示</p></div>
      </div>
    </div>
  </section>

  <!-- 在线备案表单 -->
  <section class="apply" id="apply">
    <div class="container">
      <div class="title"><h2>藏品在线备案申请</h2><p>填写信息即可提交，工作人员1-3个工作日审核</p></div>
      <div class="form-box">
        <div class="form-item"><label>藏品名称</label><input id="name" placeholder="例：青花龙纹瓶"></div>
        <div class="form-item"><label>藏品类别</label>
          <select id="type">
            <option>瓷器</option><option>玉器</option><option>书画</option><option>铜器</option><option>杂项</option>
          </select>
        </div>
        <div class="form-item"><label>持有人姓名</label><input id="owner"></div>
        <div class="form-item"><label>联系电话</label><input id="phone"></div>
        <div class="form-item"><label>备注说明</label><textarea id="remark" placeholder="简单描述年代、特征等"></textarea></div>
        <button class="btn" style="width:100%" onclick="submitApp()">提交备案申请</button>
        <p style="text-align:center;margin-top:15px;color:#14c9c9;display:none" id="okmsg">提交成功！等待审核</p>
      </div>
    </div>
  </section>

  <!-- 联系我们 -->
  <section class="contact" id="contact">
    <div class="container">
      <div class="title"><h2>联系我们</h2><p>商务合作 | 藏品咨询 | 展览洽谈</p></div>
      <div class="contact-box">
        <div class="contact-item"><i class="fa-solid fa-phone"></i><h4>咨询热线</h4><p>400-888-9999</p></div>
        <div class="contact-item"><i class="fa-solid fa-envelope"></i><h4>邮箱</h4><p>baoli@art.com</p></div>
        <div class="contact-item"><i class="fa-solid fa-location-dot"></i><h4>地址</h4><p>北京·艺术中心大厦</p></div>
      </div>
    </div>
  </section>

  <!-- 底部 -->
  <footer>
    <div class="container">
      <p>保利升煌艺术中心 © 2026 版权所有</p>
      <p>艺术品收藏 | 鉴定 | 备案 | 展览 | 数字化服务</p>
    </div>
  </footer>
</div>

<!-- 季度名额页面 -->
<div class="page" id="pageQuota">
  <header>
    <div class="container nav">
      <button class="back-btn" onclick="goHome()">← 季度名额</button>
      <div class="logo-text">保利升煌艺术中心</div>
    </div>
  </header>
  <div class="container">
    <div class="quota-card">
      <div class="quota-top">2026年·第一季度专项名额</div>
      <div class="quota-row">
        <div class="quota-col">
          <div class="quota-num">20</div>
          <div class="quota-label">本季总名额</div>
          <span class="quota-tag">限量席位</span>
        </div>
        <div class="quota-col">
          <div class="quota-num" style="color:#f7c968">1000</div>
          <div class="quota-label">已参与人数</div>
          <span class="quota-tag">持续增加中</span>
        </div>
      </div>
      <div class="quota-footer">
        <div>
          <span style="margin-right:5px;">⏱</span>
          截止 3月31日 24:00
        </div>
        <div>
          <span style="margin-right:5px;">🔘</span>
          名单公布 4月1日
        </div>
      </div>
    </div>

    <div class="step-card">
      <div class="step-item">
        <div class="step-icon">🏁</div>
        <div class="step-content">
          <h4>报名截止</h4>
          <div class="date">2026年3月31日 24:00</div>
          <p>截止前均可提交抢占申请</p>
        </div>
      </div>
      <div class="step-item">
        <div class="step-icon">📜</div>
        <div class="step-content">
          <h4>公布名单</h4>
          <div class="date">2026年4月1日</div>
          <p>保利升煌艺术中心官方公布本季20名入选藏家名单</p>
        </div>
      </div>
    </div>

    <div class="rule-card">
      <h4>参与资格</h4>
      <p>凡持有经保利升煌艺术中心正式甄选通过藏品的会员藏家，均可参与本季度名额抢占。提交申请即视为登记参与，最终入选名单将于4月1日正式对外公布，入选者将收到中心专属通知。</p>
    </div>

    <div class="list-toggle" id="listToggle">
      <div class="list-left">
        <span class="list-icon">👥</span>
        <span>查看已参与名单</span>
        <span class="list-badge">1000人</span>
      </div>
      <span id="toggleIcon">▼</span>
    </div>

    <div class="list-table" id="listTable">
      <div class="table-header">
        <div>排名</div>
        <div>姓名</div>
        <div>联系电话</div>
        <div>甄选件数</div>
      </div>
      <div class="table-row">
        <div class="rank-1">🏆 1</div>
        <div>苏*</div>
        <div class="phone">177*******</div>
        <div class="count">20件</div>
      </div>
      <div class="table-row">
        <div class="rank-2">🏆 2</div>
        <div>刘*</div>
        <div class="phone">159*******</div>
        <div class="count">20件</div>
      </div>
      <div class="table-row">
        <div class="rank-3">🏆 3</div>
        <div>彭*建</div>
        <div class="phone">136*******</div>
        <div class="count">20件</div>
      </div>
      <div class="table-row">
        <div>4</div>
        <div>丁*敏</div>
        <div class="phone">153*******</div>
        <div class="count">20件</div>
      </div>
      <div class="table-row">
        <div>5</div>
        <div>邓*辉</div>
        <div class="phone">185*******</div>
        <div class="count">20件</div>
      </div>
      <div class="table-row">
        <div>6</div>
        <div>黄*亮</div>
        <div class="phone">138*******</div>
        <div class="count">20件</div>
      </div>
      <div class="table-row">
        <div>7</div>
        <div>马*建</div>
        <div class="phone">189*******</div>
        <div class="count">20件</div>
      </div>
      <div class="table-row">
        <div>8</div>
        <div>韩*国</div>
        <div class="phone">187*******</div>
        <div class="count">20件</div>
      </div>
      <div class="table-row">
        <div>9</div>
        <div>谢*飞</div>
        <div class="phone">157*******</div>
        <div class="count">20件</div>
      </div>
      <div class="table-row">
        <div>10</div>
        <div>郑*</div>
        <div class="phone">133*******</div>
        <div class="count">20件</div>
      </div>
    </div>

    <div class="countdown-card">
      <div class="countdown-title">距报名截止还有</div>
      <div class="countdown-row">
        <div class="countdown-item">
          <div class="countdown-num" id="cdDay">26</div>
          <div class="countdown-unit">天</div>
        </div>
        <div class="countdown-item">
          <div class="countdown-num" id="cdHour">20</div>
          <div class="countdown-unit">时</div>
        </div>
        <div class="countdown-item">
          <div class="countdown-num" id="cdMin">53</div>
          <div class="countdown-unit">分</div>
        </div>
        <div class="countdown-item">
          <div class="countdown-num" id="cdSec">13</div>
          <div class="countdown-unit">秒</div>
        </div>
      </div>
    </div>

    <div class="tip-card">
      提交申请后，请耐心等待至4月1日公布名单，保利升煌艺术中心将通过系统消息及短信通知入选结果。
    </div>

    <button class="btn-full" id="applyBtn">立即抢占名额</button>
  </div>
</div>

<script>
// 页面切换
function goQuota(){
  document.getElementById('pageHome').classList.remove('active');
  document.getElementById('pageQuota').classList.add('active');
  window.scrollTo(0,0);
}
function goHome(){
  document.getElementById('pageQuota').classList.remove('active');
  document.getElementById('pageHome').classList.add('active');
  window.scrollTo(0,0);
}

// 轮播自动切换
const slides = document.querySelectorAll('.slide');
let index = 0;
function play() {
  slides.forEach(s=>s.classList.remove('active'));
  slides[index].classList.add('active');
  index = (index+1) % slides.length;
}
setInterval(play,4000);

// 提交备案表单
const API = "http://localhost:3000/api";
function submitApp(){
  const name = document.getElementById('name').value;
  const owner = document.getElementById('owner').value;
  const phone = document.getElementById('phone').value;
  if(!name||!owner||!phone){alert('请填写完整信息');return}
  fetch(API+'/collection/submit',{
    method:'POST',headers:{'Content-Type':'application/json'},
    body:JSON.stringify({
      name,type:document.getElementById('type').value,
      owner,phone,remark:document.getElementById('remark').value
    })
  }).then(res=>res.json()).then(data=>{
    if(data.code===200){
      document.getElementById('okmsg').style.display='block';
      setTimeout(()=>location.reload(),2000);
    }
  })
}

// 展开/收起名单
const listToggle = document.getElementById('listToggle');
const listTable = document.getElementById('listTable');
const toggleIcon = document.getElementById('toggleIcon');
listToggle.addEventListener('click', () => {
  listTable.classList.toggle('show');
  toggleIcon.textContent = listTable.classList.contains('show') ? '▲' : '▼';
});

// 倒计时
const endDate = new Date("2026-03-31 24:00:00").getTime();
function updateCountdown() {
  const now = new Date().getTime();
  const diff = endDate - now;
  if (diff <= 0) {
    document.getElementById('applyBtn').disabled = true;
    document.getElementById('applyBtn').textContent = '报名已截止';
    return;
  }
  const d = Math.floor(diff / (1000 * 60 * 60 * 24));
  const h = Math.floor((diff % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
  const m = Math.floor((diff % (1000 * 60 * 60)) / (1000 * 60));
  const s = Math.floor((diff % (1000 * 60)) / 1000);
  if(document.getElementById('cdDay')){
    document.getElementById('cdDay').textContent = d;
    document.getElementById('cdHour').textContent = h;
    document.getElementById('cdMin').textContent = m;
    document.getElementById('cdSec').textContent = s;
  }
}
setInterval(updateCountdown, 1000);
updateCountdown();

// 立即抢占名额
document.getElementById('applyBtn').addEventListener('click', () => {
  const name = prompt('请输入您的姓名：');
  const phone = prompt('请输入您的联系电话：');
  if (!name || !phone) return alert('请填写完整信息');
  alert('抢占成功，等待4月1日公布名单');
  location.reload();
});
</script>
</body>
</html>
