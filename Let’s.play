<!DOCTYPE html>
<html>
<head>
    <title>lets.play</title>
    <style>
        body { font-family: Arial; background:#f0f0f0; display:flex; }
        #sidebar { width: 250px; background:#222; color:white; padding:20px; height:100vh; overflow-y:auto; }
        #content { flex:1; padding:20px; }
        .game-link { display:block; padding:5px 0; color:#9cf; cursor:pointer; }
        iframe { width:100%; height:600px; border:1px solid #ccc; }

        #chat-box { position:fixed; bottom:10px; right:10px; width:300px; background:white; border:1px solid #aaa; }
        #messages { height:200px; overflow-y:auto; padding:10px; }
        #input { width:100%; box-sizing:border-box; }
    </style>
</head>
<body>

<div id="sidebar">
    <h2>lets.play – Games</h2>
    <div id="game-list"></div>
</div>

<div id="content">
    <h2>Game Viewer</h2>
    <iframe id="game-frame" src=""></iframe>
</div>

<!-- Simple Chat -->
<div id="chat-box">
    <div id="messages"></div>
    <input id="input" placeholder="Type a message…">
</div>

<script>
// ----- Game List -----
let games = [];
for (let i = 1; i <= 200; i++) {
    games.push({name:"Game " + i, url:"https://example.com/game" + i});
}

let list = document.getElementById("game-list");
games.forEach(g => {
    let d = document.createElement("div");
    d.className = "game-link";
    d.textContent = g.name;
    d.onclick = () => document.getElementById("game-frame").src = g.url;
    list.appendChild(d);
});

// ----- Simple Chat (Local Only) -----
let messages = JSON.parse(localStorage.getItem("chatMessages") || "[]");

function renderMessages() {
    let box = document.getElementById("messages");
    box.innerHTML = messages.map(m => `<div>${m}</div>`).join("");
    box.scrollTop = box.scrollHeight;
}
renderMessages();

document.getElementById("input").addEventListener("keypress", e => {
    if (e.key === "Enter") {
        messages.push(e.target.value);
        localStorage.setItem("chatMessages", JSON.stringify(messages));
        e.target.value = "";
        renderMessages();
    }
});
</script>

</body>
</html>
