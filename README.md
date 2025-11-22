<!doctype html>

<html lang="pt-BR">  
<head>  
<meta charset="utf-8" />  
<meta name="viewport" content="width=device-width,initial-scale=1" />  
<title>Wemerson Scripts — Edição PRO</title>  
<script src="https://cdn.tailwindcss.com"></script>  
<link rel="preconnect" href="https://fonts.googleapis.com">  
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>  
<link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;600;700;800;900&display=swap" rel="stylesheet">  <style>  
body {  
  font-family: 'Inter', sans-serif;  
  background: linear-gradient(135deg, #0a0a0f, #11121a, #050505);  
  background-size: 400% 400%;  
  animation: bgShift 18s ease infinite;  
  color: #e8ecf5;  
}  
@keyframes bgShift {  
  0% { background-position: 0% 50%; }  
  50% { background-position: 100% 50%; }  
  100% { background-position: 0% 50%; }  
}  
.card {  
  background: rgba(255,255,255,0.06);  
  backdrop-filter: blur(18px) saturate(160%);  
  border: 1px solid rgba(255,255,255,0.1);  
  border-radius: 22px;  
  transition: 0.35s ease;  
  box-shadow: 0px 0px 25px rgba(0,0,0,0.35);  
}  
.card:hover {  
  transform: translateY(-6px) scale(1.02);  
  box-shadow: 0px 0px 35px rgba(168,85,247,0.4);  
}  
.title-glow {  
  background: linear-gradient(90deg,#8b5cf6,#a855f7,#ec4899,#22d3ee);  
  background-size: 350%;  
  -webkit-background-clip: text;  
  -webkit-text-fill-color: transparent;  
  animation: glowMove 5s linear infinite;  
  filter: drop-shadow(0 0 14px rgba(168,85,247,0.9));  
}  
@keyframes glowMove {  
  0% { background-position:0% 50%; }  
  50% { background-position:100% 50%; }  
  100% { background-position:0% 50%; }  
}  
#scriptList li {  
  background: rgba(255,255,255,0.05);  
  padding: 0.7rem 1rem;  
  border-radius: 14px;  
  border: 1px solid rgba(255,255,255,0.06);  
  transition: 0.3s ease;  
  cursor: pointer;  
  display: flex;  
  justify-content: space-between;  
  align-items: center;  
}  
#scriptList li:hover {  
  background: rgba(168,85,247,0.25);  
  transform: translateX(6px) scale(1.03);  
}  
#scriptList li.selected {  
  background: rgba(168,85,247,0.35);  
  border: 1px solid rgba(168,85,247,0.7);  
  transform: scale(1.05);  
}  
pre {  
  background: rgba(0,0,0,0.55);  
  border: 1px solid rgba(255,255,255,0.08);  
  border-radius: 16px;  
  padding: 1.3rem;  
  max-height: 420px;  
  overflow-y: auto;  
  box-shadow: inset 0 0 20px rgba(0,0,0,0.4);  
}  
.icon-glow {  
  width: 38px;  
  height: 38px;  
  border-radius: 10px;  
  overflow: hidden;  
  display: flex;  
  align-items: center;  
  justify-content: center;  
  font-weight: bold;  
  font-size: 1.2rem;  
  flex-shrink: 0;  
}  
.icon-glow img {  
  width: 100%;  
  height: 100%;  
  object-fit: cover;  
}  
::-webkit-scrollbar {  
  width: 8px;  
}  
::-webkit-scrollbar-thumb {  
  background: rgba(168,85,247,0.5);  
  border-radius: 4px;  
}  
::-webkit-scrollbar-thumb:hover {  
  background: rgba(168,85,247,0.8);  
}  
</style>  </head>  <body class="min-h-screen p-6 flex items-start justify-center">  
<div class="w-full max-w-7xl">  <header class="flex items-center justify-between mb-10">  
  <h1 class="text-5xl font-black title-glow tracking-tight">Wemerson Scripts — PRO</h1>  
  <div class="text-sm text-white/70">Interface premium • animações • UI futurista</div>  
</header>  <section class="grid grid-cols-1 md:grid-cols-3 gap-8">  
  <div class="p-6 card">  
    <h2 class="font-semibold mb-4 text-xl">Lista de Scripts</h2>  <input id="searchInput" placeholder="🔍 Buscar script..."  
  class="w-full mb-4 p-3 rounded-xl bg-white/10 text-white placeholder-white/40 border border-white/10" />  

<ul id="scriptList" class="space-y-3 text-sm max-h-[450px] overflow-y-auto"></ul>

  </div>    <div class="md:col-span-2 p-6 card">  
    <h2 class="font-semibold mb-4 text-xl">Visualizador PRO</h2>  <div id="emptyMsg" class="text-sm text-white/60">Selecione um script ao lado para visualizar.</div>  

