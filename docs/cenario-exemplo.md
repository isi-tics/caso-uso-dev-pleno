# 🎯 Cenário de Exemplo - Caso de Uso Lúdico

Imagine que sua equipe foi contratada para desenvolver o backend de um sistema de **Avaliação de Saúde Corporativa** utilizado por clínicas e academias.

Esse sistema precisa permitir que profissionais de saúde criem **formulários personalizados** com campos básicos e campos calculados, por exemplo:

## 🧾 Campos Exemplo do Formulário

```json
[
  {
    "id": "altura",
    "tipo": "number",
    "label": "Altura (cm)",
    "validacoes": [
      { "regra": "valor > 100", "mensagem": "Altura deve ser maior que 100cm" }
    ]
  },
  {
    "id": "peso",
    "tipo": "number",
    "label": "Peso (kg)",
    "validacoes": [
      { "regra": "valor > 30", "mensagem": "Peso deve ser maior que 30kg" }
    ]
  },
  {
    "id": "sexo",
    "tipo": "select",
    "label": "Sexo",
    "opcoes": ["Masculino", "Feminino"]
  },
  {
    "id": "gravidez",
    "tipo": "boolean",
    "label": "Está grávida?",
    "condicional": {
      "regra": "sexo == 'Feminino'",
      "mensagem": "Campo visível apenas se sexo for Feminino"
    }
  },
  {
    "id": "imc",
    "tipo": "calculated",
    "label": "IMC",
    "formula": "peso / ((altura / 100)^2)",
    "fallback": 22.0,
    "dependencias": ["peso", "altura"]
  },
  {
    "id": "classificacao",
    "tipo": "calculated",
    "label": "Classificação de Risco",
    "formula": "if imc > 30 then 'Obesidade' else if imc > 25 then 'Sobrepeso' else 'Normal'",
    "dependencias": ["imc"]
  }
]
```

---

## 📊 Indicadores esperados

Você também precisa implementar agregações como:

- Média de IMC
- Percentual de pessoas com Sobrepeso
- Número de pessoas com Obesidade nos últimos 30 dias
