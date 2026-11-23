# CARDAPIO-<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<title>Cardápio Digital – Casa do Tambaqui</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Bricolage+Grotesque:wght@400;600;800&display=swap">
<style>
:root{--bg:#EEF3EE;--card:#FFFFFF;--ink:#14261F;--mute:#5B6E65;--line:#D3DED6;--river:#0F4C3A;--on-river:#FFFFFF;--acai:#4A1E57;--sun:#E8B923;--err:#B3261E;
box-sizing:border-box;padding-top:env(safe-area-inset-top,0px);padding-bottom:env(safe-area-inset-bottom,0px)}
@media (prefers-color-scheme:dark){:root:not([data-theme="light"]){--bg:#0E1A15;--card:#16271F;--ink:#E8F0EA;--mute:#9DB1A5;--line:#2A4036;--river:#3FA27F;--on-river:#06140E;--acai:#C79BD6;--sun:#E8B923;--err:#F2867F;color-scheme:dark}}
:root[data-theme="dark"]{--bg:#0E1A15;--card:#16271F;--ink:#E8F0EA;--mute:#9DB1A5;--line:#2A4036;--river:#3FA27F;--on-river:#06140E;--acai:#C79BD6;--sun:#E8B923;--err:#F2867F;color-scheme:dark}
html{scroll-padding-top:env(safe-area-inset-top,0px)}
*{box-sizing:border-box}
body{margin:0;background:var(--bg);color:var(--ink);font-family:"Bricolage Grotesque",system-ui,-apple-system,"Segoe UI",sans-serif;line-height:1.45;min-height:100vh}
main{max-width:560px;margin:0 auto;padding:16px 16px 110px}
header.top{background:var(--river);color:var(--on-river);padding:18px 16px 16px;border-radius:0 0 22px 22px}
header.top .in{max-width:560px;margin:0 auto}
header.top h1{margin:0;font-size:1.5rem;font-weight:800;letter-spacing:-.02em}
header.top p{margin:2px 0 0;opacity:.85;font-size:.9rem}
.pill{display:inline-block;background:var(--sun);color:#2B2200;font-weight:700;font-size:.8rem;padding:3px 10px;border-radius:99px;margin-bottom:8px}
h2{font-size:1.25rem;margin:18px 0 6px;letter-spacing:-.01em}
.card{background:var(--card);border:1px solid var(--line);border-radius:14px;padding:14px;margin:10px 0}
label{display:block;font-weight:600;font-size:.9rem;margin:12px 0 4px}
input[type=text],input[type=tel],input[type=email]{width:100%;font:inherit;padding:12px;border:1.5px solid var(--line);border-radius:10px;background:var(--bg);color:var(--ink)}
input:focus,button:focus-visible{outline:3px solid var(--sun);outline-offset:2px}
.btn{font:inherit;font-weight:700;border:0;border-radius:12px;padding:13px 16px;width:100%;margin-top:14px;background:var(--river);color:var(--on-river);cursor:pointer}
.btn.alt{background:transparent;color:var(--ink);border:1.5px solid var(--line)}
.err{color:var(--err);font-weight:600;font-size:.9rem;margin:8px 0 0}
.mute{color:var(--mute);font-size:.9rem}
.tabs{display:flex;gap:8px;overflow-x:auto;padding:12px 0 4px;margin:0 -16px;padding-left:16px;padding-right:16px}
.tab{flex:none;font:inherit;font-weight:600;padding:8px 14px;border-radius:99px;border:1.5px solid var(--line);background:var(--card);color:var(--ink);cursor:pointer}
.tab[aria-selected=true]{background:var(--acai);border-color:var(--acai);color:#fff}
@media (prefers-color-scheme:dark){.tab[aria-selected=true]{color:#1A0B20}}
.dish{display:flex;gap:12px;justify-content:space-between;align-items:center}
.dish h3{margin:0;font-size:1.05rem}
.dish p{margin:2px 0 6px}
.price{font-weight:800;color:var(--river)}
.step{display:flex;align-items:center;gap:10px}
.step button{width:38px;height:38px;border-radius:50%;border:1.5px solid var(--river);background:transparent;color:var(--river);font:inherit;font-size:1.25rem;font-weight:700;cursor:pointer}
.step b{min-width:18px;text-align:center}
.off{opacity:.55}
.bar{position:fixed;left:0;right:0;bottom:0;background:var(--card);border-top:1px solid var(--line);padding:10px 16px calc(10px + env(safe-area-inset-bottom,0px))}
.bar .in{max-width:560px;margin:0 auto;display:flex;align-items:center;gap:12px}
.bar .btn{margin:0;flex:1}
.row{display:flex;justify-content:space-between;gap:10px;margin:4px 0}
.total{font-size:1.2rem;font-weight:800}
.opt{display:flex;align-items:center;gap:10px;padding:12px;border:1.5px solid var(--line);border-radius:10px;margin:8px 0;cursor:pointer}
.opt input{accent-color:var(--river);width:18px;height:18px}
.ok{width:64px;height:64px;border-radius:50%;background:var(--river);color:var(--on-river);display:grid;place-items:center;font-size:2rem;margin:10px auto}
@media (prefers-reduced-motion:no-preference){.ok{animation:pop .35s ease-out}@keyframes pop{from{transform:scale(.5);opacity:0}}}
</style>
</head>
<body>
<header class="top"><div class="in">
<span class="pill" id="mesaPill"></span>
<h1>Casa do Tambaqui</h1>
<p>Peça direto da sua mesa</p>
</div></header>
<main id="app"></main>
<div class="bar" id="bar" hidden><div class="in"><div><div class="mute" id="barQtd"></div><div class="total" id="barTotal"></div></div><button class="btn" id="barBtn"></button></div></div>

<script>
var CATS=[{id:1,nome:"Entradas"},{id:2,nome:"Pratos principais"},{id:3,nome:"Bebidas"},{id:4,nome:"Sobremesas"}];
var PRATOS=[
{id:1,cat:1,nome:"Tacacá",desc:"Tucupi, jambu, goma e camarão seco.",preco:18},
{id:2,cat:1,nome:"Bolinho de pirarucu",desc:"Seis unidades com molho de pimenta de cheiro.",preco:32},
{id:3,cat:2,nome:"Tambaqui assado",desc:"Posta na brasa, farofa, vinagrete e baião.",preco:79.9},
{id:4,cat:2,nome:"Pirarucu de casaca",desc:"Lascas de pirarucu, banana, ovos e batata.",preco:68},
{id:5,cat:2,nome:"Frango com tucupi",desc:"Coxa desossada, arroz e jambu.",preco:46.5},
{id:6,cat:3,nome:"Suco de cupuaçu",desc:"Copo de 400 ml, com ou sem açúcar.",preco:12},
{id:7,cat:3,nome:"Guaraná Amazônia",desc:"Lata de 350 ml.",preco:7},
{id:8,cat:3,nome:"Caldo de cana",desc:"Copo de 500 ml.",preco:9,off:true},
{id:9,cat:4,nome:"Sorvete de açaí",desc:"Duas bolas com granola e banana.",preco:16},
{id:10,cat:4,nome:"Bolo de macaxeira",desc:"Fatia com calda de tucumã.",preco:14}];
var CLIENTES=[{id:1,nome:"Maria Souza",cpf:"11122233344",tel:"92999990000",email:""}];
var FORMAS=["