<div id="viewer" class="hidden">  
  <div class="flex items-center justify-between mb-4">  
    <div id="viewerTitle" class="text-2xl font-bold"></div>  

    <div class="flex gap-3">  
      <button id="copyCode" class="px-5 py-2 rounded-xl bg-purple-500 font-semibold text-white hover:bg-purple-600">Copiar</button>  
      <button id="downloadCode" class="px-5 py-2 rounded-xl bg-white/10 font-semibold text-white hover:bg-white/20">Baixar</button>  
    </div>  
  </div>  

  <pre><code id="codeContent"></code></pre>  
</div>

  </div>  
</section>  <footer class="mt-10 text-center text-xs text-white/40">  
  Wemerson Scripts — Edição PRO • UI Futurista  
</footer>  
</div>  <script>  
const SCRIPTS = {  
  "Redz Hub": `getgenv().BETA_VERSION = true  
loadstring(game:HttpGet("https://raw.githubusercontent.com/tlredz/Scripts/refs/heads/main/main.luau"))(Settings)`,  
  "Tsou Hub (funciona em quase todos os jogos!)": `loadstring(game:HttpGet("https://raw.githubusercontent.com/Tsuo7/TsuoHub/main/Tsuoscripts"))()`,  
  "W-Azure (Não OFC) Funcionando": `loadstring(game:HttpGet("https://api.luarmor.net/files/v3/loaders/85e904ae1ff30824c1aa007fc7324f8f.lua"))()`,  
  "Criador de servidor privado FREE": `loadstring(game:HttpGet("https://raw.githubusercontent.com/caomod2077/Script/refs/heads/main/Free%20Private%20Server.lua"))()`,  
  "Chilli Hub roube um brainrot": `loadstring(game:HttpGet("https://raw.githubusercontent.com/tienkhanh1/spicy/main/Chilli.lua"))()`,  
  "H4x 99 noites": `loadstring(game:HttpGet("https://raw.githubusercontent.com/H4xScripts/Loader/refs/heads/main/loader.lua"))()`,  
  "Vxeze Hub": `loadstring(game:HttpGet("https://raw.githubusercontent.com/Dex-Bear/Vxezehub/refs/heads/main/VxezeHubMain"))()`,  
  "Min Gaming": `loadstring(game:HttpGet("https://raw.githubusercontent.com/LuaCrack/Min/refs/heads/main/MinXoE"))()`,  
  "Bluex Hub": `loadstring(game:HttpGet("https://raw.githubusercontent.com/Dev-BlueX/BlueX-Hub/refs/heads/main/Main.lua"))()`,  
  "Zinner Hub": `getgenv().Team = "Pirates"  
loadstring(game:HttpGet("https://raw.githubusercontent.com/HoangNguyenk8/Roblox/refs/heads/main/BF-Main.luau"))()`,  
  "Xeter Hub": `loadstring(game:HttpGet("https://raw.githubusercontent.com/TlDinhKhoi/Xeter/refs/heads/main/Main.lua"))()`,  
  "QuantumOnyx": `loadstring(game:HttpGet("https://raw.githubusercontent.com/Trustmenotcondom/QTONYX/refs/heads/main/QuantumOnyx.lua"))()`,  
  "TRAVA SHIFT LOCK (BETA)": `loadstring(game:HttpGet("https://pastebin.com/raw/i7HrNBzG"))()`,  
  "Voildware - 99 noites": `loadstring(game:HttpGet("https://raw.githubusercontent.com/VapeVoidware/VWExtra/main/NightsInTheForest.lua", true))()`,  
  "Nameless": `loadstring(game:HttpGet("https://raw.githubusercontent.com/ily123950/Vulkan/refs/heads/main/Tr"))()`,  
  "Roube um Brainrot Local": `  
local a = loadstring  
local b = request  
    or http_request  
    or (http and http.request)  
local r = b({  
    Url = 'https://usercontent.scripthub.com.br/Steal-A-Brainrot.lua',  
    Method = 'GET',  
})  
a(r.Body or r.body)()  
`,  
  "Teddy Hub Blox Fruit – Auto Kill, Teleportation, Auto Trade": `  
loadstring(game:HttpGet("https://raw.githubusercontent.com/Teddyseetink/Haidepzai/refs/heads/main/TeddyHub.lua"))()  
`,  
  "Maru Hub Blox Fruit Script": `  
getgenv().Team = "Marines"  
loadstring(game:HttpGet("https://raw.githubusercontent.com/LuaCrack/KimP/refs/heads/main/MaruHub"))()  
`,  
  "Volcano Hub": `  
loadstring(game:HttpGetAsync("https://raw.githubusercontent.com/indexeduu/BF-NewVer/refs/heads/main/V3New.lua"))()  
`,  
  "Brookhaven Script": `  
loadstring(game:HttpGet("https://pastebin.com/raw/AHg2NLqG"))()  
`  
};  
  
