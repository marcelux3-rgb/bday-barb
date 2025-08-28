<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <title>🎉 FELIZ ANIVERSÁRIO BARB!!! 🎉</title>
    <style>
        html, body {
            margin: 0;
            padding: 0;
            height: 100%;
            overflow: hidden;
            font-family: 'Arial', sans-serif;
            text-align: center;
            color: whitesmoke;
        }

        /* Tela inicial do Start */
        #startScreen {
            background: linear-gradient(135deg, #800080 30%, #4B0082 60%, #000000 100%);
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100%;
            width: 100%;
            position: fixed;
            top: 0;
            left: 0;
            z-index: 10;
            flex-direction: column;
        }

        #startScreen button {
            padding: 20px 40px;
            font-size: 1.5em;
            border: none;
            border-radius: 10px;
            background: #ffcc00;
            color: #000;
            cursor: pointer;
            box-shadow: 2px 2px 5px #000;
        }

        #startScreen button:hover { 
            background: #ffaa00; 
            transform: scale(1.1); 
        }

        /* Página principal */
        #mainContent {
            display: none;
            background: linear-gradient(135deg, #800080 30%, #4B0082 60%, #000000 100%);
            height: 100%;
            width: 100%;
            position: relative;
            padding-top: 20px;
        }

        h1 { font-size: 3em; text-shadow: 2px 2px 5px #000; }
        p { font-size: 1.5em; margin: 20px 0; }
        img { width: 200px; border-radius: 20px; box-shadow: 0 0 15px #000; }
        button.surpresaBtn {
            padding: 15px 30px; font-size: 1.2em; border: none; border-radius: 10px;
            background: #ffcc00; color: #000; cursor: pointer; box-shadow: 2px 2px 5px #000;
            margin-top: 20px;
        }
        button.surpresaBtn:hover { background: #ffaa00; transform: scale(1.1); }

        .balao { position: absolute; bottom: -50px; font-size: 2em; opacity: 0; animation: subir linear; }
        @keyframes subir { 0% { bottom: -50px; opacity: 1; } 100% { bottom: 110%; opacity: 0; } }
    </style>
</head>
<body>
    <!-- Tela inicial -->
    <div id="startScreen">
        <button id="startBtn">Start</button>
    </div>

    <!-- Conteúdo principal -->
    <div id="mainContent">
        <h1>🎂 Feliz Aniversário, BARB! 🎂</h1>
        <img src="teste.jpg" alt="Foto da aniversariante">
        <p>HEY JESUS!!! Que o próximo ano seja BALA MÁXIMA! Com muita bênção, roles e JESUS 🙏!</p>
        <button class="surpresaBtn" id="surpresaBtn">Clique para a surpresa</button>

        <audio id="musica" loop>
            <source src="surpresa.mp3" type="audio/mpeg">
            Seu navegador não suporta áudio.
        </audio>
    </div>

    <script>
        const startBtn = document.getElementById('startBtn');
        const startScreen = document.getElementById('startScreen');
        const mainContent = document.getElementById('mainContent');
        const musica = document.getElementById('musica');

        startBtn.addEventListener('click', () => {
            startScreen.style.display = 'none';
            mainContent.style.display = 'block';
            musica.play().catch(err => console.log('Erro ao tentar tocar música:', err));
        });

        // BALÕES ANIMADOS
        const baloes = ['🎈','🎉','💜','💖','🎊','✨'];
        function criarBalao() {
            const balao = document.createElement('div');
            balao.className = 'balao';
            balao.innerText = baloes[Math.floor(Math.random() * baloes.length)];
            balao.style.left = Math.random() * 95 + '%';
            balao.style.fontSize = (Math.random() * 1 + 1.5) + 'em';
            const duracao = Math.random() * 5 + 5;
            balao.style.animationDuration = duracao + 's';
            mainContent.appendChild(balao);
            setTimeout(() => { balao.remove(); }, duracao * 1000);
        }
        setInterval(criarBalao, 400);

        // BOTÃO SURPRESA
        document.getElementById('surpresaBtn').addEventListener('click', () => {
            const largura = 400;
            const altura = 200;
            const esquerda = (window.screen.width - largura) / 2;
            const topo = (window.screen.height - altura) / 2;

            const novaJanela = window.open('', 'surpresa', 
                `width=${largura},height=${altura},top=${topo},left=${esquerda},resizable=no`
            );

            novaJanela.document.body.innerHTML = `
                <div style="
                    background: linear-gradient(135deg, #800080 30%, #4B0082 60%, #000000 100%);
                    color: white; width: 100%; height: 100%; display: flex; 
                    justify-content: center; align-items: center; font-family: Arial, sans-serif;
                    text-align: center; margin: 0;
                ">
                    <h2>🎁 Surpresa: Você ganhou um giftcard EMAUS!<br>CUPOM: TESTE123456 🎁</h2>
                </div>
            `;
        });
    </script>
</body>
</html>
