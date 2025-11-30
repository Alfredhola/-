<!DOCTYPE html>
<html lang="zh-TW">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>RG Golf Pairing V13 (UI & Clean Names)</title>
<style>
    :root {
        --rg-clay: #CB5A46;
        --rg-navy: #002D56;
        --rg-green: #004E38;
        --rg-white: #FFFFFF;
        --rg-grey: #F3F3F3;
        --rg-female: #C2185B; /* 女性顏色 */
        --rg-male: #002D56;    /* 男性顏色 */
        --border-radius: 8px;
    }

    body {
        font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif;
        background-color: var(--rg-grey); color: var(--rg-navy);
        margin: 0; padding: 0; display: flex; flex-direction: column; min-height: 100vh;
    }

    /* Header */
    header {
        background-color: var(--rg-navy); color: var(--rg-white);
        padding: 15px 20px; display: flex; justify-content: space-between; align-items: center;
        box-shadow: 0 2px 10px rgba(0,0,0,0.1); position: sticky; top: 0; z-index: 100;
    }
    header h1 { margin: 0; font-size: 20px; font-weight: 700; letter-spacing: 1px; }

    .container { max-width: 600px; margin: 0 auto; padding: 15px; width: 100%; box-sizing: border-box; flex: 1; }

    /* Steps */
    .step-indicator {
        display: flex; margin-bottom: 20px; background: white;
        border-radius: 50px; padding: 4px; box-shadow: 0 2px 6px rgba(0,0,0,0.06);
    }
    .step {
        flex: 1; text-align: center; padding: 8px; font-size: 13px; font-weight: 600;
        color: #bbb; cursor: pointer; border-radius: 40px; transition: 0.2s;
    }
    .step.active { background-color: var(--rg-clay); color: white; }

    /* Cards */
    .card {
        background: var(--rg-white); padding: 20px;
        border-radius: var(--border-radius); box-shadow: 0 4px 12px rgba(0,0,0,0.05);
        margin-bottom: 20px;
    }
    .card h2 {
        margin-top: 0; font-size: 16px; text-transform: uppercase; color: var(--rg-navy);
        border-left: 5px solid var(--rg-clay); padding-left: 10px; margin-bottom: 15px;
    }

    textarea {
        width: 100%; height: 150px; padding: 12px;
        border: 1px solid #ddd; border-radius: 6px; background: #fafafa;
        font-family: monospace; font-size: 15px; resize: none; box-sizing: border-box;
    }
    textarea:focus { outline: none; border-color: var(--rg-navy); background: #fff; }

    /* Buttons */
    .btn {
        padding: 14px; border: none; border-radius: 6px;
        font-size: 15px; font-weight: 600; cursor: pointer; text-transform: uppercase;
        display: flex; align-items: center; justify-content: center; gap: 8px;
        width: 100%; box-sizing: border-box; margin-top: 10px;
        transition: 0.2s; box-shadow: 0 2px 5px rgba(0,0,0,0.1);
    }
    .btn:active { transform: translateY(1px); box-shadow: none; }
    .btn-primary { background-color: var(--rg-clay); color: white; }
    .btn-secondary { background-color: var(--rg-navy); color: white; }
    .btn-outline { background: white; border: 1px solid #ddd; color: #666; box-shadow: none; }
    .btn-green { background: var(--rg-green); color: white; }
    .btn:disabled { background-color: #ddd; color: #888; cursor: not-allowed; box-shadow: none; }

    /* List Items in Edit View */
    .assign-list { display: flex; flex-direction: column; gap: 8px; }
    .assign-item {
        display: flex; align-items: center; justify-content: space-between;
        padding: 8px 12px; background: #fff; border: 1px solid #eee; border-radius: 6px;
    }
    .name-edit {
        border: none; background: transparent; font-weight: bold; color: var(--rg-navy);
        font-size: 15px; width: 120px; padding: 4px 0;
        border-bottom: 1px solid transparent; transition: 0.2s;
    }
    .name-edit:focus { outline: none; border-bottom: 1px solid var(--rg-clay); background: #fffff0; }

    .hcp-input {
        width: 40px; padding: 6px; border: 1px solid #ddd; border-radius: 4px; 
        text-align: center; font-family: monospace; font-weight: bold; color: #555;
    }
    
    .gender-toggle {
        width: 30px; height: 30px; display: flex; align-items: center; justify-content: center;
        border-radius: 50%; cursor: pointer; border: 1px solid #eee; margin-right: 10px; font-size: 16px;
    }
    .gender-toggle.female { background: #ffeef5; color: var(--rg-female); }
    .gender-toggle.male { background: #eef7ff; color: var(--rg-male); }

    .btn-del {
        background: none; border: none; color: #ccc; font-size: 20px; cursor: pointer; margin-left: 8px;
    }
    .btn-del:hover { color: #e74c3c; }

    /* Scorecard Results */
    .scorecard {
        background: white; border-radius: 8px; overflow: hidden; margin-bottom: 15px;
        box-shadow: 0 4px 10px rgba(0,0,0,0.05); 
        border: 1px solid #eee; border-top: 5px solid var(--rg-clay);
    }
    .scorecard.invalid { border-color: #e74c3c; border-top-width: 5px; }

    .scorecard-header {
        padding: 12px 15px; background: #fff; display: flex; justify-content: space-between; align-items: center;
        border-bottom: 1px solid #f0f0f0;
    }
    .group-title { font-weight: 800; color: var(--rg-navy); font-size: 14px; letter-spacing: 0.5px; }

    /* UI Arrows for Ordering */
    .order-controls { display: flex; gap: 4px; }
    .btn-icon {
        background: #f7f7f7; border: 1px solid #eee; border-radius: 4px;
        color: #666; cursor: pointer; padding: 4px 10px; font-size: 14px;
        transition: 0.2s;
    }
    .btn-icon:hover { background: #eee; color: var(--rg-navy); }
    
    table { width: 100%; border-collapse: collapse; font-size: 14px; }
    td { padding: 10px 15px; border-bottom: 1px solid #f9f9f9; vertical-align: middle; }
    tr:last-child td { border-bottom: none; }

    /* Name Coloring */
    .p-name { font-weight: 600; font-size: 15px; }
    .p-name.male { color: var(--rg-male); }
    .p-name.female { color: var(--rg-female); }

    .hidden { display: none !important; }
    
    .select-move {
        padding: 4px; border: 1px solid #eee; border-radius: 4px;
        color: #999; font-size: 11px; margin-left: 8px;
    }
</style>
</head>
<body>

<header>
    <h1>RG PAIRING V13</h1>
    <div style="font-size:11px; opacity:0.8; font-weight:normal;">UI & CLEAN NAMES</div>
</header>

<div class="container">
    
    <div class="step-indicator">
        <div class="step active" id="tab-1" onclick="goToStep(1)">1. 輸入</div>
        <div class="step" id="tab-2" onclick="goToStep(2)">2. 編輯</div>
        <div class="step" id="tab-3">3. 結果</div>
    </div>

    <!-- STEP 1: Input -->
    <div id="view-1">
        <div class="card">
            <h2>名單輸入</h2>
            <p style="font-size:13px; color:#666; margin-bottom:12px; line-height:1.5;">
                請輸入名單。系統將自動：<br>
                1. 辨識性別與中文姓名<br>
                2. 移除性別符號，並將中文名置前
            </p>
            <textarea id="input-text" placeholder="格式範例：&#10;Jason 林 12&#10;王小明 18&#10;Vikki ❤️ 24"></textarea>
            
            <button class="btn btn-primary" onclick="processInput()">下一步：解析名單 ➔</button>
        </div>
        <div style="text-align:center;">
             <button class="btn btn-outline" style="width:auto; display:inline-block; padding:8px 20px;" onclick="loadDemoData()">載入範例資料</button>
        </div>
    </div>

    <!-- STEP 2: Configure & Edit -->
    <div id="view-2" class="hidden">
        <div class="card">
            <h2>編輯名單</h2>
            <div style="margin-bottom:10px; font-size:12px; color:#666; text-align:right;">
                <span id="player-count-info"></span>
            </div>
            
            <div style="display:flex; gap:5px; margin-bottom:15px; border-bottom:1px dashed #ddd; padding-bottom:15px;">
                <input id="new-name" class="name-edit" style="flex:2; border:1px solid #ddd; border-radius:4px; padding:8px;" placeholder="姓名">
                <input id="new-hcp" type="number" class="hcp-input" style="flex:1; width:auto;" placeholder="HCP">
                <button class="btn-secondary" style="width:50px; margin:0; padding:0;" onclick="manualAddPlayer()">+</button>
            </div>

            <div class="assign-list" id="player-list"></div>

            <div style="margin-top:20px; border-top:1px solid #eee; padding-top:20px;">
                <div style="margin-bottom:12px;">
                    <label style="font-size:12px; font-weight:700; color:#666; display:block; margin-bottom:6px;">分組策略 (HCP)</label>
                    <select id="hcp-logic" style="width:100%; padding:10px; border:1px solid #ddd; border-radius:6px; font-size:14px;">
                        <option value="total_balanced" selected>⚖️ 實力平均 (每組總差點接近)</option>
                        <option value="competitive">⚔️ 組內競爭 (同組差點相近)</option>
                    </select>
                </div>
                
                <div style="margin-bottom:12px;">
                    <label style="font-size:12px; font-weight:700; color:#666; display:block; margin-bottom:6px;">性別分配</label>
                    <select id="gender-logic" style="width:100%; padding:10px; border:1px solid #ddd; border-radius:6px; font-size:14px;">
                        <option value="balanced" selected>👫 男女混編 (平均分配)</option>
                        <option value="random">🎲 隨機分配</option>
                    </select>
                </div>

                <button class="btn btn-secondary" onclick="generateResult()">執行分組演算 ⛳</button>
            </div>
        </div>
    </div>

    <!-- STEP 3: Results -->
    <div id="view-3" class="hidden">
        <div style="margin-bottom:15px; display:flex; gap:10px;">
            <button class="btn btn-outline" style="margin:0; flex:1;" onclick="goToStep(1)">↺ 重來</button>
            <button id="btn-export" class="btn btn-green" style="margin:0; flex:2;" onclick="exportText()" disabled>📋 複製文字名單</button>
        </div>
        
        <div id="result-container"></div>
    </div>

</div>

<script>
    let allPlayers = [];
    const MIN_PER_GROUP = 3;
    const MAX_PER_GROUP_STRICT = 4;
    const MANUAL_MAX_PER_GROUP = 5;

    let MAX_POSSIBLE_GROUPS = 0; 
    let finalGroups = []; 
    let idCounter = 1;

    function loadDemoData() {
        document.getElementById('input-text').value = 
`1. Jason 林 12
2. 👑 5
3. vikki 左浩毓❤️ 24
4. Philip 呂宥林 8
5. ReeAnne 洪藜恩♥️ 28
6. 💋 18
7. Amy 陳 30
8. Kevin Wang 5`;
    }

    // --- 1. Parsing Logic (Clean & Reorder) ---
    function processInput() {
        const raw = document.getElementById('input-text').value.trim();
        if (!raw) { alert("請輸入資料"); return; }
        
        const lines = raw.split('\n');
        allPlayers = [];
        idCounter = 1;
        
        const femaleKeywords = ["Mrs", "Ms", "Miss", "Lady", "女", "姐", "妹"];
        const femaleEmojiString = "🩷❤️🧡💛💜💙🩵💚🖤🩶🤍🤎💕💞💓💗❣️💖💘💝💟🧘‍♀️✨⭐️🌟🌹🦄👑👠👗👙🙋‍♀️🙎‍♀️🙆‍♀️💁‍♀️👸🏻👩‍🦰👩🏻👧💋😍";
        const femaleEmojis = [...femaleEmojiString]; 
        const leadingNumbers = /^[\d\.\s\)\-\]]+/;

        lines.forEach(line => {
            let cleanLine = line.trim();
            if (!cleanLine) return;
            cleanLine = cleanLine.replace(leadingNumbers, '').trim(); 

            let hcp = 0;
            const hcpMatch = cleanLine.match(/(\d+(\.\d+)?)$/);
            if (hcpMatch) {
                hcp = parseFloat(hcpMatch[0]);
                cleanLine = cleanLine.substring(0, hcpMatch.index).trim();
            }

            // Detect Gender
            let isFemale = false;
            if (new RegExp(femaleKeywords.join('|'), 'i').test(cleanLine)) isFemale = true;
            if (femaleEmojis.some(emoji => cleanLine.includes(emoji))) isFemale = true;

            // Clean Name: Remove Gender Keywords & Gender Emojis
            let namePart = cleanLine;
            namePart = namePart.replace(new RegExp(femaleKeywords.join('|'), 'gi'), '');
            // Remove specific gender symbols
            femaleEmojis.forEach(e => { namePart = namePart.split(e).join(''); });
            
            namePart = namePart.trim();

            // Fallback: If name became empty (e.g. only had symbol), use original stripped of numbers
            if(namePart.length === 0) {
                 // Try to keep at least something recognizable, or generic
                 namePart = cleanLine.trim() || "Player"; 
            }

            // Reorder: Chinese First, English Second
            const chineseMatch = namePart.match(/[\u4e00-\u9fa5]+/g);
            const chineseStr = chineseMatch ? chineseMatch.join('') : "";
            
            // Remove Chinese characters to get English/Symbols part
            let engStr = namePart.replace(/[\u4e00-\u9fa5]+/g, '').trim();

            let finalName = "";
            if (chineseStr && engStr) {
                finalName = `${chineseStr} ${engStr}`;
            } else {
                finalName = chineseStr || engStr;
            }

            allPlayers.push({
                id: idCounter++,
                name: finalName,
                hcp: hcp, 
                gender: isFemale ? 'F' : 'M',
                group: 0
            });
        });

        updateMaxGroups();
        renderPlayerList();
        goToStep(2);
    }

    function updateMaxGroups() {
        if (allPlayers.length === 0) return;
        MAX_POSSIBLE_GROUPS = Math.floor(allPlayers.length / 3);
        if(MAX_POSSIBLE_GROUPS < 1) MAX_POSSIBLE_GROUPS = 1;
        MAX_POSSIBLE_GROUPS += 1; // Allow one extra for flexibility
        document.getElementById('player-count-info').innerText = `共 ${allPlayers.length} 人`;
    }

    // --- 2. Edit UI ---
    
    function manualAddPlayer() {
        const nameInput = document.getElementById('new-name');
        const hcpInput = document.getElementById('new-hcp');
        const name = nameInput.value.trim();
        const hcp = parseFloat(hcpInput.value) || 0;

        if (name) {
            allPlayers.push({ id: idCounter++, name: name, hcp: hcp, gender: 'M', group: 0 });
            nameInput.value = ''; hcpInput.value = '';
            updateMaxGroups(); renderPlayerList();
        }
    }

    function updatePlayerName(pid, val) { allPlayers.find(x => x.id === pid).name = val.trim(); }
    function updatePlayerHcp(pid, val) { allPlayers.find(x => x.id === pid).hcp = parseFloat(val) || 0; }
    function deletePlayer(pid) { allPlayers = allPlayers.filter(p => p.id !== pid); updateMaxGroups(); renderPlayerList(); }
    function toggleGender(pid) { 
        const p = allPlayers.find(x => x.id === pid);
        if (p) { p.gender = p.gender === 'M' ? 'F' : 'M'; renderPlayerList(); }
    }

    function renderPlayerList() {
        const listDiv = document.getElementById('player-list');
        listDiv.innerHTML = "";

        allPlayers.forEach(p => {
            const div = document.createElement('div');
            div.className = `assign-item`;
            const genderClass = p.gender === 'F' ? 'female' : 'male';
            const genderIcon = p.gender === 'F' ? '♀' : '♂';

            div.innerHTML = `
                <div style="display:flex; align-items:center;">
                    <div class="gender-toggle ${genderClass}" onclick="toggleGender(${p.id})">${genderIcon}</div>
                    <input type="text" class="name-edit" value="${p.name}" onchange="updatePlayerName(${p.id}, this.value)">
                </div>
                <div style="display:flex; align-items:center;">
                    <input type="number" class="hcp-input" value="${p.hcp}" onchange="updatePlayerHcp(${p.id}, this.value)">
                    <button class="btn-del" onclick="deletePlayer(${p.id})">×</button>
                </div>
            `;
            listDiv.appendChild(div);
        });
    }

    // --- 3. Algorithm ---
    function generateResult() {
        if(allPlayers.length === 0) return;
        const genderLogic = document.getElementById('gender-logic').value; 
        const hcpLogic = document.getElementById('hcp-logic').value;
        
        // Simple Reset & Calculation logic
        // For UI simplicity, we just recalculate optimal groups based on list
        let pool = [...allPlayers];
        
        // Sort Pool
        if(genderLogic === 'balanced') {
            pool.sort((a,b) => {
                if(a.gender !== b.gender) return a.gender === 'F' ? -1 : 1; // F first
                return b.hcp - a.hcp;
            });
        } else {
            pool.sort((a,b) => b.hcp - a.hcp);
        }

        const totalPeople = pool.length;
        const numGroups = Math.ceil(totalPeople / 4);
        let groups = Array.from({length: numGroups}, () => []);

        // Snake distribution or Balance logic
        if (hcpLogic === 'total_balanced') {
             // Zigzag distribution by HCP
             // But first, separate genders if balanced logic is strict? 
             // Let's use simple snake fill
             pool.sort((a,b) => b.hcp - a.hcp); // Strict HCP sort
             
             // If Gender balanced is required, we distribute Ladies first
             if(genderLogic === 'balanced') {
                 const ladies = pool.filter(p=>p.gender==='F');
                 const men = pool.filter(p=>p.gender==='M');
                 
                 // Distribute Ladies
                 let gIdx = 0;
                 ladies.forEach(p => {
                     groups[gIdx].push(p);
                     gIdx = (gIdx + 1) % numGroups;
                 });
                 // Distribute Men (reverse direction to balance HCP?)
                 // Simple fill for now
                 men.forEach(p => {
                     // Find group with lowest total HCP or fewer people
                     // Simple round robin
                     groups[gIdx].push(p);
                     gIdx = (gIdx + 1) % numGroups;
                 });
             } else {
                 // Pure Snake
                 pool.forEach((p, i) => {
                     const pos = i % numGroups;
                     const gIdx = (Math.floor(i / numGroups) % 2 === 0) ? pos : (numGroups - 1 - pos);
                     groups[gIdx].push(p);
                 });
             }

        } else {
            // Competitive: Group by HCP chunks
            // 1-4 in G1, 5-8 in G2
            pool.sort((a,b) => a.hcp - b.hcp); // Low hcp first
            pool.forEach((p, i) => {
                const gIdx = Math.floor(i / 4);
                if(groups[gIdx]) groups[gIdx].push(p);
                else groups[groups.length-1].push(p); // Overflow
            });
        }

        // Assign Group IDs back to object
        groups.forEach((g, idx) => {
            g.forEach(p => p.group = idx + 1);
        });
        finalGroups = groups;
        renderResults();
        goToStep(3);
    }

    // --- 4. Render Results (Clean UI) ---
    function renderResults() {
        const container = document.getElementById('result-container');
        const btnExport = document.getElementById('btn-export');
        container.innerHTML = "";
        let allValid = true; 

        finalGroups.forEach((g, idx) => {
            if(g.length === 0) return;
            
            const totalHcp = g.reduce((s,p)=>s+p.hcp,0);
            
            // Sort by HCP inside group for display
            g.sort((a,b) => a.hcp - b.hcp);

            let isValid = (g.length >= MIN_PER_GROUP && g.length <= MAX_PER_GROUP_STRICT);
            if (!isValid) allValid = false;
            
            let cardClass = isValid ? "scorecard" : "scorecard invalid";

            let rows = g.map(p => {
                // Color class based on gender
                const colorClass = p.gender === 'F' ? 'female' : 'male';
                
                // Move Select
                let moveOpts = "";
                for(let i=0; i<finalGroups.length; i++) {
                     let selected = (i === idx) ? "selected" : "";
                     moveOpts += `<option value="${i}" ${selected}>G${i+1}</option>`;
                }

                return `
                <tr>
                    <td>
                        <div style="display:flex; align-items:center;">
                            <span class="p-name ${colorClass}">${p.name}</span>
                            <select class="select-move" onchange="manualMove(${p.id}, ${idx}, this.value)">${moveOpts}</select>
                        </div>
                    </td>
                    <td style="text-align:right; font-family:monospace; font-weight:bold; color:#666;">${p.hcp}</td>
                </tr>`;
            }).join('');

            // UI Buttons (Simple Arrows)
            let upBtn = idx > 0 ? `<button class="btn-icon" onclick="moveGroupOrder(${idx}, -1)">▲</button>` : `<button class="btn-icon" style="visibility:hidden">▲</button>`;
            let downBtn = idx < finalGroups.length - 1 ? `<button class="btn-icon" onclick="moveGroupOrder(${idx}, 1)">▼</button>` : `<button class="btn-icon" style="visibility:hidden">▼</button>`;

            container.innerHTML += `
                <div class="${cardClass}">
                    <div class="scorecard-header">
                        <div class="group-title">GROUP ${idx+1}</div>
                        <div class="order-controls">
                            ${upBtn} ${downBtn}
                        </div>
                    </div>
                    <table>${rows}</table>
                    <div style="padding:8px 15px; background:#fafafa; font-size:12px; color:#888; text-align:right; border-top:1px solid #eee;">
                        Total HCP: <strong>${totalHcp.toFixed(1)}</strong>
                    </div>
                </div>`;
        });

        if (allValid && finalGroups.length > 0) {
            btnExport.disabled = false;
            btnExport.textContent = "📋 複製文字名單";
            btnExport.classList.add('btn-green');
        } else {
            btnExport.disabled = true;
            btnExport.textContent = "⚠️ 請修正人數 (3-4人)";
            btnExport.classList.remove('btn-green');
        }
    }

    function manualMove(pid, fromIdx, toIdx) {
        fromIdx = parseInt(fromIdx); toIdx = parseInt(toIdx);
        if(fromIdx === toIdx) return;
        if(finalGroups[toIdx].length >= MANUAL_MAX_PER_GROUP) {
            alert("該組人數已達上限"); renderResults(); return;
        }
        let pIndex = finalGroups[fromIdx].findIndex(p => p.id === pid);
        if(pIndex > -1) {
            let player = finalGroups[fromIdx].splice(pIndex, 1)[0];
            finalGroups[toIdx].push(player);
            renderResults();
        }
    }

    function moveGroupOrder(index, direction) {
        let newIndex = index + direction;
        if(newIndex < 0 || newIndex >= finalGroups.length) return;
        [finalGroups[index], finalGroups[newIndex]] = [finalGroups[newIndex], finalGroups[index]];
        renderResults();
    }

    function exportText() {
        let text = "⛳️ 高爾夫分組名單\n==================\n";
        finalGroups.forEach((g, idx) => {
            if(g.length === 0) return;
            text += `\n[第 ${idx+1} 組] \n`;
            g.forEach(p => {
                text += `- ${p.name} (${p.hcp})\n`;
            });
            let total = g.reduce((s,p)=>s+p.hcp,0);
            text += `> Total HCP: ${total.toFixed(1)}\n`;
        });
        navigator.clipboard.writeText(text).then(() => { alert("名單已複製！"); });
    }

    function goToStep(n) {
        document.querySelectorAll('.step').forEach(e=>e.classList.remove('active'));
        document.getElementById(`tab-${n}`).classList.add('active');
        [1,2,3].forEach(i => document.getElementById(`view-${i}`).classList.add('hidden'));
        document.getElementById(`view-${n}`).classList.remove('hidden');
    }
</script>
</body>
</html>
