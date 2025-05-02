# Projeto API AI

## Visão Geral
Web API _Base_ Spring Boot que integra com os modelos Gemini do Google Cloud Vertex AI. API RESTful para geração de texto baseada em IA usando o serviço Vertex AI Gemini.

## Funcionalidades
- Endpoint de API REST para geração de texto com IA.
- Integração com os modelos Gemini do Google Cloud Vertex AI.
- Configuração baseada em propriedades para ID do projeto, credenciais e localização.

## Integração com o Google Cloud Vertex AI
O projeto integra-se com o Google Cloud Vertex AI utilizando a biblioteca `spring-ai`. As seguintes configurações são utilizadas:

- **ID do Projeto**: Configurado no arquivo `application.properties` como `spring.ai.vertex.ai.gemini.project-id`.
- **Localização das Credenciais**: Definida usando a propriedade `spring.ai.vertex.gemini.credentials.location=${GOOGLE_APPLICATION_CREDENTIALS}`, que aponta para o arquivo de credenciais do Google Cloud.
- **Localização**: A propriedade `spring.ai.vertex.ai.gemini.location=${PROJECT_ID}` especifica a região para o serviço Vertex AI.

### Localizações Permitidas para Modelos Gemini
De acordo com a documentação, as seguintes localizações são suportadas para a propriedade `spring.ai.vertex.ai.gemini.location`:
- `us-central1`
- `europe-west4`
- `asia-east1`

## Como Executar
1. Configure suas credenciais do Google Cloud e certifique-se de que a variável de ambiente `GOOGLE_APPLICATION_CREDENTIALS` aponta para o arquivo de credenciais.
2. Configure o arquivo `application.properties` com o ID do seu projeto no Google Cloud e a localização desejada.
3. Adicione a variável de ambiente `GOOGLE_APPLICATION_CREDENTIALS` no arquivo `launch.json` do VS Code:
   - Abra o arquivo `.vscode/launch.json`.
   - Localize a configuração do projeto.
   - Adicione a seguinte entrada no campo `env`:
     ```json
     "env": {
         "GOOGLE_APPLICATION_CREDENTIALS": "C:\\caminho\\para\\seu\\arquivo_de_credenciais.json",
         "PROJECT_ID": "seu-project-id-do-googlecloud"
     }
     ```
4. Compile e execute a aplicação usando o Maven:
   ```bash
   ./mvnw spring-boot:run
   ```
5. Acesse o endpoint de IA em `http://localhost:8080/ai` com um parâmetro de consulta `userInput`.

## Exemplo de Requisição
```http
GET http://localhost:8080/ai?userInput=Olá, IA!
```

## Dependências
- Spring Boot 3.4.5
- Spring AI Starter para Vertex AI Gemini

## Recursos Adicionais
- [Documentação do Google Cloud Vertex AI](https://cloud.google.com/vertex-ai/docs)
- [Documentação do Spring AI](https://docs.spring.io/spring-ai/docs/current/reference/html/)