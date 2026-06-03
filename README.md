# projeto-etec1
O Contabilizador Geral do Refeitório terá como finalidade realizar o controle da quantidade de alunos que utilizarão o refeitório escolar. Em cada sala será efetuada uma contagem individual, e os dados coletados serão registrados e armazenados no sistema. Posteriormente, todas as informações das turmas serão somadas automaticamente, gerando o total geral de refeições previstas para o dia.

Após a consolidação dos dados, o resultado será disponibilizado para a equipe da cantina, facilitando a organização, o preparo adequado dos alimentos e evitando desperdícios. O sistema será integrado à mesma plataforma já utilizada para o registro de irregularidades escolares, proporcionando maior praticidade, acessibilidade e centralização das informações em um único ambiente digital.
 

```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Contabilizador do Refeitório</title>

<style>
    body{
        font-family: Arial, sans-serif;
        background:#f4f4f4;
        padding:20px;
        text-align:center;
    }

    .container{
        max-width:600px;
        margin:auto;
        background:white;
        padding:20px;
        border-radius:10px;
        box-shadow:0 0 10px rgba(0,0,0,0.1);
    }

    h1{
        color:#2e7d32;
    }

    .sala{
        margin:15px 0;
    }

    input{
        width:100px;
        padding:8px;
        text-align:center;
        font-size:16px;
    }

    button{
        background:#2e7d32;
        color:white;
        border:none;
        padding:10px 20px;
        cursor:pointer;
        border-radius:5px;
        margin-top:20px;
    }

    button:hover{
        background:#1b5e20;
    }

    #resultado{
        margin-top:20px;
        font-size:24px;
        font-weight:bold;
        color:#2e7d32;
    }
</style>
</head>
<body>

<div class="container">

    <h1>🍽️ Contabilizador do Refeitório</h1>

    <div class="sala">
        <label>Sala 1:</label>
        <input type="number" id="sala1" min="0" value="0">
    </div>

    <div class="sala">
        <label>Sala 2:</label>
        <input type="number" id="sala2" min="0" value="0">
    </div>

    <div class="sala">
        <label>Sala 3:</label>
        <input type="number" id="sala3" min="0" value="0">
    </div>

    <div class="sala">
        <label>Sala 4:</label>
        <input type="number" id="sala4" min="0" value="0">
    </div>

    <button onclick="somar()">Calcular Total</button>

    <div id="resultado">
        Total de refeições: 0
    </div>

</div>

<script>
function somar(){

    let sala1 = Number(document.getElementById("sala1").value);
    let sala2 = Number(document.getElementById("sala2").value);
    let sala3 = Number(document.getElementById("sala3").value);
    let sala4 = Number(document.getElementById("sala4").value);

    let total = sala1 + sala2 + sala3 + sala4;

    document.getElementById("resultado").innerHTML =
        "Total de refeições: " + total;
}
</script>

</body>
</html>
