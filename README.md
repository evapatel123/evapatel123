<!doctype html>
<html lang="en">
 <head><script>window["__codeletBootstrap__"]=JSON.parse('{"A":"A","B":"20260723-05-e9a76f4"}');</script><script src="/_sdk/e358eac22bd01364.telemetry_sdk.js" integrity="sha512-KPxp3rw4K8Nu9ceWJc3gyM7srgaZxiFWOVbyu260EYzzAqdz10mfo5xyXrCx+wEKtGo77JbtmwXvFLbwrGzwvw=="></script>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Eva Banner</title>
  <script src="https://cdn.tailwindcss.com/3.4.17"></script>
  <link href="https://fonts.googleapis.com/css2?family=Space+Mono:wght@400;700&amp;display=swap" rel="stylesheet">
  <style>
    :root {
      --cyan: #00eaff;
      --electric-blue: #008cff;
    }

    * { box-sizing: border-box; }

    html, body {
      width: 100%;
      margin: 0;
      overflow-x: hidden;
    }

    body {
      font-family: "Space Mono", monospace;
    }

    .app-wrapper {
      width: 100%;
      min-height: calc(100 * min(var(--vh, 1vh), 1vh));
      display: flex;
      align-items: center;
      justify-content: center;
      overflow: hidden;
    }

    .banner-stage {
      position: relative;
      width: 100%;
      isolation: isolate;
      overflow: hidden;
      background: #02090d;
    }

    .banner-image {
      position: relative;
      z-index: 1;
      display: block;
      width: 100%;
      height: auto;
      pointer-events: none;
      user-select: none;
    }

    .fx-layer {
      position: absolute;
      inset: 0;
      z-index: 2;
      overflow: hidden;
      pointer-events: none;
    }

    .code-column {
      position: absolute;
      top: -52%;
      color: rgba(68, 255, 241, .76);
      font-family: "Space Mono", monospace;
      font-size: clamp(5px, .72vw, 12px);
      font-weight: 400;
      line-height: 1.2;
      letter-spacing: .08em;
      writing-mode: vertical-rl;
      text-orientation: upright;
      white-space: nowrap;
      text-shadow:
        0 0 3px rgba(0, 234, 255, .9),
        0 0 10px rgba(0, 234, 255, .42);
      opacity: 0;
      animation: code-fall var(--duration) linear var(--delay) infinite;
    }

    .code-column::after {
      content: "";
      position: absolute;
      inset: auto -2px -12% -2px;
      height: 22%;
      background: linear-gradient(to top, rgba(192, 255, 255, .72), transparent);
      filter: blur(2px);
    }

    @keyframes code-fall {
      0% {
        transform: translateY(-12%);
        opacity: 0;
      }
      9% { opacity: var(--opacity); }
      78% { opacity: var(--opacity); }
      100% {
        transform: translateY(310%);
        opacity: 0;
      }
    }

    .center-pulse {
      position: absolute;
      z-index: 3;
      left: 18%;
      right: 15%;
      top: 25%;
      height: 43%;
      border-radius: 48%;
      background: radial-gradient(
        ellipse at center,
        rgba(0, 234, 255, .12) 0%,
        rgba(0, 141, 255, .05) 38%,
        transparent 70%
      );
      mix-blend-mode: screen;
      filter: blur(14px);
      animation: center-glow 3.8s ease-in-out infinite;
      pointer-events: none;
    }

    @keyframes center-glow {
      0%, 100% {
        opacity: .28;
        transform: scale(.96);
        filter: blur(14px);
      }
      50% {
        opacity: .68;
        transform: scale(1.035);
        filter: blur(18px);
      }
    }

    .scan-line {
      position: absolute;
      z-index: 4;
      top: -14%;
      left: 0;
      width: 100%;
      height: 12%;
      opacity: 0;
      background: linear-gradient(
        to bottom,
        transparent 0%,
        rgba(0, 234, 255, .015) 35%,
        rgba(93, 248, 255, .24) 49%,
        rgba(0, 234, 255, .035) 53%,
        transparent 100%
      );
      mix-blend-mode: screen;
      animation: scan 6.2s cubic-bezier(.4, 0, .2, 1) infinite;
      pointer-events: none;
    }

    @keyframes scan {
      0%, 10% {
        transform: translateY(0);
        opacity: 0;
      }
      14% { opacity: .55; }
      67% {
        transform: translateY(950%);
        opacity: .34;
      }
      69%, 100% {
        transform: translateY(950%);
        opacity: 0;
      }
    }

    .circuit-flicker {
      position: absolute;
      z-index: 3;
      height: 1px;
      background: linear-gradient(
        90deg,
        transparent,
        rgba(80, 248, 255, .88),
        rgba(0, 141, 255, .4),
        transparent
      );
      box-shadow: 0 0 7px rgba(0, 234, 255, .65);
      opacity: 0;
      transform-origin: left center;
      animation: circuit-signal var(--flash-speed) steps(2, end) var(--flash-delay) infinite;
      pointer-events: none;
    }

    .circuit-flicker::after {
      content: "";
      position: absolute;
      right: 8%;
      top: -2px;
      width: 5px;
      height: 5px;
      border: 1px solid rgba(91, 248, 255, .9);
      box-shadow: 0 0 5px rgba(0, 234, 255, .8);
    }

    @keyframes circuit-signal {
      0%, 78%, 82%, 88%, 100% {
        opacity: 0;
        transform: scaleX(.15);
      }
      79%, 81% {
        opacity: .8;
        transform: scaleX(1);
      }
      85% {
        opacity: .38;
        transform: scaleX(.68);
      }
    }

    .pixel-spark {
      position: absolute;
      z-index: 4;
      width: 3px;
      height: 3px;
      border-radius: 50%;
      background: #baffff;
      box-shadow:
        0 0 4px #86ffff,
        0 0 10px var(--cyan),
        0 0 18px var(--electric-blue);
      opacity: 0;
      animation: spark var(--spark-speed) ease-in-out var(--spark-delay) infinite;
      pointer-events: none;
    }

    @keyframes spark {
      0%, 75%, 100% {
        opacity: 0;
        transform: scale(.4);
      }
      79% {
        opacity: .95;
        transform: scale(1.6);
      }
      85% {
        opacity: .25;
        transform: scale(.8);
      }
    }

    .edge-vignette {
      position: absolute;
      z-index: 5;
      inset: 0;
      background:
        linear-gradient(90deg, rgba(0, 8, 12, .15), transparent 10%, transparent 90%, rgba(0, 8, 12, .15)),
        linear-gradient(0deg, rgba(0, 8, 12, .13), transparent 18%, transparent 88%, rgba(0, 8, 12, .1));
      pointer-events: none;
    }

    @media (prefers-reduced-motion: reduce) {
      .code-column,
      .center-pulse,
      .scan-line,
      .circuit-flicker,
      .pixel-spark {
        animation: none !important;
      }

      .center-pulse { opacity: .25; }
    }
  </style>
  <script src="https://cdn.jsdelivr.net/npm/lucide@0.263.0/dist/umd/lucide.min.js" type="text/javascript"></script>
  <script src="/_sdk/935a53bc2e11fb8d.data_sdk.js" type="text/javascript" integrity="sha512-qr2oyPnEys1WebcOABaRh6hG77r5PWpqeWW6JTKbRJqly/INsfBi31CVNlTmHqjgeLpkVmmHZJUdxSx/32tOFQ=="></script>
  <script src="/_sdk/6030e540d4419216.resizing_sdk.js" type="text/javascript" integrity="sha512-b5KWzyoXsbWP4smq4sftIi6Kts4YVBpBsz0BwCViwbBJkK64a3/Z6ZMdWA+qnplNcXw4mhZeqvQi3mOosiRJdA=="></script>
 </head>
 <body data-template-id="__page-root">
  <div class="app-wrapper">
   <header class="sr-only">
    <h1>Eva programming banner</h1>
   </header>
   <main class="w-full" aria-label="Animated cyber programming banner">
    <figure class="banner-stage" aria-label="Hello, I'm Eva cyber-themed banner with animated digital effects"><img data-template-id="banner-image" class="canva-image banner-image" loading="lazy">
     <div class="fx-layer" aria-hidden="true"><span class="code-column" style="left:3%;--duration:7.8s;--delay:-5.1s;--opacity:.34">01101010100110100110</span> <span class="code-column" style="left:9%;--duration:10.4s;--delay:-8.7s;--opacity:.28">10110010111001011001</span> <span class="code-column" style="left:16%;--duration:8.7s;--delay:-1.8s;--opacity:.38">00101101001011101010</span> <span class="code-column" style="left:23%;--duration:11.2s;--delay:-6.2s;--opacity:.24">11001001010110010111</span> <span class="code-column" style="left:31%;--duration:9.6s;--delay:-3.7s;--opacity:.31">01011010110100101100</span> <span class="code-column" style="left:39%;--duration:12s;--delay:-9.4s;--opacity:.2">10100110100111010010</span> <span class="code-column" style="left:47%;--duration:8.3s;--delay:-4.3s;--opacity:.27">00110101101001010110</span> <span class="code-column" style="left:56%;--duration:10.8s;--delay:-7.1s;--opacity:.3">11010100101101001101</span> <span class="code-column" style="left:64%;--duration:9.1s;--delay:-2.6s;--opacity:.25">01001110110100101011</span> <span class="code-column" style="left:72%;--duration:11.6s;--delay:-10.2s;--opacity:.34">10110100101011010100</span> <span class="code-column" style="left:81%;--duration:8.9s;--delay:-5.8s;--opacity:.29">00101011100101101010</span> <span class="code-column" style="left:89%;--duration:10.1s;--delay:-3.1s;--opacity:.4">11010010110101001101</span> <span class="code-column" style="left:96%;--duration:12.4s;--delay:-8.4s;--opacity:.25">01100101001011101001</span>
     </div>
     <div class="center-pulse" aria-hidden="true"></div>
     <div class="scan-line" aria-hidden="true"></div>
     <div class="circuit-flicker" aria-hidden="true" style="left:4%;top:48%;width:19%;--flash-speed:4.7s;--flash-delay:-1.1s"></div>
     <div class="circuit-flicker" aria-hidden="true" style="left:19%;top:74%;width:22%;--flash-speed:5.8s;--flash-delay:-3.5s"></div>
     <div class="circuit-flicker" aria-hidden="true" style="left:58%;top:63%;width:25%;--flash-speed:5.2s;--flash-delay:-2.2s"></div>
     <div class="circuit-flicker" aria-hidden="true" style="left:74%;top:43%;width:21%;--flash-speed:6.3s;--flash-delay:-4.9s"></div>
     <div class="circuit-flicker" aria-hidden="true" style="left:38%;top:84%;width:31%;--flash-speed:7.1s;--flash-delay:-2.8s"></div><span class="pixel-spark" aria-hidden="true" style="left:15%;top:40%;--spark-speed:3.8s;--spark-delay:-1.2s"></span> <span class="pixel-spark" aria-hidden="true" style="left:43%;top:73%;--spark-speed:4.6s;--spark-delay:-3.5s"></span> <span class="pixel-spark" aria-hidden="true" style="left:76%;top:55%;--spark-speed:5.1s;--spark-delay:-2.1s"></span> <span class="pixel-spark" aria-hidden="true" style="left:93%;top:31%;--spark-speed:4.2s;--spark-delay:-.8s"></span>
     <div class="edge-vignette" aria-hidden="true"></div>
    </figure>
   </main>
   <footer class="sr-only">
    Animated Eva banner
   </footer>
  </div>
  <script src="/_sdk/c939c145c3c74230.editing_sdk.js" integrity="sha512-jh2pv/gl9Gzzn5dxfzwQO4wkqtnAQIim+LIUDYfVu2cdqPkQV2MqbjsDUW5IYbrSZFjRlOBrIWzlvWDXQYxOjg=="></script>
 </body>
