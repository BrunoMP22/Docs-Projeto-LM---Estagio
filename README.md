# Docs-Projeto-LM

## 🛠️ Tecnologias Utilizadas
- Docker  
- n8n  
- API ViaCEP  
- Excel (.xlsx)

---

## 🧱 Ambiente e Instalação

### 🔹 Pré-requisitos
- Docker Desktop instalado  
- Navegador web  

---

## 🔹 Subindo o n8n com Docker

### 📄 Arquivo `docker-compose.yml`
```yaml
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
Execução manual do workflow para testes e demonstração.

2. Edit Fields
Criação de um campo chamado ceps, contendo uma lista fixa de CEPs.

3. Split Out
Conversão do array de CEPs em múltiplos itens individuais.

4. Loop Over Items
Processamento de cada CEP separadamente.

5. HTTP Request
Requisição GET para a API pública ViaCEP.

A URL é construída dinamicamente utilizando expressão no n8n:

'https://viacep.com.br/ws/' + $json.ceps + '/json/'
O fluxo possui tratamento de erro configurado para não interromper a execução em caso de falha.

6. Convert to File
Conversão dos dados retornados em um arquivo Excel (.xlsx).

🌐 API Utilizada
🔹 ViaCEP
Endpoint:

https://viacep.com.br/ws/{CEP}/json/
API pública utilizada para consulta de endereços a partir de CEPs.

📁 Saída do Projeto
Arquivo gerado:

cep.xlsx
O arquivo contém os dados retornados pela API ViaCEP para cada CEP processado.

👤 Autor
Bruno Primo
