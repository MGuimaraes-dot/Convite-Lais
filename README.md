<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Convite Chá de Bebê</title>
    <style>
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        body {
            background-color: #fdf8f5;
            color: #4a4a4a;
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            padding: 20px;
        }
        .card {
            background: #ffffff;
            max-width: 450px;
            width: 100%;
            border-radius: 20px;
            padding: 35px 25px;
            text-align: center;
            box-shadow: 0 10px 30px rgba(0,0,0,0.08);
            border: 1px solid #f0e6df;
        }
        .tag {
            background-color: #f4e3d7;
            color: #9c6b4e;
            padding: 6px 14px;
            border-radius: 20px;
            font-size: 0.85rem;
            font-weight: 600;
            display: inline-block;
            margin-bottom: 15px;
        }
        h1 {
            color: #7d533b;
            font-size: 1.8rem;
            margin-bottom: 10px;
        }
        p.subtitle {
            font-size: 1rem;
            line-height: 1.5;
            margin-bottom: 25px;
            color: #666;
        }
        .details {
            background-color: #faf5f2;
            border-radius: 12px;
            padding: 18px;
            margin-bottom: 20px;
            text-align: left;
            font-size: 0.95rem;
            line-height: 1.8;
        }
        .gift-box {
            background-color: #fff8e7;
            border: 1px dashed #d4a373;
            border-radius: 12px;
            padding: 14px;
            margin-bottom: 25px;
            color: #7d533b;
            font-weight: 600;
            font-size: 0.95rem;
        }
        input[type="text"] {
            width: 100%;
            padding: 14px;
            border: 1px solid #dcdcdc;
            border-radius: 10px;
            font-size: 1rem;
            margin-bottom: 15px;
            outline: none;
            transition: border-color 0.3s;
        }
        input[type="text"]:focus {
            border-color: #9c6b4e;
        }
        .btn-group {
            display: flex;
            gap: 10px;
        }
        button {
            flex: 1;
            padding: 14px;
            border: none;
            border-radius: 10px;
            font-size: 1rem;
            font-weight: 600;
            cursor: pointer;
            transition: opacity 0.2s;
        }
        button:hover {
            opacity: 0.9;
        }
        .btn-yes {
            background-color: #7d533b;
            color: white;
        }
        .btn-no {
            background-color: #e8e8e8;
            color: #555;
        }
        #mensagem {
            margin-top: 15px;
            font-weight: 600;
            font-size: 0.9rem;
            color: #c5221f;
            display: none;
        }
    </style>
</head>
<body>

<div class="card">
    <span class="tag">Você está convidado!</span>
    <h1>Chá de Bebê</h1>
    <p class="subtitle">Venha celebrar conosco esse momento tão especial e cheio de amor!</p>

    <div class="details">
        <p>📅 <strong>Data:</strong> 15 de Dezembro de 2026</p>
        <p>⏰ <strong>Horário:</strong> 15h00</p>
        <p>📍 <strong>Local:</strong> Salão de Festas - Rua Exemplo, 123</p>
    </div>

    <div class="gift-box">
        🎁 Sugestão de presente: <strong>Fralda e um mimo</strong>
    </div>

    <div id="form-area">
        <input type="text" id="nome" placeholder="Digite seu nome completo" required>
        <div class="btn-group">
            <button class="btn-yes" onclick="enviarWhatsApp('Confirmado')">Confirmar Presença</button>
            <button class="btn-no" onclick="enviarWhatsApp('Não poderei ir')">Não poderei ir</button>
        </div>
        <div id="mensagem">Por favor, digite seu nome antes de responder.</div>
    </div>
</div>

<script>
    const MEU_WHATSAPP = "5517988269285";

    function enviarWhatsApp(status) {
        const nomeInput = document.getElementById('nome');
        const nome = nomeInput.value.trim();
        const msgDiv = document.getElementById('mensagem');

        if (!nome) {
            msgDiv.style.display = "block";
            return;
        }
        msgDiv.style.display = "none";

        let texto = "";
        if (status === 'Confirmado') {
            texto = `Olá! Meu nome é *${nome}* e *confirmo minha presença* no Chá de Bebê! 🍼🎉`;
        } else {
            texto = `Olá! Meu nome é *${nome}* e infelizmente *não poderei comparecer* ao Chá de Bebê.`;
        }

        const url = `https://wa.me/${MEU_WHATSAPP}?text=${encodeURIComponent(texto)}`;
        window.open(url, '_blank');
    }
</script>

</body>
</html>