</html>

### 🚀 About Me

🔭 &nbsp;I'm currently working on **an application**  
🌱 &nbsp;I'm currently learning **Rust, Java and advanced SQL**  
👯 &nbsp;I'm looking to collaborate on **more interesting projects**  
😄 &nbsp;Pronouns: **she/her**  
⚡ &nbsp;Fun fact: **I am also a graphic designer and a starting-off technical writer**

Check out my Latest blogs! : https://hashnode.com/@evapatel123

### 🛠️ Tech Stack

<p align="left">
  <img src="https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black" alt="JavaScript" />
  <img src="https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white" alt="Python" />
  <img src="https://img.shields.io/badge/Java-ED8B00?style=for-the-badge&logo=openjdk&logoColor=white" alt="Java" />
  <img src="https://img.shields.io/badge/SQL-4479A1?style=for-the-badge&logo=mysql&logoColor=white" alt="SQL" />
  <img src="https://img.shields.io/badge/TypeScript-3178C6?style=for-the-badge&logo=typescript&logoColor=white" alt="TypeScript" />
  <img src="https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white" alt="HTML5" />
  <img src="https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge&logo=css3&logoColor=white" alt="CSS3" />
  <img src="https://img.shields.io/badge/Rust-000000?style=for-the-badge&logo=rust&logoColor=white" alt="Rust" />
  <img src="https://img.shields.io/badge/React-20232A?style=for-the-badge&logo=react&logoColor=61DAFB" alt="React" />
  <img src="https://img.shields.io/badge/Node.js-339933?style=for-the-badge&logo=nodedotjs&logoColor=white" alt="Node.js" />
  <img src="https://img.shields.io/badge/Django-092E20?style=for-the-badge&logo=django&logoColor=white" alt="Django" />
  <img src="https://img.shields.io/badge/Flask-000000?style=for-the-badge&logo=flask&logoColor=white" alt="Flask" />
  <img src="https://img.shields.io/badge/Tailwind%20CSS-06B6D4?style=for-the-badge&logo=tailwindcss&logoColor=white" alt="Tailwind CSS" />
  <img src="https://img.shields.io/badge/PyTorch-EE4C2C?style=for-the-badge&logo=pytorch&logoColor=white" alt="PyTorch" />
  <img src="https://img.shields.io/badge/TensorFlow-FF6F00?style=for-the-badge&logo=tensorflow&logoColor=white" alt="TensorFlow" />
  <img src="https://img.shields.io/badge/pandas-150458?style=for-the-badge&logo=pandas&logoColor=white" alt="pandas" />
  <img src="https://img.shields.io/badge/NumPy-013243?style=for-the-badge&logo=numpy&logoColor=white" alt="NumPy" />
  <img src="https://img.shields.io/badge/PostgreSQL-4169E1?style=for-the-badge&logo=postgresql&logoColor=white" alt="PostgreSQL" />
  <img src="https://img.shields.io/badge/Firebase-FFCA28?style=for-the-badge&logo=firebase&logoColor=black" alt="Firebase" />
  <img src="https://img.shields.io/badge/Supabase-3FCF8E?style=for-the-badge&logo=supabase&logoColor=black" alt="Supabase" />
  <img src="https://img.shields.io/badge/MySQL-4479A1?style=for-the-badge&logo=mysql&logoColor=white" alt="MySQL" />
  <img src="https://img.shields.io/badge/Vercel-000000?style=for-the-badge&logo=vercel&logoColor=white" alt="Vercel" />
  <img src="https://img.shields.io/badge/Netlify-00C7B7?style=for-the-badge&logo=netlify&logoColor=white" alt="Netlify" />
  <img src="https://img.shields.io/badge/Git-F05032?style=for-the-badge&logo=git&logoColor=white" alt="Git" />
  <img src="https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white" alt="GitHub" />
  <img src="https://img.shields.io/badge/VS%20Code-007ACC?style=for-the-badge&logo=vscodium&logoColor=white" alt="VS Code" />
  <img src="https://img.shields.io/badge/Figma-F24E1E?style=for-the-badge&logo=figma&logoColor=white" alt="Figma" />
  <img src="https://img.shields.io/badge/Slack-4A154B?style=for-the-badge&logo=slack&logoColor=white" alt="Slack" />
  <img src="https://img.shields.io/badge/Notion-000000?style=for-the-badge&logo=notion&logoColor=white" alt="Notion" />
  <img src="https://img.shields.io/badge/GitLab-FC6D26?style=for-the-badge&logo=gitlab&logoColor=white" alt="GitLab" />
</p>

---

### 📊 GitHub Stats

<p align="center">
  <img height="165" src="https://github-readme-stats-five-sigma-99.vercel.app/api?username=evapatel123&show_icons=true&theme=tokyonight&title_color=0891b2&icon_color=0891b2&hide_border=true&bg_color=00000000&count_private=true" alt="stats" />
  <img height="165" src="https://github-readme-stats-five-sigma-99.vercel.app/api/top-langs/?username=evapatel123&layout=compact&theme=tokyonight&title_color=0891b2&icon_color=0891b2&hide_border=true&bg_color=00000000&langs_count=8" alt="top langs" />
</p>
---

### 📈 Contribution Graph

<p align="center">
  <img width="100%" src="https://github-readme-activity-graph.vercel.app/graph?username=evapatel123&bg_color=00000000&color=0891b2&line=0891b2&point=c9d1d9&area=true&hide_border=true" alt="activity graph" />
</p>

---

### 💭 Dev Quote

<p align="center">
  <img src="https://quotes-github-readme.vercel.app/api?type=horizontal&theme=tokyonight" alt="Dev quote" />
</p>

---
<p align="center"><i>⭐️ From <a href="https://github.com/evapatel123">evapatel123</a></i></p>
