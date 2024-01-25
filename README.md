# Como salvar o termo

### Passo 1 - Copiar dados do termo na aba atual pro seu clipboard

1- abrir o menu de desenvolvedor
2- abrir a aba console
3- colar o seguinte código:

```javascript
function copiarTermo() {
  var termo = window.localStorage.getItem('termo');
  var duo = window.localStorage.getItem('duo');
  var quatro = window.localStorage.getItem('quatro');

  var result = {};

  if (termo) {
    result.termo = termo;
  }

  if (duo) {
    result.duo = duo;
  }

  if (quatro) {
    result.quatro = quatro;
  }

  var resultString = "let dados = " + JSON.stringify(result) + ";";

  var dummy = document.createElement("textarea");
  document.body.appendChild(dummy);
  dummy.value = resultString;
  dummy.select();
  document.execCommand("copy");
  document.body.removeChild(dummy);
}
```

4- depois, digitar `copiarTermo()` e apertar enter

> isso vai copiar para seu clipboard um código no formato `let dados = <alguma coisa grande>`. **Salve esse código em algum lugar**.

### Passo 2 - "Transferir" o termo para outro computador

1- repetir os passos 1 e 2 do passo 1
2- colar este código:

```javascript
function salvarTermoCopiado() {
  if (dados && dados.termo) {
    window.localStorage.setItem('termo', dados.termo);
  }

  if (dados && dados.duo) {
    window.localStorage.setItem('duo', dados.duo);
  }

  if (dados && dados.quatro) {
    window.localStorage.setItem('quatro', dados.quatro);
  }
}
```

3-digitar `salvarTermoCopiado()` e apertar enter. **CUIDADO**: isto vai sobrescrever os dados do termo atual
