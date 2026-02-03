Docs-Projeto-LM
🛠️ Tecnologias Utilizadas

Docker

n8n

API ViaCEP

Excel (.xlsx)

🧱 Ambiente e Instalação

🔹 Pré-requisitos

Docker Desktop instalado

Navegador web

🔹 Subindo o n8n com Docker

📄 Arquivo docker-compose.yml:

version: '3.1'

services:
  n8n:
    image: n8nio/n8n
    ports:
      - 5678:5678
    environment:
      - N8N_HOST=localhost
      - N8N_PORT=5678
      - N8N_PROTOCOL=http
    volumes:
      - ./n8n_data:/home/node/.n8n
▶️ Comando para iniciar o serviço:

docker compose up -d (CMD DO COMPUTADOR - BARRA DE PESQUISA DENTRO DO ARQUIVO DOCKER)
🌐 Acesso:

http://localhost:5678
🔄 Workflow de Automação:

🔹 Etapas do Fluxo

Trigger Manual

Execução manual do workflow para testes e demonstração.

Edit Fields

Criação de um campo ceps contendo uma lista fixa de CEPs.

Split Out

Conversão do array de CEPs em múltiplos itens individuais.

Loop Over Items

Processamento de cada CEP separadamente.

HTTP Request

Requisição GET para a API pública ViaCEP.

URL dinâmica construída via expressão:

'https://viacep.com.br/ws/' + $json.ceps + '/json/' (Utilizei chaves em destaque do comando , obrigando o n8n a reconhecer a linha como codigo , ao inves de texto)
Tratamento de erro configurado para não interromper o fluxo.

Convert to File

Conversão dos dados retornados em um arquivo Excel (.xlsx).

🌐 API Utilizada: 🔹 ViaCEP

    URL:

      https://viacep.com.br/ws/{CEP}/json/
📁 Saída do Projeto

Arquivo gerado:

data.xlsx
👤 Autor:

Bruno Primo