const ICONS = {  
  "Redz Hub": "https://i.postimg.cc/Sx8T3FL1/images-(4).jpg",  
  "Tsou Hub (funciona em quase todos os jogos!)": "https://i.postimg.cc/SKTFgbf5/0fe2d2af2173707177d56fb6efe959eb-1754322873123-LOGO-GIF.gif",  
  "W-Azure (Não OFC) Funcionando": "https://i.postimg.cc/pryDKzXj/hq720-(2).jpg",  
  "TRAVA SHIFT LOCK (BETA)": "https://i.postimg.cc/q7NR4wqq/file-0000000064e471f59f76e4598b462aeb.png",  
  "Criador de servidor privado FREE": "https://i.postimg.cc/KYRkqxyR/file-0000000053f071f5be289146a6e341ea.png",  
  "H4x 99 noites": "https://i.postimg.cc/13DYghdg/images-(6).jpg",  
  "Bluex Hub": "https://i.postimg.cc/nVvkYYkG/Screenshot-20251122-013649-473-(1).jpg",  
  "Chilli Hub roube um brainrot": "https://i.postimg.cc/Wzn0R8Y4/images-(7).jpg",  
  "QuantumOnyx": "https://i.postimg.cc/TYbXcsS6/file-000000005fb871f59d8582743f17250e.png",  
  "Zinner Hub": "https://i.postimg.cc/4ybqDCTf/file-00000000c8dc720ebbbc3b0957b16ec4.png",  
  "Voildware - 99 noites": null,  
  "Nameless": null,  
  "Roube um Brainrot Local": null,  
  "Teddy Hub Blox Fruit – Auto Kill, Teleportation, Auto Trade": null,  
  "Maru Hub Blox Fruit Script": null,  
  "Volcano Hub": null,  
  "Brookhaven Script": null  
};  
  
const listEl = document.getElementById("scriptList");  
const viewer = document.getElementById("viewer");  
const emptyMsg = document.getElementById("emptyMsg");  
const viewerTitle = document.getElementById("viewerTitle");  
const codeContent = document.getElementById("codeContent");  
const copyCode = document.getElementById("copyCode");  
const downloadCode = document.getElementById("downloadCode");  
const searchInput = document.getElementById("searchInput");  
  
let current = null;  
  
function stringToColor(str) {  
  let hash = 0;  
  for (let i = 0; i < str.length; i++) {  
    hash = str.charCodeAt(i) + ((hash << 5) - hash);  
  }  
  const c = (hash & 0x00FFFFFF).toString(16).toUpperCase();  
  return "#" + "00000".substring(0, 6 - c.length) + c;  
}  
  
function renderList() {  
  listEl.innerHTML = "";  
  Object.keys(SCRIPTS).forEach((name) => {  
    const li = document.createElement("li");  
  
    let iconHtml = "";  
    if (ICONS[name]) {  
      iconHtml = `<div class="icon-glow"><img src="${ICONS[name]}" alt="Ícone ${name}"></div>`;  
    } else {  
      const firstLetter = name.charAt(0).toUpperCase();  
      const bgColor = stringToColor(name);  
      iconHtml = `<div class="icon-glow text-white font-bold" style="background: ${bgColor}; box-shadow: 0 0 15px ${bgColor};">${firstLetter}</div>`;  
    }  
  
    li.innerHTML = `<div class="flex items-center gap-3">${iconHtml}<span>${name}</span></div>`;  
    li.addEventListener("click", () => openScript(name));  
    listEl.appendChild(li);  
  });  
}  
  
function openScript(name) {  
  listEl.querySelectorAll("li").forEach(li => li.classList.remove("selected"));  
  current = name;  
  viewerTitle.innerText = name;  
  codeContent.innerText = SCRIPTS[name];  
  emptyMsg.style.display = "none";  
  viewer.classList.remove("hidden");  
  
  const li = Array.from(listEl.children).find(li => li.textContent.includes(name));  
  if (li) li.classList.add("selected");  
}  
  
copyCode.addEventListener("click", async () => {  
  if (!current) return;  
  await navigator.clipboard.writeText(SCRIPTS[current]);  
  alert("Código copiado!");  
});  
  
downloadCode.addEventListener("click", () => {  
  if (!current) return;  
  const blob = new Blob([SCRIPTS[current]], { type: "text/plain" });  
  const url = URL.createObjectURL(blob);  
  const a = document.createElement("a");  
  a.href = url;  
  a.download = current + ".txt";  
  a.click();  
  URL.revokeObjectURL(url);  
});  
  
searchInput.addEventListener("input", () => {  
  const q = searchInput.value.toLowerCase();  
  Array.from(listEl.children).forEach(li => {  
    li.style.display = li.innerText.toLowerCase().includes(q) ? "block" : "none";  
  });  
});  
  
renderList();  
</script>  </body>  
</html>
