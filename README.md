# 🍽️ Assistente de Delivery com AWS Step Functions e Bedrock 🚀

## 🌟 Descrição
Este projeto consiste em um assistente de delivery que sugere um menu completo, incluindo comida, bebida e localização, utilizando AWS Step Functions e AWS Lambda.

## 🛠️ Tecnologias Utilizadas
- **AWS Step Functions**: Orquestração de microserviços
- **AWS Lambda**: Funções sem servidor para sugestões
- **JSON**: Estrutura de dados para o workflow

## 🔗 Link do GitHub
[Visite meu GitHub!](https://github.com/Rafael2k03)

## 🚀 Como Funciona
1. **GetFoodSuggestion**: Invoca uma função Lambda para obter sugestões de comida.
2. **GetDrinkSuggestion**: Invoca uma função Lambda para obter sugestões de bebida.
3. **GetLocationSuggestion**: Invoca uma função Lambda para obter sugestões de localização.
4. **CompileMenu**: Compila todas as sugestões em um menu completo.

## 🔧 Configuração
Para replicar este projeto, você precisará:
1. Criar funções Lambda para `suggest-food`, `suggest-drink` e `suggest-location`.
2. Substituir `REGION` e `ACCOUNT_ID` nos ARNs das funções.
3. Implantar o workflow no AWS Step Functions.

## 📝 Exemplo de Código
```json
{
  "Comment": "🍽️✨ Workflow to create a complete menu suggestion - by Rafael Gonçalves 🧑‍💻",
  "StartAt": "GetFoodSuggestion",
  "States": {
    "GetFoodSuggestion": {
      "Type": "Task",
      "Resource": "arn:aws:states:::lambda:invoke",
      "Parameters": {
        "FunctionName": "arn:aws:lambda:REGION:ACCOUNT_ID:function:suggest-food",
        "Payload": {}
      },
      "ResultPath": "$.menu.food",
      "Next": "GetDrinkSuggestion"
    },
    // Outros estados...
  }
}
