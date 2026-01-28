# 🎓 Gerador de Certificados Automatizado (Bubble.io + n8n) -(Projeto de Estudo)

Este é um dos meus primeiros projetos utilizando ferramentas No-Code. O objetivo foi criar um sistema simples que gera um PDF personalizado automaticamente quando o usuário clica em um botão.

## 💡 O que o projeto faz?

É uma aplicação simples onde o usuário:
1. Digita o nome do aluno, curso e carga horária.
2. Escolhe um modelo visual (Moderno, Clássico ou Elegante).
3. Recebe um link para baixar o certificado em PDF pronto.

## 🛠️ Ferramentas que utilizei

Usei três ferramentas diferentes:

* **Bubble.io:** Para criar a tela (Frontend) e o botão de ação.
* **n8n:** Para fazer a lógica "nos bastidores" (Backend). É ele quem recebe os dados e decide qual modelo usar.
* **PDFMonkey:** Para desenhar o certificado (HTML/CSS) e gerar o arquivo final.

## 📸 Demonstração Bubble
### Área para Gerar o Certificado:
#### **SIDEBAR**:
<img width="190" height="723" alt="image" src="https://github.com/user-attachments/assets/a8b11efc-ad8b-4ded-b873-72e8a8a12286" />

### **Tipos de Templates**: 
#### **1 - Moderno:**
<img width="894" height="657" alt="imagem_moderno" src="https://github.com/user-attachments/assets/f628216a-8ebd-4e30-bf27-ce08c6daa34d" />

#### **2 - Clássico:**
<img width="894" height="613" alt="imagem_clássica" src="https://github.com/user-attachments/assets/2a9cca88-d588-46d0-ad5f-f4b7e87fd877" />

#### **3 - Elegante:**
<img width="895" height="675" alt="imagem_elegante" src="https://github.com/user-attachments/assets/1d3cbdee-0f98-4f13-962c-a0f55728a425" />

## **Tela completa**
<img width="1919" height="722" alt="image" src="https://github.com/user-attachments/assets/5a1310f0-9321-4332-91b1-4b5eb50618c6" />

### Área de registro:
<img width="1919" height="530" alt="image" src="https://github.com/user-attachments/assets/61aed6b7-2f45-4275-baa1-7ad6bf8ed0e5" />

 ---
🔗 **Acesse o projeto:** (https://gyovannab23-76958.bubbleapps.io/version-test/?debug_mode=true) 
### OBSERVAÇÃO

**⚠️ Notas Importantes (Leia antes de testar)**

1. **Ambiente de Desenvolvimento:** O link acima roda em modo de teste (`version-test`), por isso você verá uma barra de Debug na parte inferior da tela.
2. **Limites da API:** Este projeto utiliza o plano gratuito do PDFMonkey. **Caso o PDF não seja gerado**, é provável que o limite mensal de processamento da API tenha sido atingido. Se isso acontecer, peço desculpas!


## 📸 Demonstração do n8n
<img width="1107" height="559" alt="image" src="https://github.com/user-attachments/assets/aa1486d5-c586-471d-9fb5-78f165c99fa6" />

## 📸 Demonstração do Certificado Gerado:
![Exemplo do Certificado](<img width="1227" height="872" alt="image" src="https://github.com/user-attachments/assets/066cb31a-62d7-42b2-8717-3e4e6575cb0e" />


---

## 🚀 Sobre o Projeto

Este projeto resolve o problema da geração manual de documentos. Através de uma interface amigável, o usuário insere os dados do aluno e escolhe um modelo visual. O sistema processa tudo em background e devolve um link de download seguro em segundos.
O diferencial deste projeto é a **arquitetura desacoplada**: o Bubble cuida apenas do Frontend e Banco de Dados, enquanto o n8n atua como um Backend lógico, gerenciando regras de negócios e integrações de terceiros.

## ▶️ Vídeo demonstrando o funcionamento:
[Link do Funcionamento](https://drive.google.com/drive/folders/1thV-Qn0doxZ8Fw1yUqcjMQWCKdtDGRlW?usp=sharing) 

## 🛠️ Stack Tecnológico & Arquitetura

O fluxo de dados foi construído da seguinte forma:

1.  **Frontend (Bubble.io):**
    * Captura de dados (Nome, Curso, Carga Horária, Instituto).
    * API Connector configurado para disparo de Webhooks.
    * Lógica de UX para aguardar a resposta da API (Loading states).

2.  **Orquestração (n8n):**
    * **Webhook Receiver:** Recebe o JSON do Bubble.
    * **Switch Logic:** Roteamento condicional inteligente que identifica qual template o usuário escolheu (Moderno, Clássico ou Elegante) e direciona para o fluxo correto.
    * **Tratamento de Erros:** Configuração de "Wait for Completion" para garantir que o link só seja retornado após a renderização total do arquivo.

3.  **Geração de Documentos (PDFMonkey):**
    * Templates HTML/CSS responsivos.
    * Renderização de variáveis dinâmicas e imagens de fundo via URL pública.
```mermaid
graph LR
    A[Usuário/Bubble] -->|JSON Data| B(n8n Webhook)
    B --> C{Switch: Qual Template?}
    C -- Moderno --> D[Template Moderno]
    C -- Clássico --> E[Template Clássico]
    C -- Elegante --> F[Template Elegante]
    D & E & F --> G[Gera Link PDF]
    G -->|Response 200 OK| A
```
---

## 🎥 Demonstração do projeto
Este projeto foi desenvolvido em Bubble, com geração de certificados em PDF
utilizando PDFMonkey e automação via n8n.

## 👨‍💻 Autor
Gyovanna Garcês 
