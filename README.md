# 🌌 Fundo Mágico: Seu Background Gerado por IA! 🪄

**Status:** ✨ Completo e Gerando Magia (Trabalho de Faculdade Aprovado!)

Cansado de passar horas no CSS tentando acertar aquele gradiente perfeito? O projeto **Fundo Mágico** usa o poder da **Inteligência Artificial** para transformar uma simples descrição de texto em um **background HTML/CSS** pronto para ser usado. É o Front-end encontrando o futuro!

> 🎓 **Missão Acadêmica (ADS):** Este projeto foi desenvolvido como um trabalho prático para a faculdade de **Análise e Desenvolvimento de Sistemas**. O foco era demonstrar a capacidade de construir uma aplicação web completa que integra as tecnologias básicas (**HTML, CSS, JavaScript**) com um serviço de **Backend/API (n8n)**, simulando a integração com um modelo de IA Generativa.

---

## 🛠️ Tecnologias Envolvidas (O Tripé Mágico)

O Fundo Mágico é uma *Single Page Application* (SPA) com um toque de infraestrutura externa:

| Tecnologia | Função na Aplicação | Destaque Técnico |
| :--- | :--- | :--- |
| **HTML5 & CSS3** | **Interface e Estilo** | Design *Dark Mode* moderno com a fonte **Roboto Mono**. Estrutura para exibir o formulário, o *preview* e os blocos de código gerado. |
| **JavaScript (Vanilla JS)** | **O Motor da Mágica** | Responsável por capturar o *prompt* do usuário, gerenciar o estado de carregamento e fazer a comunicação assíncrona com o *backend*. |
| **n8n / Webhook** | **O Cérebro da IA** | Atua como a API intermediária. O Webhook recebe a requisição do Front-end e (simuladamente) orquestra a chamada a um modelo de IA para gerar o código CSS e HTML. |
| **`fetch` API** | **Comunicação** | Realiza a requisição **POST** assíncrona para a API do n8n, enviando o `prompt` em formato JSON. |

---

## 💡 Destaques Técnicos (Para Avaliadores)

Este projeto demonstra o domínio de conceitos essenciais de desenvolvimento Front-end moderno e integração com APIs.

### 1. ⚙️ Fluxo de Integração e Carregamento (UX)

O código JavaScript (`index.js`) é focado em experiência de usuário (UX) e tratamento de fluxo assíncrono:

* **Prevenção de Recarregamento:** O `event.preventDefault()` é usado para criar uma experiência de SPA, onde apenas o conteúdo é atualizado.
* **Gestão de Estado:** A função `setLoading(true/false)` gerencia o estado do botão para indicar claramente que a geração está em andamento.
* **Tratamento de Erros:** O bloco `try...catch...finally` garante que o carregamento seja desativado e o usuário receba uma mensagem de erro em caso de falha.

### 2. 🧱 Renderização Dinâmica (A Magia Acontece)

A exibição do resultado não é estática, mas sim construída em tempo real:

* **Preview:** O HTML gerado é injetado diretamente na seção `#preview-section`.
* **Estilo Dinâmico:** O CSS retornado pela API é injetado na tag `<head>` da página através da criação de uma tag `<style id="dynamic-style">` via JavaScript, garantindo que o novo fundo seja aplicado **sem recarregar a página**.

```javascript
// Remove o estilo anterior e injeta o novo CSS
let styleTag = document.getElementById("dynamic-style");
if (styleTag) styleTag.remove(); 

if(data.style) {
    styleTag = document.createElement('style');
    styleTag.id = "dynamic-style";
    styleTag.textContent = data.style;
    document.head.appendChild(styleTag);
}
```

### 3. 🎨 Design e Estrutura
Estilo Dark Mode: O CSS é desenhado para um ambiente dark mode (fundo #0f131a).

Estrutura Simples: O HTML é focado na semântica e clareza, com seções dedicadas à entrada (main-card), ao preview (preview-card) e à saída do código (code-grid).
---
### 🚀 Como Executar
Para ver a mágica em ação:

Clone o repositório:

```Bash
git clone [URL_DO_SEU_REPOSITORIO]
Abra o arquivo: Abra o arquivo index.html no seu navegador. Não é necessário servidor local!
```

Teste: Digite um prompt como: "Um gradiente de azul celeste para laranja pôr do sol com um padrão de ondas sutis" e clique em Gerar Background Mágico.
