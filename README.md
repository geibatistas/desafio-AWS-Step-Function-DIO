# 🚀 Desafio AWS Step Functions – Bootcamp AWS - DIO

## 📖 Descrição
Este repositório contém a prática realizada durante o Bootcamp AWS, explorando o serviço **AWS Step Functions** para orquestração de workflows automatizados.  
O objetivo é consolidar conceitos de automação, mensageria e boas práticas de arquitetura em nuvem, integrando serviços como **Lambda, S3, SNS, SQS e DynamoDB**.

---

## 🎯 Objetivos de Aprendizagem
- Aplicar conceitos de orquestração em um ambiente prático.  
- Documentar processos técnicos de forma clara e estruturada.  
- Utilizar o GitHub como ferramenta de compartilhamento de documentação técnica.  

---

## 🛠️ Passo a Passo Realizado
1. **Criação das funções Lambda**  
   - `validateFileLambda`: valida se o arquivo possui extensão `.csv`.  
   - `processFileLambda`: simula processamento do arquivo.  

2. **Criação da tabela DynamoDB**  
   - Nome: `FileResults`.  
   - Chave primária: `FileName` (String).  

3. **Criação do tópico SNS**  
   - Nome: `FileValidatedTopic`.  
   - Usado para notificação de sucesso.  

4. **Montagem da máquina de estado no Step Functions**  
   - Estados: `ValidateFile` → `ProcessFile` → `SaveToDynamoDB` → `NotifySuccess`.  
   - Integração com Lambda, DynamoDB e SNS.  

5. **Execução e monitoramento**  
   - Teste com input JSON:  
     ```json
     {
       "fileName": "teste.csv"
     }
     ```
   - Execução bem-sucedida registrada no console.  

---

## 💡 Erros enfrentados e soluções
- **ARN incorreto (conta diferente)**  
  - Erro: *“Expected ACCOUNT_ID, was 123456789012”*.  
  - Solução: substituir pelo ARN da Lambda na mesma conta e região.  

- **Runtime da Lambda**  
  - Erro: *“exports is not defined in ES module scope”*.  
  - Solução: usar runtime Node.js 18.x com `index.js` e `exports.handler`.  

- **Tabela DynamoDB inexistente**  
  - Erro: falha no `PutItem`.  
  - Solução: criar tabela `FileResults` com chave primária `FileName`.  

- **Tópico SNS inexistente**  
  - Erro: *“InvalidClientTokenId”*.  
  - Solução: criar tópico SNS `FileValidatedTopic` e atualizar ARN no JSON.  

---

## 📂 Estrutura do Repositório

