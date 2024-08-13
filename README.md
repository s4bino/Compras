# Monitoramento de Preços - Compras Paraguai

Este projeto permite monitorar os preços dos produtos do site [Compras Paraguai](https://www.comprasparaguai.com.br).

## Instruções de Uso

Para utilizar o código, siga os passos abaixo:

1. **Pré-requisitos**:
    - Ter o Docker instalado no seu sistema.

2. **Compilação**:
    - No Windows, execute o comando:
      ```bash
      docker-compose up --build
      ```
    - No Linux, execute o comando:
      ```bash
      docker compose up --build
      ```

3. **Utilização**:
    - No formulário, insira apenas links que sigam o formato abaixo:
      ```
      https://www.comprasparaguai.com.br/celular-apple-iphone-15-pro-max-256gb_48864/
      ```
      > **Nota:** Os links **DEVEM** ter exatamente essa estrutura. Qualquer outro formato resultará em erro, pois os dados não poderão ser capturados corretamente.

    - Esses links são os que aparecem quando você clica em um produto na página principal do site.

## Observações

- Este projeto foi desenvolvido para facilitar o monitoramento de preços em um mercado específico. Certifique-se de que os links fornecidos correspondam aos produtos que deseja monitorar.

- Em caso de dúvidas ou problemas, verifique se o formato do link está correto e se o Docker está configurado adequadamente em seu sistema.

### Rotas da Interface do Usuário

- **GET/ **

  - **Descrição:** Serve o arquivo `index.html`, apenas uma visualização do form, futuramente será uma página melhor elaborada sobre o projeto em si.

- **GET /chart**

  - **Descrição:** Serve o arquivo `chart.html`, utilizado para exibir gráficos de produtos.

### Rota de Notificação

- **POST /notify**

  - **Descrição:** Processa o formulário de configuração de alerta e armazena as preferências de alerta.
  - **Corpo da Requisição:** JSON contendo o nome do produto, e-mail e preço desejado para o alerta.
  - **Resposta de Sucesso:**
    ```json
    {
      "message": "Dados recebidos com sucesso e alerta configurado!"
    }
    ```

### Configuração de Email

O projeto utiliza o Nodemailer para enviar e-mails de notificação. O serviço de e-mail e as credenciais devem ser configurados no código.

```javascript
const transporter = nodemailer.createTransport({
    service: 'gmail',
    auth: {
        user: 'example@gmail.com',
        pass: 'password'
    }
});




