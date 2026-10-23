<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>My Site</title>
<style>
:root{--bg:#1b1030;--panel:#2a1b4a;--panel2:#3a2766;--ink:#fff7e8;--muted:#b9a9de;--coral:#ff5d73;--cyan:#3ee0cf;--butter:#ffe27a}
*{box-sizing:border-box}
html{background:var(--bg)}
body{margin:0;min-height:100vh;color:var(--ink);font-family:"Trebuchet MS",Verdana,sans-serif;line-height:1.6;
 background-color:var(--bg);background-attachment:fixed;
 background-image:
  radial-gradient(circle at 15% 0,rgba(110,60,210,.55) 0,transparent 45%),
  radial-gradient(circle at 95% 100%,rgba(255,93,115,.35) 0,transparent 45%),
  radial-gradient(circle at 70% 30%,rgba(62,224,207,.12) 0,transparent 35%),
  linear-gradient(rgba(255,255,255,.04) 1px,transparent 1px),
  linear-gradient(90deg,rgba(255,255,255,.04) 1px,transparent 1px);
 background-size:auto,auto,auto,40px 40px,40px 40px}
button{font:inherit;cursor:pointer}
a{color:var(--cyan)}
:focus-visible{outline:3px solid var(--butter);outline-offset:3px}
.wrap{max-width:760px;margin:0 auto;padding:0 20px}
header{padding:48px 0 10px}
h1{margin:0;font-family:"Arial Black",Impact,sans-serif;font-size:clamp(2.4rem,8vw,4.4rem);line-height:1;letter-spacing:-.02em;
 color:var(--butter);text-shadow:4px 4px 0 var(--coral)}
header p{margin:16px 0 0;color:var(--muted);max-width:46ch}
/* Text list (no boxes) */
.list{margin:36px 0 50px;padding:0;list-style:none}
.list li{border-top:1px solid rgba(255,247,232,.18)}
.list li:last-child{border-bottom:1px solid rgba(255,247,232,.18)}
.item{display:block;width:100%;text-align:left;background:none;border:0;color:var(--ink);padding:18px 4px;transition:padding .15s}
.item b{display:block;font-size:1.35rem;transition:color .15s}
.item span{color:var(--muted)}
.item:hover{padding-left:14px}
.item:hover b{color:var(--butter)}
/* Detail page */
#detail{display:none;padding:30px 0 50px}
.back{background:none;border:0;color:var(--cyan);padding:0;margin-bottom:18px;font-size:1rem}
.back:hover{text-decoration:underline}
#dtitle{margin:0 0 14px;font-size:2rem;color:var(--butter)}
.page h3{margin-top:0}
.btn{display:inline-block;background:var(--coral);color:#fff;border:0;border-radius:10px;padding:10px 20px;font-weight:bold;text-decoration:none}
footer{padding:0 0 34px;color:var(--muted);font-size:.85rem}
@media (prefers-reduced-motion:reduce){*{transition:none!important}}
</style>
</head>
<body>
<div class="wrap">
  <header>
    <h1 id="siteTitle"></h1>
    <p id="siteTag"></p>
  </header>

  <main id="home"><ul class="list" id="list"></ul></main>

  <main id="detail">
    <button class="back" id="back">&larr; Back</button>
    <h2 id="dtitle"></h2>
    <div class="page" id="dbody"></div>
  </main>

  <footer id="siteFoot"></footer>
</div>

<script>

const SITE = {
  title: "My Site",
  tagline: "A short sentence about what this site is for.",
  footer: "Made by your name."
};


const ITEMS = [
  {
    title: "First thing",
    desc: "One line about it.",
    content: `
      <p>Write whatever you want here. You can use normal HTML: paragraphs, lists, images, links.</p>
      <a class="btn" href="#">A button</a>`
  },
  {
    title: "Second thing",
    desc: "One line about it.",
    content: `<p>Replace this text with your own.</p>`
  },
  {
    title: "Third thing",
    desc: "One line about it.",
    content: `<p>Replace this text with your own.</p>`
  },
  {
    title: "About me",
    desc: "Who made this.",
    content: `<p>Say hi and tell people a bit about you or your project.</p>`
  }
];


const $ = id => document.getElementById(id);
document.title = SITE.title;
$('siteTitle').textContent = SITE.title;
$('siteTag').textContent = SITE.tagline;
$('siteFoot').textContent = SITE.footer;

ITEMS.forEach((it, i) => {
  const li = document.createElement('li');
  const b = document.createElement('button');
  b.className = 'item';
  b.innerHTML = '<b>' + it.title + '</b><span>' + it.desc + '</span>';
  b.onclick = () => show(i);
  li.appendChild(b);
  $('list').appendChild(li);
});

function show(i) {
  $('dtitle').textContent = ITEMS[i].title;
  $('dbody').innerHTML = ITEMS[i].content;
  $('home').style.display = 'none';
  $('detail').style.display = 'block';
  window.scrollTo(0, 0);
}
$('back').onclick = () => {
  $('detail').style.display = 'none';
  $('home').style.display = 'block';
};
</script>
</body>
</html>
