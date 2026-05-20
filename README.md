# projeto-etec1
O Contabilizador Geral do Refeitório terá como finalidade realizar o controle da quantidade de alunos que utilizarão o refeitório escolar. Em cada sala será efetuada uma contagem individual, e os dados coletados serão registrados e armazenados no sistema. Posteriormente, todas as informações das turmas serão somadas automaticamente, gerando o total geral de refeições previstas para o dia.

Após a consolidação dos dados, o resultado será disponibilizado para a equipe da cantina, facilitando a organização, o preparo adequado dos alimentos e evitando desperdícios. O sistema será integrado à mesma plataforma já utilizada para o registro de irregularidades escolares, proporcionando maior praticidade, acessibilidade e centralização das informações em um único ambiente digital.
 

```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<title>Contabilizador do Refeitório</title>

<style>
  body {
    font-family: Arial;
    background: #f4f6f8;
    padding: 20px;
  }

  h1 {
    text-align: center;
  }

  .container {
    max-width: 500px;
    margin: auto;
    background: white;
    padding: 20px;
    border-radius: 10px;
    box-shadow: 0 0 10px rgba(0,0,0,0.1);
  }

  .sala {
    display: flex;
    justify-content: space-between;
    margin-bottom: 10px;
  }

  input {
    width: 80px;
    padding: 5px;
  }

  button {
    width: 100%;
    padding: 10px;
    margin-top: 10px;
    border: none;
    border-radius: 5px;
    background: #007bff;
    color: white;
    cursor: pointer;
  }

  button:hover {
    background: #0056b3;
  }

  .total {
    margin-top: 15px;
    font-size: 18px;
    font-weight: bold;
    text-align: center;
  }

  .historico {
    margin-top: 20px;
    font-size: 14px;
  }
</style>
</head>

<body>

<div class="container">
  <h1>Refeitório</h1>

  <div id="salas"></div>

  <button onclick="adicionarSala()">+ Adicionar Sala</button>
  <button onclick="salvar()">Salvar Contagem</button>
  <button onclick="calcular()">Calcular Total</button>

  <div class="total" id="total"></div>

  <div class="historico">
    <h3>Histórico</h3>
    <ul id="historicoLista"></ul>
  </div>
</div>

<script>
let salas = JSON.parse(localStorage.getItem("salas")) || ["Sala 1", "Sala 2"];

function renderizar() {
  const container = document.getElementById("salas");
  container.innerHTML = "";

  salas.forEach((nome, index) => {
    const valor = localStorage.getItem(nome) || 0;

    container.innerHTML += `
      <div class="sala">
        <span>${nome}</span>
        <input type="number" id="input${index}" value="${valor}">
      </div>
    `;
  });
}

function adicionarSala() {
  const nome = prompt("Nome da sala:");
  if (nome) {
    salas.push(nome);
    localStorage.setItem("salas", JSON.stringify(salas));
    renderizar();
  }
}

function salvar() {
  salas.forEach((nome, index) => {
    const valor = document.getElementById("input" + index).value;
    localStorage.setItem(nome, valor);
  });

  alert("Contagem salva!");
}

function calcular() {
  let total = 0;

  salas.forEach(nome => {
    total += parseInt(localStorage.getItem(nome) || 0);
  });

  document.getElementById("total").innerText =
    "Total de refeições: " + total;

  salvarHistorico(total);
}

function salvarHistorico(total) {
  const data = new Date().toLocaleDateString();
  let historico = JSON.parse(localStorage.getItem("historico")) || [];

  historico.push({ data, total });
  localStorage.setItem("historico", JSON.stringify(historico));

  mostrarHistorico();
}

function mostrarHistorico() {
  const lista = document.getElementById("historicoLista");
  lista.innerHTML = "";

  let historico = JSON.parse(localStorage.getItem("historico")) || [];

  historico.forEach(item => {
    lista.innerHTML += `<li>${item.data} - ${item.total} refeições</li>`;
  });
}

renderizar();
mostrarHistorico();
</script>

</body>
</html>
```
