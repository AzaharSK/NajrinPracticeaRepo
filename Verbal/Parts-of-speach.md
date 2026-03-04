<img width="1911" height="692" alt="image" src="https://github.com/user-attachments/assets/1acd7781-3bfb-4dfe-95ad-f0bb2eae55bb" />
<img width="1899" height="763" alt="image" src="https://github.com/user-attachments/assets/a3005a8d-9cd1-4795-807c-a88024c214dd" />


### Noun Examples

* `Place` - Goa, Taj Mahal, Sea, River, Planet, Farmhouse, Tourist place, etc. 
* `Person` - John, Biographer, Cardiologist, Cameramen, Actress, Politicians, etc.
* `Things` -  Grains, Rocks, Trees, Forest, Paper, Glass, Metals, Plastic, etc.
* `Ideas` - Revolution, Resolution, Invention, Conclusion, Argument, etc.


# Collective Nouns :
<img width="1788" height="652" alt="image" src="https://github.com/user-attachments/assets/64306963-a892-4116-aa52-5e5584a3d640" />
<img width="1520" height="661" alt="image" src="https://github.com/user-attachments/assets/fb8621b6-fb74-40c4-b3f8-b67855723784" />
<img width="1661" height="655" alt="image" src="https://github.com/user-attachments/assets/0d60b395-9bf2-41cd-b92a-8e5d1fb43f43" />
<img width="1520" height="661" alt="image" src="https://github.com/user-attachments/assets/8cf9150b-8371-4cbe-a6bd-af34a2a01a7e" />
<img width="1520" height="661" alt="image" src="https://github.com/user-attachments/assets/33dd1f66-5194-46b5-8697-94db0d9789e2" />
<img width="1484" height="636" alt="image" src="https://github.com/user-attachments/assets/239f7b11-bbd5-4280-a954-57c71b976463" />
<img width="1484" height="636" alt="image" src="https://github.com/user-attachments/assets/664da992-9dbf-49b9-b0fb-279db8b7824a" />
<img width="1484" height="636" alt="image" src="https://github.com/user-attachments/assets/5af12212-2221-44f3-8a2b-5e2c34af589b" />

# [Material Noun](https://github.com/AzaharSK/NajrinPracticeaRepo/blob/main/Verbal/made_of_worksheet.html)


