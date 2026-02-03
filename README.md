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
📄 Arquivo docker-compose.yml
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

▶️ Comando para iniciar o serviço

Execute o comando abaixo no terminal (CMD ou PowerShell), dentro da pasta onde está o arquivo docker-compose.yml:

docker compose up -d

🌐 Acesso ao n8n

Após subir o container, o n8n estará disponível em:

http://localhost:5678

🔄 Workflow de Automação
🔹 Etapas do Fluxo

1. Trigger Manual
Execução manual do workflow, utilizada para testes e demonstração do funcionamento do fluxo.

2. Edit Fields
Criação de um campo chamado ceps, contendo uma lista fixa de CEPs para consulta.

3. Split Out
Conversão do array de CEPs em múltiplos itens individuais, permitindo o processamento unitário.

4. Loop Over Items
Iteração sobre cada CEP, garantindo que as requisições sejam feitas uma a uma.

5. HTTP Request
Requisição do tipo GET para a API pública ViaCEP.

A URL é construída dinamicamente utilizando expressão no n8n:

'https://viacep.com.br/ws/' + $json.ceps + '/json/'


A expressão foi configurada no modo Expression, permitindo que o n8n interprete o valor como código e não como texto estático.

O tratamento de erro foi configurado para que falhas em um item não interrompam a execução do fluxo.

6. Convert to File
Conversão dos dados retornados pela API em um arquivo Excel (.xlsx).

🌐 API Utilizada
🔹 ViaCEP

Endpoint:

https://viacep.com.br/ws/{CEP}/json/


API pública utilizada para consulta de endereços a partir de CEPs.

📁 Saída do Projeto

Arquivo gerado em formato Excel:

data.xlsx


O arquivo contém os dados retornados pela API ViaCEP para cada CEP processado no fluxo.

👤 Autor

Bruno Primo
