<html>

<body>
    <canvas id="canvas" height="20" width="20" style="border: 1px solid #CCC;
         height: 500px; width: 500px; image-rendering: pixelated;"></canvas>
    <script>
        var canvas = document.getElementById('canvas')
        var context = canvas.getContext('2d');

        var jogador1 = {
            x: 12,
            y: 15,
        }
        var inimigos = [{
            x: 5,
            y: 5,
        }]

        function adicionarInimigo() {
            if (inimigos.length < 15) {
                inimigos.push({
                    x: Math.floor(Math.random() * (19 - 0)),
                    y: Math.floor(Math.random() * (19 - 0))
                })
                desenharJogo();
            }
        }
        setInterval(adicionarInimigo, 2000)

        function desenharJogador() {
            context.fillStyle = `black`;
            context.fillRect(jogador1.x, jogador1.y, 1, 1);
        }
        function desenharInimigo(inimigo) {
            context.fillStyle = `red`;
            context.fillRect(inimigo.x, inimigo.y, 1, 1);
        }

        function limparTela() {
            context.clearRect(0, 0, 20, 20);
        }


        function desenharJogo() {
            limparTela();
            for (let i = 0; i < inimigos.length; i++) {
                desenharInimigo(inimigos[i]);
            }
            desenharJogador();
        }

        document.addEventListener('keydown', movePlayer);

        function movePlayer(event) {
            if (event.key == 'ArrowUp') {
                if (jogador1.y > 0) {
                    jogador1.y = jogador1.y - 1;
                }
            }
            if (event.key == 'ArrowDown') {
                if (jogador1.y < 19) {
                    jogador1.y = jogador1.y + 1;
                }
            }
            if (event.key == 'ArrowLeft') {
                if (jogador1.x > 0) {
                    jogador1.x = jogador1.x - 1;
                }
            }
            if (event.key == 'ArrowRight') {
                if (jogador1.x < 19) {
                    jogador1.x = jogador1.x + 1;
                }
            }
            desenharJogo();
        }

    </script>
</body>

</html>
