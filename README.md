# 💡 Simulador de Arduino com JavaScript (Johnny-Five + Mock-Firmata)

Este projeto simula um Arduino usando **JavaScript** com as bibliotecas [Johnny-Five](https://github.com/rwaldron/johnny-five) e [Mock-Firmata](https://github.com/ajfisher/mock-firmata). Ideal para quem quer testar lógica de automação **sem precisar de hardware físico**.

---

## 🚀 Funcionalidade

Simula um LED conectado na porta 13 do Arduino, que **pisca a cada 1 segundo**.

---

## 🧰 Tecnologias utilizadas

- [Node.js](https://nodejs.org/)
- [Johnny-Five](https://www.npmjs.com/package/johnny-five)
- [Mock-Firmata](https://www.npmjs.com/package/mock-firmata)

---

## 🛠️ Como rodar o projeto

### 1. Instale o Node.js

Se ainda não tiver, baixe aqui:  
👉 https://nodejs.org/

### 2. Clone o repositório ou crie o diretório do projeto

```bash
mkdir arduino-js
cd arduino-js
```

### 3. Inicialize o projeto Node.js

```bash
npm init -y
```

### 4. Instale as dependências

```bash
npm install johnny-five mock-firmata
```

### 5. Crie o arquivo `index.js` com o seguinte conteúdo:

```javascript
const five = require("johnny-five");
const MockFirmata = require("mock-firmata").Firmata;

// Cria uma "placa virtual"
const io = new MockFirmata();
const board = new five.Board({
  io: io,
  repl: false,
  debug: false
});

// Quando a "placa" estiver pronta
board.on("ready", () => {
  console.log("Placa virtual pronta!");

  const led = new five.Led(13);

  let estado = false;

  // Pisca o LED virtual a cada 1 segundo
  setInterval(() => {
    estado = !estado;
    if (estado) {
      led.on();
      console.log("LED ligado");
    } else {
      led.off();
      console.log("LED desligado");
    }
  }, 1000);
});
```

### 6. Execute o projeto

```bash
node index.js
```

Você verá no terminal:

```
Placa virtual pronta!
LED ligado
LED desligado
LED ligado
...
```

---

## ✅ Próximos passos sugeridos

- Criar lógica de botão virtual (`five.Button`)
- Simular sensores ou servos
- Integrar com uma interface web usando Express.js

---

## 📄 Licença

Este projeto é livre para estudo e modificação. Sem restrições de uso pessoal ou educacional.

---

Feito com 💻 e ☕ por [Juancjc]