```html
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Things Are Made Of... 🌟</title>
<link href="https://fonts.googleapis.com/css2?family=Nunito:wght@700;800;900&family=Fredoka+One&display=swap" rel="stylesheet">
<style>
  :root {
    --yellow: #FFD93D;
    --orange: #FF6B35;
    --blue: #4ECDC4;
    --green: #95E1D3;
    --pink: #FF8B94;
    --purple: #A78BFA;
    --bg: #FFFBEF;
    --card-bg: #FFFFFF;
    --border-radius: 20px;
    --shadow: 0 6px 20px rgba(0,0,0,0.10);
  }

  * { box-sizing: border-box; margin: 0; padding: 0; }

  body {
    font-family: 'Nunito', sans-serif;
    background: var(--bg);
    background-image:
      radial-gradient(circle at 10% 20%, #FFD93D22 0%, transparent 40%),
      radial-gradient(circle at 90% 80%, #4ECDC422 0%, transparent 40%),
      radial-gradient(circle at 50% 50%, #FF8B9411 0%, transparent 60%);
    min-height: 100vh;
    padding: 30px 20px 60px;
  }

  /* ─── HEADER ─── */
  .header {
    text-align: center;
    margin-bottom: 40px;
  }
  .header h1 {
    font-family: 'Fredoka One', cursive;
    font-size: clamp(2rem, 6vw, 3.6rem);
    color: var(--orange);
    text-shadow: 3px 3px 0 #FFD93D, 5px 5px 0 rgba(0,0,0,0.08);
    letter-spacing: 1px;
    margin-bottom: 8px;
  }
  .header p {
    font-size: 1.1rem;
    color: #888;
    font-weight: 700;
  }
  .dots-bar {
    display: flex;
    justify-content: center;
    gap: 8px;
    margin-top: 14px;
  }
  .dot {
    width: 14px; height: 14px;
    border-radius: 50%;
    display: inline-block;
  }

  /* ─── GRID ─── */
  .grid {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    gap: 18px;
    max-width: 900px;
    margin: 0 auto;
  }

  /* ─── CARD ─── */
  .card {
    background: var(--card-bg);
    border-radius: var(--border-radius);
    box-shadow: var(--shadow);
    border: 3px solid transparent;
    padding: 16px 12px;
    display: flex;
    align-items: center;
    gap: 0;
    transition: transform 0.2s, box-shadow 0.2s;
    position: relative;
    overflow: hidden;
  }
  .card:hover {
    transform: translateY(-4px);
    box-shadow: 0 12px 30px rgba(0,0,0,0.15);
  }

  /* colour cycling for cards */
  .card:nth-child(6n+1) { border-color: #FFD93D; }
  .card:nth-child(6n+2) { border-color: #4ECDC4; }
  .card:nth-child(6n+3) { border-color: #FF8B94; }
  .card:nth-child(6n+4) { border-color: #A78BFA; }
  .card:nth-child(6n+5) { border-color: #FF6B35; }
  .card:nth-child(6n+6) { border-color: #95E1D3; }

  /* ─── ITEM BOX (object / material) ─── */
  .item {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    flex: 1;
    min-width: 0;
  }
  .item-emoji {
    font-size: clamp(2rem, 5vw, 3rem);
    line-height: 1.1;
    margin-bottom: 6px;
  }
  .item-label {
    font-family: 'Fredoka One', cursive;
    font-size: clamp(0.72rem, 2vw, 0.98rem);
    text-align: center;
    border-radius: 30px;
    padding: 3px 10px;
    width: 100%;
    max-width: 110px;
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
  }

  /* label colours */
  .card:nth-child(6n+1) .thing .item-label  { background: #FFD93D; color: #5a3d00; }
  .card:nth-child(6n+1) .material .item-label{ background: #FFF3C4; color: #5a3d00; }
  .card:nth-child(6n+2) .thing .item-label  { background: #4ECDC4; color: #fff; }
  .card:nth-child(6n+2) .material .item-label{ background: #C8F5F2; color: #1a6b66; }
  .card:nth-child(6n+3) .thing .item-label  { background: #FF8B94; color: #fff; }
  .card:nth-child(6n+3) .material .item-label{ background: #FFD5D8; color: #7a0010; }
  .card:nth-child(6n+4) .thing .item-label  { background: #A78BFA; color: #fff; }
  .card:nth-child(6n+4) .material .item-label{ background: #E9E0FF; color: #4b3a99; }
  .card:nth-child(6n+5) .thing .item-label  { background: #FF6B35; color: #fff; }
  .card:nth-child(6n+5) .material .item-label{ background: #FFD6C5; color: #7a2800; }
  .card:nth-child(6n+6) .thing .item-label  { background: #95E1D3; color: #1a5c53; }
  .card:nth-child(6n+6) .material .item-label{ background: #DDF5F1; color: #1a5c53; }

  /* ─── ARROW SECTION ─── */
  .arrow-area {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    gap: 2px;
    padding: 0 4px;
    flex-shrink: 0;
  }
  .made-of-text {
    font-family: 'Fredoka One', cursive;
    font-size: clamp(0.55rem, 1.4vw, 0.72rem);
    color: #aaa;
    text-align: center;
    white-space: nowrap;
    letter-spacing: 0.5px;
  }
  .arrow-svg {
    width: clamp(28px, 5vw, 44px);
    height: 18px;
  }

  /* ─── PRINT / PAGE BREAK ─── */
  @media print {
    body { background: white; padding: 10px; }
    .card { break-inside: avoid; }
    .grid { gap: 12px; }
  }

  /* ─── FOOTER ─── */
  .footer {
    text-align: center;
    margin-top: 50px;
    font-family: 'Fredoka One', cursive;
    font-size: 1.1rem;
    color: #ccc;
  }
</style>
</head>
<body>

<div class="header">
  <h1>🌟 Things Are Made Of… 🌟</h1>
  <p>Match each object to its material!</p>
  <div class="dots-bar">
    <span class="dot" style="background:#FFD93D"></span>
    <span class="dot" style="background:#FF6B35"></span>
    <span class="dot" style="background:#FF8B94"></span>
    <span class="dot" style="background:#A78BFA"></span>
    <span class="dot" style="background:#4ECDC4"></span>
    <span class="dot" style="background:#95E1D3"></span>
    <span class="dot" style="background:#FFD93D"></span>
  </div>
</div>

<div class="grid" id="grid"></div>

<div class="footer">✏️ Learn • Explore • Discover ✏️</div>

<script>
const items = [
  { thing:"Shirt",    thingE:"👕",  material:"Cotton",     matE:"🌸" },
  { thing:"Table",    thingE:"🪑",  material:"Wood",       matE:"🪵" },
  { thing:"Chair",    thingE:"🪑",  material:"Wood",       matE:"🪵" },
  { thing:"Door",     thingE:"🚪",  material:"Wood",       matE:"🪵" },
  { thing:"Window",   thingE:"🪟",  material:"Glass",      matE:"🔮" },
  { thing:"Bottle",   thingE:"🍶",  material:"Plastic",    matE:"♻️" },
  { thing:"Spoon",    thingE:"🥄",  material:"Steel",      matE:"⚙️" },
  { thing:"Fork",     thingE:"🍴",  material:"Steel",      matE:"⚙️" },
  { thing:"Knife",    thingE:"🔪",  material:"Steel",      matE:"⚙️" },
  { thing:"Plate",    thingE:"🍽️", material:"Ceramic",    matE:"🏺" },
  { thing:"Cup",      thingE:"☕",  material:"Glass",      matE:"🔮" },
  { thing:"Bowl",     thingE:"🥣",  material:"Clay",       matE:"🏺" },
  { thing:"Ring",     thingE:"💍",  material:"Gold",       matE:"🥇" },
  { thing:"Necklace", thingE:"📿",  material:"Silver",     matE:"🥈" },
  { thing:"Bracelet", thingE:"📿",  material:"Gold",       matE:"🥇" },
  { thing:"Coin",     thingE:"🪙",  material:"Metal",      matE:"⚙️" },
  { thing:"Nail",     thingE:"🔩",  material:"Iron",       matE:"🪝" },
  { thing:"Chain",    thingE:"⛓️", material:"Iron",       matE:"🪝" },
  { thing:"Bridge",   thingE:"🌉",  material:"Concrete",   matE:"🧱" },
  { thing:"Road",     thingE:"🛣️", material:"Asphalt",    matE:"🖤" },
  { thing:"Roof",     thingE:"🏠",  material:"Tiles",      matE:"🟫" },
  { thing:"Bag",      thingE:"👜",  material:"Leather",    matE:"🟤" },
  { thing:"Belt",     thingE:"🩱",  material:"Leather",    matE:"🟤" },
  { thing:"Jacket",   thingE:"🧥",  material:"Leather",    matE:"🟤" },
  { thing:"Sweater",  thingE:"🧶",  material:"Wool",       matE:"🐑" },
  { thing:"Scarf",    thingE:"🧣",  material:"Silk",       matE:"🕷️" },
  { thing:"Blanket",  thingE:"🛌",  material:"Wool",       matE:"🐑" },
  { thing:"Curtain",  thingE:"🪟",  material:"Fabric",     matE:"🧵" },
  { thing:"Carpet",   thingE:"🟫",  material:"Wool",       matE:"🐑" },
  { thing:"Rope",     thingE:"🪢",  material:"Nylon",      matE:"🧵" },
  { thing:"Tyre",     thingE:"🚗",  material:"Rubber",     matE:"⚫" },
  { thing:"Pencil",   thingE:"✏️", material:"Wood",       matE:"🪵" },
  { thing:"Notebook", thingE:"📓",  material:"Paper",      matE:"📄" },
  { thing:"Newspaper",thingE:"📰",  material:"Paper",      matE:"📄" },
  { thing:"Book",     thingE:"📚",  material:"Paper",      matE:"📄" },
  { thing:"Brick",    thingE:"🧱",  material:"Clay",       matE:"🏺" },
  { thing:"Statue",   thingE:"🗿",  material:"Marble",     matE:"⬜" },
  { thing:"Wall",     thingE:"🧱",  material:"Bricks",     matE:"🧱" },
  { thing:"Fence",    thingE:"🌲",  material:"Wood",       matE:"🪵" },
  { thing:"Watch",    thingE:"⌚",  material:"Metal",      matE:"⚙️" },
  { thing:"Key",      thingE:"🔑",  material:"Metal",      matE:"⚙️" },
  { thing:"Helmet",   thingE:"⛑️", material:"Plastic",    matE:"♻️" },
  { thing:"Bucket",   thingE:"🪣",  material:"Plastic",    matE:"♻️" },
  { thing:"Box",      thingE:"📦",  material:"Cardboard",  matE:"📦" },
  { thing:"Mat",      thingE:"🟫",  material:"Straw",      matE:"🌾" },
  { thing:"Basket",   thingE:"🧺",  material:"Bamboo",     matE:"🎋" },
  { thing:"Drum",     thingE:"🥁",  material:"Leather",    matE:"🟤" },
  { thing:"Candle",   thingE:"🕯️", material:"Wax",        matE:"🕯️" },
  { thing:"Mirror",   thingE:"🪞",  material:"Glass",      matE:"🔮" },
  { thing:"Comb",     thingE:"🪮",  material:"Plastic",    matE:"♻️" },
  { thing:"Cupboard", thingE:"🗄️", material:"Wood",       matE:"🪵" },
  { thing:"Gate",     thingE:"🚧",  material:"Iron",       matE:"🪝" },
  { thing:"Railing",  thingE:"🔩",  material:"Steel",      matE:"⚙️" },
  { thing:"Crown",    thingE:"👑",  material:"Gold",       matE:"🥇" },
  { thing:"Medal",    thingE:"🥉",  material:"Bronze",     matE:"🥉" },
  { thing:"Trophy",   thingE:"🏆",  material:"Metal",      matE:"⚙️" },
  { thing:"Pot",      thingE:"🫕",  material:"Aluminium",  matE:"🥄" },
  { thing:"Pan",      thingE:"🍳",  material:"Steel",      matE:"⚙️" },
  { thing:"Jug",      thingE:"🫗",  material:"Plastic",    matE:"♻️" },
  { thing:"Sink",     thingE:"🚿",  material:"Steel",      matE:"⚙️" },
  { thing:"Bathtub",  thingE:"🛁",  material:"Fiberglass", matE:"🔮" },
  { thing:"Pillow",   thingE:"🛏️", material:"Cotton",     matE:"🌸" },
  { thing:"Quilt",    thingE:"🛌",  material:"Wool",       matE:"🐑" },
  { thing:"Sock",     thingE:"🧦",  material:"Cotton",     matE:"🌸" },
  { thing:"Glove",    thingE:"🧤",  material:"Leather",    matE:"🟤" },
  { thing:"Shoe",     thingE:"👟",  material:"Leather",    matE:"🟤" },
  { thing:"Sandal",   thingE:"🩴",  material:"Rubber",     matE:"⚫" },
  { thing:"Ladder",   thingE:"🪜",  material:"Wood",       matE:"🪵" },
  { thing:"Tower",    thingE:"🗼",  material:"Stone",      matE:"🪨" },
  { thing:"Temple",   thingE:"⛩️", material:"Marble",     matE:"⬜" },
  { thing:"Mosque",   thingE:"🕌",  material:"Stone",      matE:"🪨" },
  { thing:"Church",   thingE:"⛪",  material:"Brick",      matE:"🧱" },
  { thing:"Hut",      thingE:"🛖",  material:"Mud",        matE:"🟤" },
  { thing:"Cabin",    thingE:"🏚️", material:"Wood",       matE:"🪵" },
  { thing:"Desk",     thingE:"🖥️", material:"Wood",       matE:"🪵" },
  { thing:"Shelf",    thingE:"📚",  material:"Wood",       matE:"🪵" },
  { thing:"Tray",     thingE:"🍽️", material:"Plastic",    matE:"♻️" },
  { thing:"Tap",      thingE:"🚿",  material:"Steel",      matE:"⚙️" },
  { thing:"Bell",     thingE:"🔔",  material:"Brass",      matE:"🔔" },
  { thing:"Whistle",  thingE:"📯",  material:"Metal",      matE:"⚙️" },
  { thing:"Sword",    thingE:"⚔️", material:"Steel",      matE:"⚙️" },
  { thing:"Shield",   thingE:"🛡️", material:"Iron",       matE:"🪝" },
  { thing:"Spear",    thingE:"🏹",  material:"Wood",       matE:"🪵" },
  { thing:"Button",   thingE:"🔘",  material:"Plastic",    matE:"♻️" },
  { thing:"Zipper",   thingE:"🤐",  material:"Metal",      matE:"⚙️" },
  { thing:"Frame",    thingE:"🖼️", material:"Wood",       matE:"🪵" },
  { thing:"Toy",      thingE:"🧸",  material:"Plastic",    matE:"♻️" },
  { thing:"Doll",     thingE:"🪆",  material:"Cloth",      matE:"🧵" },
  { thing:"Kite",     thingE:"🪁",  material:"Paper",      matE:"📄" },
  { thing:"Flag",     thingE:"🚩",  material:"Cloth",      matE:"🧵" },
  { thing:"Tent",     thingE:"⛺",  material:"Canvas",     matE:"🟫" },
  { thing:"Boat",     thingE:"⛵",  material:"Wood",       matE:"🪵" },
  { thing:"Ship",     thingE:"🚢",  material:"Steel",      matE:"⚙️" },
  { thing:"Plane",    thingE:"✈️", material:"Aluminium",  matE:"🥄" },
  { thing:"Car",      thingE:"🚗",  material:"Metal",      matE:"⚙️" },
  { thing:"Bus",      thingE:"🚌",  material:"Steel",      matE:"⚙️" },
  { thing:"Train",    thingE:"🚂",  material:"Iron",       matE:"🪝" },
  { thing:"Rocket",   thingE:"🚀",  material:"Metal",      matE:"⚙️" },
];

const grid = document.getElementById('grid');

const arrowSVG = `<svg class="arrow-svg" viewBox="0 0 44 18" fill="none" xmlns="http://www.w3.org/2000/svg">
  <path d="M2 9 Q22 2 42 9" stroke="#FFCC00" stroke-width="3" stroke-linecap="round" fill="none"/>
  <path d="M36 5 L42 9 L36 13" stroke="#FFCC00" stroke-width="3" stroke-linecap="round" stroke-linejoin="round" fill="none"/>
</svg>`;

items.forEach(({thing, thingE, material, matE}) => {
  const card = document.createElement('div');
  card.className = 'card';
  card.innerHTML = `
    <div class="item thing">
      <div class="item-emoji">${thingE}</div>
      <div class="item-label">${thing}</div>
    </div>
    <div class="arrow-area">
      ${arrowSVG}
      <div class="made-of-text">made of</div>
    </div>
    <div class="item material">
      <div class="item-emoji">${matE}</div>
      <div class="item-label">${material}</div>
    </div>
  `;
  grid.appendChild(card);
});
</script>
</body>
</html>


```
