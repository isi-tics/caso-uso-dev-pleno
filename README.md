
# Caso de Uso - Desenvolvedor Pleno


O desafio enfatiza o **backend e arquitetura**, com possibilidade de implementações adicionais:

### Essenciais para Destaque
- **Código limpo e legível**, seguindo princípios do Clean Code (nomes significativos, pequenas funções, baixo acoplamento, alta coesão)
- **Arquitetura consistente** com separação clara entre camadas (MVC, DDD, Hexagonal)
- **Tratamento de erros** e respostas HTTP padronizadas (mensagens claras e status codes corretos)
- **Documentação técnica clara** no README.md explicando setup, execução e decisões técnicas
- **Uso consciente de bibliotecas** externas com explicações das escolhas de dependência

## O Que Será Avaliado

| Item                      | Obrigatório? | Peso |
|---------------------------|--------------|------|
| Engine funcional          |             | ★★★★★ |
| Justificativas técnicas  |             | ★★★★☆ |
| Testes automatizados     |             | ★★★★☆ |
| Organização do código    |             | ★★★★☆ |
| Documentação clara       |             | ★★★☆☆ |

---

### Diferenciais Técnicos que Contam Pontos

*Estas funcionalidades **não são obrigatórias**, mas demonstram maturidade técnica e visão sistêmica avançada:*

- **Interface frontend responsiva** — SPA (React/Vue/Angular) que consuma a API, demonstrando visão completa do produto e experiência full-stack

- **Docker containerizado** — `Dockerfile` + `docker-compose.yml` para ambiente isolado e deploy simplificado (facilita avaliação)

- **Validação robusta ** — Sanitização de entradas (prevent XSS), validação de schema.

- **Rate limiting** — Throttling por IP/usuário para proteção contra abuso e DDoS (express-rate-limit ou equivalente)

- **Cache inteligente** — Otimização de recálculos de formulários complexos usando memória ou Redis (evita processamento redundante)

- **Processamento paralelo** — Execução concorrente de múltiplos formulários usando workers/threads (worker_threads ou cluster)

- **RESTful + OpenAPI** — API bem estruturada com versionamento (/v1/forms) e documentação Swagger automática (swagger-jsdoc)

- **Variáveis de ambiente** — Externalização de configs (.env) com validação de schema no startup (dotenv + validação)

- **Migrations estruturadas** — Versionamento de banco com rollback e evolução controlada do schema (Knex.js/Prisma migrations)

- **Code coverage + quality gates** — Cobertura mínima de testes (85%+) com ferramentas de análise de código (nyc/c8 + ESLint)

- **Testes de mutação** — Property-based testing (fast-check) e mutation testing (Stryker) para validar robustez dos testes

- **Audit logs detalhados** — Rastreamento completo de operações (Winston + structured logging)

- **Plugin system** — Sistema extensível para validadores customizados por domínio de negócio (strategy pattern + dynamic loading)

**Estratégia recomendada:** Seleção de 2-3 itens que mais demonstrem forças técnicas ao invés de implementação superficial de todos os itens.

---

## Sobre Este Desafio

O desafio simula **cenários reais de arquitetura** encontrados em **sistemas críticos de produção**. A solução deve demonstrar **competência técnica sólida**, **maturidade arquitetural** e **visão sistêmica**.

O objetivo é avaliar a capacidade de **tomar decisões técnicas fundamentadas**, **comunicar trade-offs de forma clara** e **entregar software robusto** que funcione em ambiente real, com potencial para crescer e evoluir.

### Competências Fundamentais de um Desenvolvedor Pleno

As competências esperadas para desenvolvedor pleno incluem domínio nas seguintes áreas:

**Arquitetura e Design**
- **Decisões arquiteturais fundamentadas** com justificativas claras e comunicação efetiva
- **Balanceamento consciente de trade-offs** entre performance, manutenibilidade, extensibilidade e time-to-market
- **Sistemas resilientes** com tratamento gracioso de falhas e recuperação automática
- **Design patterns aplicados estrategicamente** com justificativa de uso e contexto apropriado

**Qualidade de Código e Engenharia**
- **Clean Code e princípios SOLID** aplicados consistentemente em toda a base de código
- **Testes estratégicos** que validam comportamentos críticos do sistema
- **Modelagem de domínio** com abstrações apropriadas ao contexto de negócio
- **Gestão consciente de dependências** e controle de acoplamento entre módulos
- **APIs consistentes** que facilitam integração, manutenção e evolução

**Aspectos Operacionais e Observabilidade**
- **Documentação técnica viva** através de ADRs e código autodocumentado
- **Observabilidade integrada** para debugging, monitoramento e troubleshooting
- **Segurança por design** aplicada em todas as camadas da aplicação
- **Otimização baseada em dados** usando profiling e métricas reais
- **Estratégias de deploy** e operação em ambientes produtivos
- **Antecipação de requisitos futuros** sem over-engineering
- **Trabalho efetivo com constraints** técnicos e limitações de infraestrutura

### Contexto de Negócio: Caso de Uso

**Cenário:** Desenvolvimento do **núcleo arquitetural** de uma plataforma de formulários inteligentes de **missão crítica**. A solução constitui a **base tecnológica** para unificar e modernizar múltiplos sistemas legados de uma grande corporação multinacional, substituindo décadas de soluções fragmentadas por uma **arquitetura consistente e escalável**.

**Stakeholders envolvidos:**
- **Área da Saúde**: Formulários de triagem médica com cálculos automáticos de risco
- **Setor Industrial**: Checklists de segurança com validações cruzadas obrigatórias
- **Compliance Fiscal**: Formulários tributários com regras complexas de negócio
- **Auditoria Interna**: Necessidade de rastreabilidade completa de todas as operações

**O Problema:**
A empresa atualmente possui múltiplos sistemas legados, cada um com sua própria lógica de formulários. Isso gera:
- **Inconsistências** entre diferentes áreas
- **Retrabalho** constante para implementar mudanças similares
- **Falta de auditoria** centralizada
- **Performance degradada** em formulários complexos
- **Dificuldade para evoluir** regras de negócio

**Objetivo da Solução:**
A engine de formulários universal deve servir como base para todos esses sistemas críticos, mantendo:

**Confiabilidade Absoluta**
- O sistema nunca pode falhar silenciosamente - toda falha deve ser explícita e tratada
- Mecanismos de fallback automático quando cálculos falham
- Validação rigorosa de entrada e saida para prevenir estados inconsistentes

**Auditabilidade Completa**
- Rastreamento granular de cada execução, incluindo valores intermediários
- Versionamento de formulários para manter histórico de mudanças

**Extensibilidade Empresarial**
- Arquitetura modular que permita adicionar novos tipos de campo sem quebrar o existente
- Configuração declarativa que não exija alterações de código para mudanças simples

---

# Especificação Técnica e Modelagem do Sistema

## Visão Geral das APIs

A API para serviço **formulários** deve ser capaz de:

- Criar formulários com campos dinâmicos e regras entre campos e tipos;
- Executar fórmulas que dependem de múltiplos outros campos;
- Validar dados de forma contextual e condicional;
- Detectar inconsistências técnicas e semânticas;



## **POST /formularios**

### Finalidade

Cria um novo formulário inteligente, com campos dinâmicos, regras de exibição, cálculos e validações contextuais. Cada novo formulário recebe automaticamente um `schema_version` iniciado em `1`.

---

### Regras de Negócio

* Cada formulário criado é versionado automaticamente. O primeiro envio sempre cria `schema_version: 1`.
* Campos com `id` duplicado devem ser rejeitados.
* Todos os campos do schema devem conter `tipo` válido e propriedades obrigatórias.
* Regras inválidas como `idade >` (incompleta) ou `campoA &&` devem gerar erro.

### Campos do Sistema

Todos os formulários possuem campos de controle automáticos:

| Campo | Tipo | Descrição |
|-------|------|-----------|
| `id` | string | Identificador único do formulário |
| `schema_version` | integer | Versão atual do schema (incremental) |
| `is_ativo` | boolean | Status do formulário (true = ativo, false = removido) |
| `data_criacao` | datetime | Timestamp de criação do formulário |
| `data_remocao` | datetime | Timestamp de remoção lógica (null se ativo) |
| `usuario_remocao` | string | ID do usuário que removeu o formulário |
| `protegido` | boolean | Se true, impede remoção manual do formulário |

---

### Requisição

**Cabeçalhos HTTP obrigatórios:**

```http
Content-Type: application/json
Accept: application/json
```

### Corpo da Requisição (Request Body)

```json
{
  "nome": "Ficha de Admissão",
  "descricao": "Formulário usado no onboarding de colaboradores",
  "campos": [
    {
      "id": "nome_completo",
      "label": "Nome completo",
      "tipo": "text",
      "obrigatorio": true,
      "capitalizar": true,
      "multilinha": false,
      "validacoes": [
        { "tipo": "tamanho_minimo", "valor": 5 },
        { "tipo": "regex", "valor": "^[A-Z][a-z]+( [A-Z][a-z]+)*$" }
      ]
    },
    {
      "id": "idade",
      "label": "Idade",
      "tipo": "number",
      "formato": "inteiro",
      "obrigatorio": true,
      "validacoes": [
        { "tipo": "minimo", "valor": 18 },
        { "tipo": "maximo", "valor": 65 }
      ]
    },
    {
      "id": "aceita_termos",
      "label": "Aceita os termos e condições?",
      "tipo": "boolean",
      "obrigatorio": true,
      "condicional": "idade >= 18"
    }
  ]
}
```

---

### Validações

| Campo           | Regra                                                                                       |
| --------------- | ------------------------------------------------------------------------------------------- |
| `nome`          | Obrigatório, no máximo 255 caracteres.                                                      |
| `descricao`     | Opcional, até 500 caracteres.                                                              |
| `campos`        | Array obrigatório com no mínimo 1 e no máximo 100 campos.                                   |
| `campos[].id`   | Deve ser único, alfanumérico, sem espaços ou símbolos.                                      |
| `campos[].tipo` | Deve ser um dos tipos válidos: `text`, `number`, `date`, `select`, `boolean`, `calculated`. |

---

### Respostas

####  Sucesso – 201 Created

```json
{
  "id": "formulario_001",
  "schema_version": 1,
  "mensagem": "Formulário criado com sucesso",
  "criado_em": "2024-01-15T10:34:00Z"
}
```

####  Erros

**400 – Payload inválido**

```json
{
  "erro": "payload_invalido",
  "mensagem": "O campo 'campos' deve conter ao menos um item válido"
}
```

**422 – Erro de regras**

```json
{
  "erro": "regra_invalida",
  "campo": "idade",
  "mensagem": "Valor máximo não pode ser menor que o valor mínimo"
}
```

**409 – ID duplicado**

```json
{
  "erro": "id_duplicado",
  "campo": "nome_completo",
  "mensagem": "Já existe um campo com o id 'nome_completo'"
}
```

---

## **GET /formularios**

### Finalidade

Retorna a lista de formulários cadastrados no sistema, com suporte a filtros, paginação e ordenação. A API permite navegar pelos formulários existentes, realizar buscas por nome ou versão e preparar a visualização para uso administrativo ou operacional.

---

### Regras de Negócio

* O sistema deve retornar apenas formulários ativos (não deletados logicamente).
* Se não for passado nenhum filtro, todos os formulários ativos são retornados (limitados por `page_size`).
* Os filtros por nome são case-insensitive e parciais.
* A paginação padrão é de 20 registros por página, limitada a no máximo 100 por `page_size`.

---

### Parâmetros de Consulta (Query Params)

| Parâmetro        | Tipo    | Descrição                                                              |
| ---------------- | ------- | ---------------------------------------------------------------------- |
| `nome`           | string  | (opcional) Filtra formulários que contenham o texto informado no nome. |
| `schema_version` | integer | (opcional) Filtra por versão exata do schema.                          |
| `pagina`         | integer | Página desejada. Começa em 1. Padrão: 1.                               |
| `tamanho_pagina` | integer | Quantidade de itens por página. Padrão: 20. Máximo: 100.               |
| `ordenar_por`    | string  | (opcional) Campo para ordenação. Aceita: `nome`, `criado_em`.          |
| `ordem`          | string  | (opcional) `asc` ou `desc`. Padrão: `asc`.                             |

---

### Requisição

```http
GET /formularios?nome=onboarding&pagina=2&tamanho_pagina=10&ordenar_por=criado_em&ordem=desc
Accept: application/json
```

---

### Resposta – 200 OK

```json
{
  "pagina_atual": 2,
  "total_paginas": 5,
  "total_itens": 47,
  "formularios": [
    {
      "id": "formulario_001",
      "nome": "Onboarding RH",
      "schema_version": 2,
      "criado_em": "2024-01-15T10:34:00Z"
    },
    {
      "id": "formulario_002",
      "nome": "Onboarding Operacional",
      "schema_version": 1,
      "criado_em": "2024-01-10T16:10:00Z"
    }
  ]
}
```

---

### Respostas de Erro

####  400 – Parâmetro inválido

```json
{
  "erro": "parametro_invalido",
  "campo": "tamanho_pagina",
  "mensagem": "O parâmetro tamanho_pagina deve ser menor ou igual a 100."
}
```

####  422 – Filtro malformado

```json
{
  "erro": "filtro_invalido",
  "mensagem": "O campo 'ordenar_por' deve ser um dos valores permitidos: nome, criado_em."
}
```

---

## **GET /formularios/:id**

### Finalidade

Retorna todas as informações de um formulário específico, incluindo seu schema completo, versão e estrutura de campos. A API é utilizada tanto para exibição quanto para montagem dinâmica do formulário no frontend.

---

### Regras de Negócio

* O `id` informado deve corresponder a um formulário existente e ativo.
* O schema retornado **deve conter todos os campos com todas as suas propriedades e regras**, conforme especificado na definição de schema.
* Se o formulário estiver obsoleto (excluído logicamente ou substituído), deve retornar erro.
* Campos do tipo `calculated` devem estar com suas fórmulas e dependências bem resolvidas.
* Campos ocultos por `condicional` ainda são retornados na definição — a lógica de exibição é feita no cliente.

---

### Requisição

```http
GET /formularios/formulario_001
Accept: application/json
```

---

### Resposta – 200 OK

```json
{
  "id": "formulario_001",
  "nome": "Formulário de Onboarding RH",
  "descricao": "Formulário utilizado no processo de integração de novos colaboradores.",
  "schema_version": 2,
  "criado_em": "2024-01-15T10:34:00Z",
  "campos": [
    {
      "id": "nome_completo",
      "label": "Nome completo",
      "tipo": "text",
      "obrigatorio": true,
      "tamanho_maximo": 100,
      "regex": "^[A-Z][a-z]+( [A-Z][a-z]+)+$"
    },
    {
      "id": "data_nascimento",
      "label": "Data de nascimento",
      "tipo": "date",
      "minima": "1900-01-01",
      "maxima": "2030-12-31",
      "obrigatorio": true
    },
    {
      "id": "idade",
      "label": "Idade (calculada)",
      "tipo": "calculated",
      "formula": "floor((today() - data_nascimento) / 365.25)",
      "dependencias": ["data_nascimento"],
      "precisao": 0
    },
    {
      "id": "aceite_politica",
      "label": "Aceito a política de privacidade?",
      "tipo": "boolean",
      "obrigatorio": true
    },
    {
      "id": "area_atuacao",
      "label": "Área de atuação",
      "tipo": "select",
      "opcoes": [
        { "label": "Engenharia", "value": "eng" },
        { "label": "Recursos Humanos", "value": "rh" },
        { "label": "Financeiro", "value": "fin" }
      ],
      "obrigatorio": true
    }
  ]
}
```

---

### Respostas de Erro

####  404 – Formulário não encontrado

```json
{
  "erro": "formulario_nao_encontrado",
  "mensagem": "O formulário com id 'formulario_001' não foi localizado ou está inativo."
}
```

####  422 – ID malformado

```json
{
  "erro": "id_invalido",
  "mensagem": "O identificador do formulário informado não é válido."
}
```

### Regras extras:

* Caso o schema contenha referências circulares entre `calculated`, a API deve abortar com erro 500 e registrar o incidente.
* Campos `condicional` devem ser retornados como string, mesmo que baseados em booleans.

---

## **DELETE /formularios/:id**

### Finalidade

Marca um formulário como **removido logicamente**, sem apagar fisicamente os dados do banco. A operação também **inativa todas as versões e impede novos envios de respostas**, mas **preserva**:

* O histórico de versões (schemas)
* As respostas associadas
* Os metadados e logs

---

### Parâmetros de URL

| Parâmetro | Tipo   | Obrigatório | Descrição                                   |
| --------- | ------ | ----------- | ------------------------------------------- |
| `id`      | string | Sim         | Identificador do formulário a ser removido. |

---

### Requisição

Nenhum corpo (`body`) é necessário.

---

### Regras de Negócio

* O formulário **não é excluído fisicamente**, apenas marcado como:

  ```json
  {
    "is_ativo": false,
    "data_remocao": "2024-03-15T23:59:59Z",
    "usuario_remocao": "usuario_admin"
  }
  ```
* Todas as versões (`schemas`) do formulário também recebem `is_ativo: false`.
* Nenhuma nova resposta pode ser enviada após a remoção lógica.
* As **respostas existentes permanecem intactas**, podendo ser acessadas normalmente (ex: para auditoria, dashboards ou reprocessamento).
* Se o formulário já estiver removido (`is_ativo: false`), a operação é **idempotente** (retorna 200 OK).
* A remoção lógica só é permitida se o formulário **não estiver em uso exclusivo por outro sistema** (ex: com `protegido: true`).

---

### Exemplo de Requisição

```http
DELETE /formularios/formulario_abc
Accept: application/json
```

---

### Resposta – 200 OK

```json
{
  "mensagem": "Formulário 'formulario_abc' marcado como removido com sucesso. Nenhuma resposta foi excluída.",
  "status": "soft_deleted"
}
```

---

### Casos de Erro

####  404 – Formulário inexistente

```json
{
  "erro": "formulario_nao_encontrado",
  "mensagem": "Nenhum formulário com ID 'formulario_abc' foi encontrado no sistema."
}
```

####  409 – Formulário protegido

```json
{
  "erro": "formulario_protegido",
  "mensagem": "Este formulário é protegido e não pode ser removido manualmente."
}
```

####  500 – Falha ao atualizar status lógico

```json
{
  "erro": "falha_remocao_logica",
  "mensagem": "Erro interno ao marcar o formulário como removido. Nenhuma alteração foi feita."
}
```

---

### Considerações Técnicas

* A lógica de soft delete deve atualizar os campos:

  * `is_ativo: false`
  * `data_remocao`: timestamp do momento da operação
  * `usuario_remocao`: usuário ou token responsável
* A listagem de formulários (`GET /formularios`) **não deve exibir formulários inativos**, a menos que explicitamente solicitado via filtro `?incluir_inativos=true`.
* A consulta por ID (`GET /formularios/:id`) pode retornar o formulário inativo, mas com o status destacado:

  ```json
  {
    "id": "formulario_abc",
    "is_ativo": false,
    "mensagem": "Este formulário foi removido em 2024-03-15 por usuario_admin."
  }
  ```
* Logs de remoção devem ser armazenados para fins de auditoria.

---

## **PUT /formularios/:id/schema_version**

### Finalidade

Cria uma **nova versão do formulário**, atualizando o schema e, opcionalmente, metadados como nome e descrição. Este endpoint é crítico para garantir versionamento controlado, mantendo o histórico de versões anteriores e compatibilidade com respostas antigas.

---

### Regras de Negócio

* O formulário identificado por `:id` **deve existir** e estar ativo.
* O campo `schema_version` identifica numericamente a versão do schema que está sendo publicada.
* O novo schema **não pode ter versão inferior** à versão atual do formulário.
* Metadados como `nome`, `descricao`, `tags`, etc., podem ser atualizados junto com o novo schema.
* Todos os campos enviados substituem completamente o schema anterior. O sistema não faz merge.
* Campos `calculated` podem depender de campos `calculated` anteriores, desde que não haja ciclo.

---

### Requisição

```http
PUT /formularios/formulario_001/schema_version
Content-Type: application/json
```

#### Corpo (exemplo completo)

```json
{
  "schema_version": 3,
  "nome": "Formulário de Cadastro de Pessoas (v3)",
  "descricao": "Versão revisada com validações de idade e ocupação",
  "campos": [
    {
      "id": "nome_completo",
      "label": "Nome completo",
      "tipo": "text",
      "obrigatorio": true,
      "tamanho_maximo": 100
    },
    {
      "id": "data_nascimento",
      "label": "Data de nascimento",
      "tipo": "date",
      "minima": "1900-01-01",
      "maxima": "2030-12-31"
    },
    {
      "id": "idade",
      "label": "Idade (auto)",
      "tipo": "calculated",
      "formula": "floor((today() - data_nascimento) / 365.25)",
      "dependencias": ["data_nascimento"],
      "precisao": 0
    },
    {
      "id": "ocupacao",
      "label": "Área de atuação",
      "tipo": "select",
      "opcoes": [
        { "label": "TI", "value": "ti" },
        { "label": "Educação", "value": "edu" },
        { "label": "Saúde", "value": "saude" }
      ]
    },
    {
      "id": "e_maior_de_idade",
      "label": "É maior de idade?",
      "tipo": "calculated",
      "formula": "idade >= 18",
      "dependencias": ["idade"]
    }
  ]
}
```

---

### Resposta – 200 OK

```json
{
  "mensagem": "Versão atualizada com sucesso.",
  "id": "formulario_001",
  "schema_version_anterior": 2,
  "schema_version_nova": 3,
  "atualizado_em": "2024-03-15T15:20:00Z"
}
```

---
### Casos de Erro

####  422 – Schema ID já utilizado

```json
{
  "erro": "schema_version_invalida",
  "mensagem": "A versão 3 é inferior ou igual à versão atual do formulário."
}
```

####  422 – Validação dos campos

```json
{
  "erro": "schema_invalido",
  "mensagem": "Há erros nos campos do novo schema.",
  "erros": [
    {
      "campo": "idade",
      "mensagem": "Dependência 'data_nascimento' não existe no schema."
    },
    {
      "campo": "ocupacao",
      "mensagem": "Valores duplicados detectados em 'opcoes'."
    }
  ]
}
```

---

## **POST /formularios/:id/respostas**

### Finalidade

Recebe os dados preenchidos de um formulário, valida os campos, aplica regras condicionais e cálculos, e registra o resultado. Gera também logs completos de execução para rastreabilidade futura.

---

### Regras de Negócio

* O formulário `:id` **deve existir** e estar ativo.
* A versão do schema será assumida como a **mais recente**, a menos que o payload inclua explicitamente `schema_version`.
* Todos os campos obrigatórios devem estar presentes e válidos.
* Campos do tipo `calculated` **não precisam ser enviados** pelo cliente — serão computados automaticamente.
* Campos com dependência condicional (exibição, obrigatoriedade, etc.) só são validados **se visíveis ou aplicáveis no contexto**.
* Todas as validações são **atomizadas**: múltiplos erros são retornados em uma única resposta.

---

### Requisição

```http
POST /formularios/formulario_001/respostas
Content-Type: application/json
```

#### Corpo (Exemplo)

```json
{
  "schema_version": 3,
  "respostas": {
    "nome_completo": "Maria Santos",
    "data_nascimento": "1995-02-14",
    "ocupacao": "ti"
  }
}
```

>  Note: `idade` e `e_maior_de_idade` não são enviados pois são calculados.

---

### Resposta – 201 Created

```json
{
  "mensagem": "Resposta registrada com sucesso.",
  "id_resposta": "resposta_12345",
  "calculados": {
    "idade": 30,
    "e_maior_de_idade": true
  },
  "executado_em": "2024-03-15T22:12:01Z"
}
```

---

### Esquema de Validação (Schema Simplificado)

```json
{
  "type": "object",
  "required": ["respostas"],
  "properties": {
    "schema_version": {
      "type": "string",
      "type": "integer",
      "description": "Opcional. Se omitido, usa a última versão disponível."
    },
    "respostas": {
      "type": "object",
      "description": "Dicionário de respostas por campo",
      "patternProperties": {
        "^[a-z0-9_]+$": {}
      },
      "additionalProperties": true
    }
  }
}
```

---

### Casos de Erro

####  400 – Campos obrigatórios ausentes

```json
{
  "erro": "validacao_falhou",
  "mensagem": "Alguns campos obrigatórios não foram preenchidos.",
  "erros": [
    {
      "campo": "nome_completo",
      "mensagem": "Campo obrigatório não informado."
    }
  ]
}
```

####  422 – Inconsistência semântica

```json
{
  "erro": "inconsistencia_negocio",
  "mensagem": "Dados inconsistentes detectados.",
  "erros": [
    {
      "campo": "idade",
      "mensagem": "O valor calculado está abaixo do permitido para esta ocupação."
    }
  ]
}
```

####  409 – Schema obsoleto

```json
{
  "erro": "schema_desatualizado",
  "mensagem": "A versão do schema informada não é mais aceita para novos envios."
}
```

---

## **GET /formularios/:id/respostas**

### Finalidade

Retorna uma **lista paginada** de respostas para o formulário identificado por `:id`, permitindo:

* Filtrar por qualquer campo de resposta;
* Incluir/excluir campos calculados;
* Navegar por páginas com tamanho customizável;
* Obter os nomes dos campos no formato amigável.

---

### Parâmetros de URL

| Parâmetro | Tipo   | Obrigatório | Descrição                                        |
| --------- | ------ | ----------- | ------------------------------------------------ |
| `id`      | string | Sim         | ID do formulário cujas respostas serão listadas. |

---

### Parâmetros de Query (Filtros)

| Parâmetro            | Tipo    | Descrição                                                    |
| -------------------- | ------- | ------------------------------------------------------------ |
| `pagina`             | integer | Página atual (default: 1).                                   |
| `tamanho_pagina`     | integer | Tamanho da página (default: 20, máximo: 100).                |
| `incluir_calculados` | boolean | Se `true`, inclui os campos calculados no retorno.           |
| `schema_version`     | integer | Filtra apenas respostas associadas a essa versão do schema.  |
| `campo_<idCampo>`    | variado | Filtro por valor de qualquer campo. Ex: `campo_ocupacao=ti`. |

>  Os filtros por `campo_` aplicam-se diretamente às chaves das respostas.

---

### Exemplo de Requisição

```http
GET /formularios/formulario_001/respostas?pagina=1&tamanho_pagina=10&incluir_calculados=true&campo_ocupacao=ti
Accept: application/json
```

---

### Resposta – 200 OK

```json
{
  "pagina": 1,
  "tamanho_pagina": 10,
  "total": 42,
  "resultados": [
    {
      "id_resposta": "resposta_67890",
      "criado_em": "2024-03-15T22:10:01Z",
      "schema_version": 3,
      "respostas": {
        "nome_completo": "Maria Santos",
        "data_nascimento": "1995-02-14",
        "ocupacao": "ti"
      },
      "calculados": {
        "idade": 30,
        "e_maior_de_idade": true
      }
    }
  ]
}
```

---

### Campos do Retorno

| Campo         | Tipo     | Descrição                                                 |
| ------------- | -------- | --------------------------------------------------------- |
| `pagina`      | integer  | Página atual.                                             |
| `limite`      | integer  | Tamanho da página.                                        |
| `total`       | integer  | Total de respostas encontradas.                           |
| `resultados`  | array    | Lista das respostas encontradas.                          |
| `id_resposta` | string   | Identificador único da resposta.                          |
| `schema_version` | integer | Número da versão do formulário utilizada no envio. |
| `respostas`   | objeto   | Campos preenchidos pelo usuário.                          |
| `calculados`  | objeto   | Campos calculados pelo sistema (opcional).                |
| `criado_em`   | datetime | Timestamp de envio da resposta.                           |

---

### Casos de Erro

####  404 – Formulário não encontrado

```json
{
  "erro": "formulario_nao_encontrado",
  "mensagem": "O formulário formulario_001 não existe ou está inativo."
}
```

####  400 – Filtros inválidos

```json
{
  "erro": "parametros_invalidos",
  "mensagem": "O parâmetro campo_idade deve ser um número inteiro.",
  "campo": "campo_idade"
}
```

####  422 – Página fora do intervalo

```json
{
  "erro": "pagina_invalida",
  "mensagem": "A página 9999 não contém resultados."
}
```

---

### Boas Práticas

* Utilize `incluir_calculados=false` se quiser apenas os dados enviados.
* Use filtros pelo campo de interesse via `campo_<id>`, com correspondência exata.

---

## **DELETE /formularios/:id/respostas/:id_resposta**

### Finalidade

Marca uma **resposta específica de um formulário como inativa** (`is_ativo: false`), sem apagar os dados do banco. A remoção lógica é usada para manter rastreabilidade, auditoria e consistência histórica, especialmente em ambientes com regras de conformidade (LGPD, ISO, etc.).

---

### Parâmetros de URL

| Parâmetro     | Tipo   | Obrigatório | Descrição                                           |
| ------------- | ------ | ----------- | --------------------------------------------------- |
| `id`          | string | Sim         | ID do formulário ao qual a resposta está vinculada. |
| `id_resposta` | string | Sim         | ID da resposta a ser removida.                      |

---

### Requisição

Não requer body (`body` vazio).

---

### Regras de Negócio

* A resposta **não é excluída fisicamente**, mas marcada com:

  ```json
  {
    "is_ativo": false,
    "data_remocao": "2024-03-15T23:59:59Z",
    "usuario_remocao": "usuario_admin"
  }
  ```
* Não pode remover uma resposta:

  * De um formulário inativo (`is_ativo: false`)
  * Que já está removida (operação é idempotente)
* O `usuario_remocao` deve ser rastreável (ID de quem disparou a exclusão).
* A API deve rejeitar a exclusão se a resposta estiver **congelada**, por exemplo:

  * Enviada como parte de um laudo já assinado digitalmente
  * Associada a relatórios legais
* Deve ser possível restaurar futuramente, se o sistema oferecer essa funcionalidade.

---

### Exemplo de Requisição

```http
DELETE /formularios/formulario_abc/respostas/resposta_001
Accept: application/json
```

---

### Resposta – 200 OK

```json
{
  "mensagem": "Resposta 'resposta_001' marcada como inativa com sucesso.",
  "status": "soft_deleted"
}
```

---

### Casos de Erro

####  404 – Resposta não encontrada

```json
{
  "erro": "resposta_nao_encontrada",
  "mensagem": "A resposta 'resposta_001' não foi localizada para o formulário 'formulario_abc'."
}
```

####  410 – Já removida anteriormente

```json
{
  "erro": "resposta_ja_removida",
  "mensagem": "A resposta já está inativa. Nenhuma ação adicional foi realizada."
}
```

####  403 – Formulário inativo

```json
{
  "erro": "formulario_inativo",
  "mensagem": "Este formulário foi desativado e não permite alterações em suas respostas."
}
```

####  423 – Resposta protegida (vinculada a laudo ou bloqueada)

```json
{
  "erro": "resposta_congelada",
  "mensagem": "A resposta está protegida e não pode ser removida devido a políticas de retenção."
}
```

---

### Considerações Técnicas

* A operação de soft delete deve atualizar os seguintes campos:

  * `is_ativo: false`
  * `data_remocao`
  * `usuario_remocao`
* Os logs de alteração devem conter:

  ```json
  {
    "acao": "remocao_logica",
    "entidade": "resposta",
    "id_formulario": "formulario_abc",
    "id_resposta": "resposta_001",
    "usuario": "usuario_admin",
    "data_hora": "2024-03-15T23:59:59Z"
  }
  ```


---
### Regras de Negocio:

### 1. **Criação de formulários dinâmicos**

Cada formulário é composto por **um ou mais campos** definidos em tempo de criação. Esses campos devem ser interpretados dinamicamente com base no seguinte modelo:

####  Tipos de campo suportados:

| Tipo (`tipo`) | Descrição                                                                                 | Exemplo JSON                                        |
| ------------- | ----------------------------------------------------------------------------------------- | --------------------------------------------------- |
| `text`        | Campo de texto livre, pode incluir restrições de tamanho ou expressão regular             | `"tipo": "text"`                                    |
| `number`      | Campo numérico. Deve suportar validações como mínimo, máximo e divisibilidade             | `"tipo": "number"`                                  |
| `boolean`     | Representa uma opção binária (sim/não, verdadeiro/falso)                                  | `"tipo": "boolean"`                                 |
| `select`      | Campo com lista fixa de opções (array de strings ou pares `label`/`value`)                | `"tipo": "select", "opcoes": ["A", "B", "C"]`       |
| `date`        | Campo de data, com validações de intervalo ou comparação com outros campos                | `"tipo": "date"`                                    |
| `calculated`  | Campo cujo valor é **derivado automaticamente** de outros campos, por meio de uma fórmula | `"tipo": "calculated", "formula": "peso / altura²"` |

## 🧾 Campos Explicados

```json
{
  "id": "peso",
  "label": "Peso do paciente",
  "tipo": "number",
  "formato": "decimal",
  "obrigatorio": true,
  "validacoes": [
    { "regra": "minimo", "valor": 0 },
    { "regra": "maximo", "valor": 300 },
    { "regra": "multiplo_de", "valor": 0.1 }
  ],
  "condicional": "idade >= 0 && idade <= 120"
}
```

### Campo `id` (string)

Identificador único do campo no formulário. Ele será usado internamente em fórmulas e regras condicionais.

* Não deve conter espaços, acentos ou caracteres especiais.
* Deve ser único em cada versão de formulário.
* Recomenda-se usar snake\_case (`peso_paciente`, `data_inicio`).

---

### Campo `label` (string)

Nome amigável exibido na interface do usuário.

* Deve ser claro, objetivo e específico.
* Pode conter espaços e acentos.
* Obrigatório para todos os tipos de campo.

---

### Campo `tipo` (string)

Define o tipo de dado. Os valores possíveis são:

* `"text"`: campo alfanumérico
* `"number"`: numérico, inteiro ou decimal
* `"boolean"`: verdadeiro/falso
* `"date"`: data no formato ISO (`YYYY-MM-DD`)
* `"select"`: opções pré-definidas (única ou múltipla)
* `"calculated"`: campo derivado automaticamente

---

## Campo `text` 

Campos do tipo `text` são utilizados para capturar informações alfanuméricas inseridas pelo usuário, como nome, endereço, observações ou descrições livres.

###  Exemplo completo de schema:

```json
{
  "id": "nome_completo",
  "label": "Nome Completo",
  "tipo": "text",
  "obrigatorio": true,
  "capitalizar": true,
  "multilinha": false,
  "condicional": "idade >= 18",
  "validacoes": [
    {
      "tipo": "tamanho_minimo",
      "valor": 5
    },
    {
      "tipo": "tamanho_maximo",
      "valor": 120
    },
    {
      "tipo": "regex",
      "valor": "^[A-Za-zÀ-ú\\s]+$"
    },
    {
      "tipo": "nao_conter",
      "valor": ["admin", "root", "null"]
    },
    {
      "tipo": "nao_vazio"
    }
  ]
}
```

---

###  Campos Fixos

| Propriedade   | Tipo    | Descrição                                                          |
| ------------- | ------- | ------------------------------------------------------------------ |
| `id`          | string  | Identificador único sem espaços, usado internamente e em fórmulas. |
| `label`       | string  | Rótulo exibido ao usuário. Obrigatório.                            |
| `tipo`        | string  | Valor fixo: `"text"`.                                              |
| `obrigatorio` | boolean | Se verdadeiro, exige preenchimento (mesmo que `""`).               |
| `capitalizar` | boolean | Se verdadeiro, o texto deve ser capitalizado automaticamente.      |
| `multilinha`  | boolean | Permite múltiplas linhas (textarea) ao invés de input simples.     |
| `condicional` | string  | Expressão lógica para exibição ou obrigatoriedade dinâmica.        |
| `validacoes`  | array   | Lista de objetos com validações detalhadas, descritas abaixo.      |

---

###  Regras disponíveis no campo `validacoes`

| Tipo de Validação | Valor esperado         | Comportamento                                     |
| ----------------- | ---------------------- | ------------------------------------------------- |
| `tamanho_minimo`  | inteiro ≥ 0            | Quantidade mínima de caracteres.                  |
| `tamanho_maximo`  | inteiro ≥ `min`        | Quantidade máxima de caracteres.                  |
| `regex`           | string (RegExp válida) | Valor deve bater com o padrão informado.          |
| `nao_vazio`       | —                      | Rejeita strings vazias ou apenas com espaços.     |
| `nao_conter`      | array de strings       | Rejeita valores contendo qualquer termo da lista. |

---

### 🚨 Regras de Negócio e Considerações

1. **Capitalização**:

   * Se `capitalizar = true`, o valor enviado será automaticamente transformado em *title case* (ex: "Maria Santos").
   * Isso é feito antes das validações.

2. **Regex inválido**:

   * Se o padrão informado não for compilável, a criação do formulário deverá falhar com erro 422.

3. **Validação de campos obrigatórios**:

   * Campos obrigatórios devem ser preenchidos quando visíveis. Se ocultos por `condicional`, a obrigatoriedade é suspensa.

4. **`nao_conter` com termos sensíveis**:

   * Pode ser usado para impedir submissões com palavras restritas como `"admin"`, `"senha"`, `"proibido"`.

5. **`multilinha` e validações**:

   * Quando `multilinha = true`, o campo aceita quebras de linha e texto mais extenso.

6. **Interação com `condicional`**:

   * A visibilidade do campo deve ser avaliada com base na expressão booleana em `condicional`, podendo ocultar ou desobrigar o campo dinamicamente.

---

### 🧠 Casos adicionais de validação recomendada (não obrigatória)

* **Bloqueio de nomes reservados**:

  * Ex: impedir que campos como `nome_completo` contenham `"root"` ou `"sistema"`.

* **Bloqueio de valores repetidos entre campos**:

  * Ex: `email` e `confirmar_email` não devem ser iguais a outros campos específicos.
  * Isso pode ser tratado via regras do tipo `diferente_de(campo)` (a definir na engine de regras condicionais).

---

##  Campo `number` 

Campos do tipo `number` são utilizados para representar valores quantitativos como idade, peso, temperatura, índice ou qualquer outro dado numérico. Podem ser inteiros ou decimais e aceitam regras matemáticas e restrições de faixa.

---

###  Exemplo completo de schema

```json
{
  "id": "idade",
  "label": "Idade",
  "tipo": "number",
  "formato": "inteiro",
  "obrigatorio": true,
  "condicional": "pais == 'Brasil'",
  "validacoes": [
    {
      "tipo": "minimo",
      "valor": 0
    },
    {
      "tipo": "maximo",
      "valor": 120
    },
    {
      "tipo": "multiplo_de",
      "valor": 1
    },
    {
      "tipo": "nao_nulo"
    }
  ]
}
```

---

###  Campos Fixos

| Propriedade   | Tipo    | Descrição                                                            |
| ------------- | ------- | -------------------------------------------------------------------- |
| `id`          | string  | Identificador único e sem espaços. Usado em fórmulas e dependências. |
| `label`       | string  | Nome amigável exibido ao usuário. Obrigatório.                       |
| `tipo`        | string  | Valor fixo: `"number"`.                                              |
| `formato`     | string  | `"inteiro"` ou `"decimal"`. Controla a precisão permitida.           |
| `obrigatorio` | boolean | Define se o valor precisa ser informado.                             |
| `condicional` | string  | Expressão lógica que controla visibilidade e obrigatoriedade.        |
| `validacoes`  | array   | Conjunto de regras de valor e integridade aplicadas ao campo.        |

---

###  Regras disponíveis no campo `validacoes`

| Tipo de Validação | Valor esperado             | Comportamento                                            |
| ----------------- | -------------------------- | -------------------------------------------------------- |
| `minimo`          | number                     | Valor informado deve ser ≥ ao mínimo.                    |
| `maximo`          | number                     | Valor informado deve ser ≤ ao máximo.                    |
| `multiplo_de`     | number > 0                 | Valor informado deve ser múltiplo exato.                 |
| `formato`         | `"inteiro"` ou `"decimal"` | Aplicado implicitamente com `tipo`.                      |
| `nao_nulo`        | —                          | Valor não pode ser `null` nem indefinido se obrigatório. |

---

### 🚨 Regras de Negócio e Considerações

1. **Tipos de número permitidos**:

   * Se `formato = "inteiro"`, apenas números sem parte decimal são válidos (ex: 23).
   * Se `formato = "decimal"`, o campo aceita frações (ex: 23.5) e pode conter até 10 casas decimais por padrão.

2. **Multiplicidade (`multiplo_de`)**:

   * Exemplo: se `multiplo_de = 0.5`, os valores válidos são 0.0, 0.5, 1.0, 1.5 etc.
   * Devem ser validados com tolerância de erro: `Math.abs(valor % base) < 1e-6`.

3. **Faixa invertida (inconsistência)**:

   * Se `minimo > maximo`, o schema do campo é inválido e deve ser rejeitado na criação.

4. **Valores ausentes**:

   * Se `obrigatorio = true`, o campo deve ser informado explicitamente (mesmo que 0).
   * Se `obrigatorio = false`, o campo pode ser omitido e nenhum cálculo depende dele diretamente.

5. **Validação condicional**:

   * O campo pode estar visível apenas se certas condições forem satisfeitas (ex: `"sexo == 'masculino'"`).
   * Campos invisíveis não devem ser validados, mesmo que obrigatórios.

6. **Limites e extremos**:

   * O backend deve suportar valores no intervalo seguro para `float64` (IEEE 754), evitando estouros ou `Infinity`.
   * Ideal validar com `Number.isFinite()` antes de aplicar regras.

---

### 🧠 Casos adicionais para avaliar criticamente

* **Número negativo onde não faz sentido**:

  * Por exemplo, idade ou quantidade não devem aceitar números negativos. Exigir `minimo >= 0`.

* **Erros sutis com ponto flutuante**:

  * 0.1 + 0.2 != 0.3 → exigir uso de `toFixed` ou funções de precisão no cálculo de dependentes.

* **Validação cruzada (regra futura)**:

  * Poderá ser adicionado um validador do tipo `diferente_de(campoX)` ou `menor_que(campoY)`.

---

###  Submissões com erro devem retornar:

```json
{
  "erro": "campo_invalido",
  "campo": "idade",
  "mensagem": "O valor deve ser um número inteiro entre 0 e 120, múltiplo de 1."
}
```
---

##  Campo `boolean`

Campos do tipo `boolean` representam decisões binárias ou estados lógicos: verdadeiro/falso, sim/não, ativo/inativo, ligado/desligado. São fundamentais em lógicas condicionais e impactam diretamente a visibilidade e a obrigatoriedade de outros campos.

---

###  Exemplo completo de schema

```json
{
  "id": "aceita_termos",
  "label": "Aceita os termos e condições?",
  "tipo": "boolean",
  "obrigatorio": true,
  "condicional": "pais == 'Brasil'",
  "validacoes": [
    {
      "tipo": "nao_nulo"
    },
    {
      "tipo": "valor_esperado",
      "valor": true
    }
  ]
}
```

---

###  Campos Fixos

| Propriedade   | Tipo    | Descrição                                                         |
| ------------- | ------- | ----------------------------------------------------------------- |
| `id`          | string  | Identificador único (sem espaços, usado em lógicas e fórmulas).   |
| `label`       | string  | Nome amigável exibido ao usuário. Obrigatório.                    |
| `tipo`        | string  | Valor fixo: `"boolean"`.                                          |
| `obrigatorio` | boolean | Define se o valor deve obrigatoriamente ser fornecido.            |
| `condicional` | string  | Expressão lógica que controla visibilidade e obrigatoriedade.     |
| `validacoes`  | array   | Regras de valor ou integridade específicas para campos booleanos. |

---

###  Regras disponíveis no campo `validacoes`

| Tipo de Validação      | Valor esperado | Comportamento                                                           |
| ---------------------- | -------------- | ----------------------------------------------------------------------- |
| `nao_nulo`             | —              | Valor deve ser explicitamente `true` ou `false`.                        |
| `valor_esperado`       | `true`/`false` | Força a submissão a ter exatamente esse valor.                          |
| `bloqueado_para_falso` | —              | Caso `false`, bloqueia o envio e exige explicação adicional (avançado). |

---

### ⚙️ Regras de Negócio e Considerações

1. **Obrigatoriedade lógica**:

   * Se `obrigatorio = true`, o valor deve obrigatoriamente estar presente como `true` ou `false`.
   * Valores `null`, `undefined`, strings `"true"` ou `"false"` são **inválidos**.

2. **Tipo estrito**:

   * O valor **deve ser booleano real**. Ex: `true` ou `false`. Nenhum outro tipo é aceito.

3. **Controle de visibilidade com `condicional`**:

   * Exemplo: `"idade >= 18"` → o campo só aparece se a idade for maior ou igual a 18.
   * Campos ocultos **não devem ser validados**, mesmo que `obrigatorio`.

4. **Regras avançadas de coerção de decisão**:

   * `valor_esperado: true` pode ser exigido para aceite explícito (ex: termos de uso).
   * `bloqueado_para_falso` pode ser usado para impedir recusas sem justificativa (ex: "Não aceito").

5. **Influência sobre outros campos**:

   * Campos `boolean` são frequentemente usados em expressões de `condicional` em outros campos.
   * Exemplo: `condicional: "aceita_termos == true"`.

6. **Cuidado com auto-checks no frontend**:

   * A submissão deve ser validada no backend mesmo que o valor venha marcado automaticamente.

---

### 🧠 Situações Críticas a serem validadas

* **Campo obrigatório + condicional**:

  * Deve ser validado **somente se a condição tornar o campo visível**.

* **Submissão com ausência de valor**:

  * Se `obrigatorio = true` e não enviado, retornar erro `"campo_invalido"`.

* **Uso incorreto como string**:

  * `valor = "true"` (string) é inválido. Deve ser `true` (booleano literal).

* **Confusão semântica**:

  * Campos como "Está ativo?" devem ser claros no `label`, pois inversões lógicas podem induzir erro.

---

###  Submissões com erro devem retornar:

```json
{
  "erro": "campo_invalido",
  "campo": "aceita_termos",
  "mensagem": "Necessário aceitar os termos e condições para continuar."
}
```
---

##  Campo `date`

Campos do tipo `date` são usados para capturar datas relevantes, como nascimento, vencimento, inspeção, etc. O formato e a coerência são cruciais, especialmente para sistemas com cálculos, filtros temporais e auditoria.

---

###  Exemplo completo de schema

```json
{
  "id": "data_nascimento",
  "label": "Data de nascimento",
  "tipo": "date",
  "obrigatorio": true,
  "minima": "1900-01-01",
  "maxima": "2030-12-31",
  "condicional": "idade_estimada < 150",
  "validacoes": [
    {
      "tipo": "data_futura",
      "permitido": false
    },
    {
      "tipo": "anterior_a",
      "campo": "data_fim"
    }
  ]
}
```

---

###  Campos Fixos

| Propriedade   | Tipo    | Descrição                                                             |
| ------------- | ------- | --------------------------------------------------------------------- |
| `id`          | string  | Identificador único do campo, sem espaços.                            |
| `label`       | string  | Nome amigável exibido ao usuário. Obrigatório.                        |
| `tipo`        | string  | Valor fixo: `"date"`.                                                 |
| `obrigatorio` | boolean | Se verdadeiro, o campo precisa conter uma data válida.                |
| `minima`      | string  | (opcional) Data mínima permitida, no formato ISO 8601 (`YYYY-MM-DD`). |
| `maxima`      | string  | (opcional) Data máxima permitida, no mesmo formato.                   |
| `condicional` | string  | (opcional) Expressão lógica para controle de visibilidade.            |
| `validacoes`  | array   | Lista de validações adicionais aplicáveis à data.                     |

---

###  Regras disponíveis no campo `validacoes`

| Tipo de Validação     | Parâmetros              | Descrição                                                                        |
| --------------------- | ----------------------- | -------------------------------------------------------------------------------- |
| `data_futura`         | `permitido: true/false` | Define se é permitido informar uma data posterior à data atual.                  |
| `formato_iso_estrito` | —                       | Valida se o valor segue **rigorosamente** o padrão `YYYY-MM-DD`.                 |
| `nao_nulo`            | —                       | Garante que a data seja preenchida caso o campo esteja visível.                  |
| `anterior_a`          | `campo: string`         | Verifica se a data atual é anterior à de outro campo (`data_inicio < data_fim`). |

---

### ⚙️ Regras de Negócio e Considerações

1. **Formato obrigatório ISO 8601**:

   * Apenas `YYYY-MM-DD` é aceito.
   * Formatos como `DD/MM/YYYY`, `YYYY/MM/DD` ou `2024-7-5` são rejeitados.

2. **Validação de faixa (`minima`, `maxima`)**:

   * Se `minima` for definida, a data deve ser ≥ `minima`.
   * Se `maxima` for definida, a data deve ser ≤ `maxima`.
   * Se `minima > maxima`, o schema é inválido e deve ser rejeitado na criação.

3. **Validação cruzada com outro campo (`anterior_a`)**:

   * A data deve ser anterior à data de outro campo.
   * Se o campo de comparação (`campo`) estiver vazio ou for inválido, a validação pode ser adiada até o valor existir.
   * Exemplo comum: `data_inicio < data_fim`.

4. **Regras de obrigatoriedade**:

   * Se `obrigatorio = true`, a ausência do valor causa erro.
   * A visibilidade e obrigatoriedade devem respeitar a expressão `condicional`.

5. **Validação contra data futura**:

   * `data_futura: false` impede datas superiores à atual (ex: nascimento no futuro).
   * Comparações devem usar `UTC` para consistência.

6. **Datas inválidas semanticamente**:

   * `2023-02-30` tem o formato correto, mas é inválida. Deve ser rejeitada com mensagem explícita.

7. **Timezone e precisão**:

   * Qualquer valor com horário (`T00:00:00Z`) é rejeitado.
   * Apenas datas puras são válidas.

---

###  Submissão com erro deve retornar:

```json
{
  "erro": "campo_invalido",
  "campo": "data_nascimento",
  "mensagem": "A data deve ser anterior à data de fim e estar entre 1900-01-01 e 2030-12-31."
}
```

---

##  Campo `select`

O tipo `select` representa escolhas entre **opções predefinidas**, muito comum em formulários para capturar categorias, status, regiões, ou qualquer dado com domínio fechado. Pode ser de seleção **única** ou **múltipla**, e exige especial atenção à coerência dos valores informados.

---

###  Exemplo completo de schema

```json
{
  "id": "estado_civil",
  "label": "Estado civil",
  "tipo": "select",
  "obrigatorio": true,
  "multipla": false,
  "opcoes": [
    { "label": "Solteiro", "value": "solteiro" },
    { "label": "Casado", "value": "casado" },
    { "label": "Divorciado", "value": "divorciado" }
  ],
  "condicional": "idade >= 18",
  "validacoes": [
    {
      "tipo": "valor_na_lista"
    }
  ]
}
```

---

###  Campos Fixos

| Propriedade   | Tipo    | Descrição                                                                  |
| ------------- | ------- | -------------------------------------------------------------------------- |
| `id`          | string  | Identificador único. Sem espaços, usado para lógica condicional e cálculo. |
| `label`       | string  | Nome visível ao usuário. Obrigatório.                                      |
| `tipo`        | string  | Valor fixo: `"select"`.                                                    |
| `multipla`    | boolean | Define se o usuário pode selecionar múltiplos valores.                     |
| `opcoes`      | array   | Lista com objetos `{ label: string, value: string }`. Mínimo: 1 item.      |
| `obrigatorio` | boolean | Se `true`, o campo deve ser respondido.                                    |
| `condicional` | string  | (opcional) Expressão booleana que ativa ou esconde o campo.                |
| `validacoes`  | array   | Lista de regras adicionais a serem verificadas.                            |

---

###  Regras disponíveis no campo `validacoes`

| Tipo de Validação         | Parâmetros         | Descrição                                                                        |
| ------------------------- | ------------------ | -------------------------------------------------------------------------------- |
| `valor_na_lista`          | —                  | Garante que os valores submetidos existam em `opcoes[].value`.                   |
| `quantidade_minima`       | `minimo: number`   | (somente com `multipla: true`) Valida que pelo menos `n` valores sejam marcados. |
| `quantidade_maxima`       | `maximo: number`   | (somente com `multipla: true`) Limita a seleção a no máximo `n` valores.         |
| `obrigatorio_condicional` | `condicao: string` | Força a resposta apenas se a condição for verdadeira. Ex: `sexo == 'feminino'`.  |

---

### ⚙️ Regras de Negócio e Considerações

1. **Formato das opções (`opcoes`)**:

   * Cada item deve conter `label` (texto visível) e `value` (string que será submetida).
   * `value` deve ser uma string sem espaços e **única dentro do campo**.
   * `label` pode conter acentos, espaços e maiúsculas.

2. **Validação na submissão**:

   * `multipla = false`: o valor submetido deve ser uma **string exata** de um dos `value`.
   * `multipla = true`: o valor submetido deve ser um **array de strings**, com valores válidos.
   * Valores não incluídos na lista devem gerar erro imediato.

3. **Múltiplas seleções**:

   * Quando `multipla = true`, o sistema deve validar:

     * Se o array contém **ao menos um** valor, se obrigatório.
     * Se os valores são únicos (sem duplicatas).
     * Se todos estão presentes em `opcoes[]`.

4. **Regras cruzadas com validações adicionais**:

   * Campos podem exigir que, se `sexo == 'feminino'`, ao menos uma das opções do campo "serviços extras" esteja marcada.
   * Ou: permitir apenas valores com prefixo `tipo_` (exemplo de filtro por naming convention nos values).

5. **Tamanho das opções**:

   * O número de opções permitidas no campo deve estar entre 1 e 100.
   * Campos com 0 opções ou listas duplicadas devem ser rejeitados no schema.

6. **Visibilidade condicional**:

   * `condicional: "idade >= 18"` faz com que o campo só seja exibido se a idade for compatível.
   * Campos escondidos não devem ser validados na submissão, mesmo que `obrigatorio = true`.

7. **Consistência na serialização**:

   * Para submissão com `multipla: true`, os valores devem ser um array:
      `["valor1", "valor2"]`
      `"valor1,valor2"` (string concatenada — inválida)

8. **Ordem e agrupamento**:

   * A ordem de exibição deve respeitar a ordem em `opcoes[]`.
   * Agrupamentos lógicos (ex: "Regiões Norte/Nordeste") podem ser indicados via prefixo no label (opcional).

---

###  Submissão com erro deve retornar:

```json
{
  "erro": "valor_invalido",
  "campo": "estado_civil",
  "mensagem": "O valor 'solteirao' não é uma opção válida para este campo."
}
```

Ou, no caso de múltiplas seleções inválidas:

```json
{
  "erro": "valores_invalidos",
  "campo": "interesses",
  "mensagem": "Os valores ['xpto', 'admin'] não estão disponíveis na lista de opções."
}
```

---

###  Casos frequentes de erro:

* Submeter `["sim", "sim"]` com duplicidade (rejeitado).
* Submeter string com `multipla: true` (rejeitado).
* Submeter `value` inexistente por erro de digitação ou schema desatualizado (rejeitado).
* Criar formulário com `opcoes: []` (rejeitado na validação de schema).

---

##  Campo `calculated`

O campo `calculated` é um tipo especial que **não recebe entrada do usuário final**. Seu valor é sempre derivado **a partir de uma expressão lógica, aritmética ou condicional**, e é recalculado automaticamente sempre que qualquer campo do qual ele depende é alterado.

---

###  Exemplo completo de schema

```json
{
  "id": "imc",
  "label": "Índice de Massa Corporal",
  "tipo": "calculated",
  "formula": "peso / (altura/100)^2",
  "dependencias": ["peso", "altura"],
  "precisao": 2
}
```

---

###  Campos Fixos

| Propriedade    | Tipo    | Descrição                                                                |
| -------------- | ------- | ------------------------------------------------------------------------ |
| `id`           | string  | Identificador único do campo. Sem espaços, usado na `formula` e lógica.  |
| `label`        | string  | Nome do campo exibido ao usuário. Obrigatório.                           |
| `tipo`         | string  | Valor fixo: `"calculated"`.                                              |
| `formula`      | string  | Expressão matemática ou lógica. Obrigatória.                             |
| `dependencias` | array   | Lista de `id`s de campos que influenciam o valor calculado. Obrigatório. |
| `precisao`     | integer | (opcional) Número de casas decimais para valores numéricos.              |
| `condicional`  | string  | (opcional) Expressão que define visibilidade do campo.                   |

---

###  Regras disponíveis no campo `validacoes`

Geralmente, campos `calculated` **não recebem validações diretas** (como `obrigatorio`, regex, etc.), mas o sistema pode permitir validações de consistência como:

| Tipo de Validação     | Parâmetros    | Descrição                                                         |
| --------------------- | ------------- | ----------------------------------------------------------------- |
| `valor_na_lista`      | `valores: []` | O resultado da fórmula deve estar contido na lista fornecida.     |
| `igual_a`             | `valor: any`  | O resultado deve ser exatamente igual ao valor indicado.          |
| `intervalo_valido`    | `min`, `max`  | O resultado deve estar entre os valores definidos.                |
| `formato_data_valida` | —             | Se o valor for uma data, deve estar em ISO e ser uma data válida. |

---

### ⚙️ Regras de Negócio e Considerações

1. **Valores sempre são readonly**:

   * Nunca devem ser enviados pelo usuário.
   * Se enviados, são ignorados silenciosamente.

2. **Sintaxe da fórmula**:

   * Deve conter apenas variáveis que existam em `dependencias`.

   * Funções suportadas incluem:

     ```plaintext
     if(condicao, valor_se_verdadeiro, valor_se_falso)
     min(a, b, ...)
     max(a, b, ...)
     abs(x)
     sqrt(x)
     log(x)
     ceil(x)
     floor(x)
     round(x, precisao)
     ```

   * Operações permitidas: `+`, `-`, `*`, `/`, `^`, `==`, `!=`, `>`, `<`, `>=`, `<=`, `&&`, `||`.

3. **Campos `calculated` podem depender de outros `calculated`**:

   * A única restrição é que **não pode haver dependência cíclica**.

     * Exemplo válido: `A → B → C` (C depende de B, que depende de A).
     * Exemplo inválido: `A → B → A` (ciclo entre A e B).

   * A engine deve realizar detecção de ciclos no momento de montar o schema e rejeitar esquemas inválidos.

4. **Ordem de avaliação**:

   * O sistema deve montar um **grafo acíclico direcionado** com os nós `calculated`, e avaliar na ordem correta (topological sort).

5. **Tipo de resultado**:

   * Pode ser **número**, **string** ou **boolean**, dependendo da lógica da `formula`.
   * O campo deve ser interpretado como string se a `formula` retorna `if(...)` com textos.
   * Se o resultado for numérico, `precisao` deve ser aplicada.

6. **Casos comuns de erro de avaliação**:

   * Referência a campo inexistente.
   * Divisão por zero.
   * Resultado `NaN` ou `undefined`.
   * Resultado inválido para o tipo de dado esperado (ex: `"abc" * 2`).

7. **Precauções adicionais**:

   * Não é permitido modificar diretamente o valor do campo.
   * Caso a `formula` não possa ser avaliada por erro sintático ou semântico, o sistema deve mostrar erro claro em tela e rejeitar o schema no cadastro.

---

###  Submissão incorreta com campo `calculated`

Submissão onde o usuário tenta alterar um campo calculado:

```json
{
  "imc": 30.1
}
```

Resposta esperada:

```json
{
  "erro": "campo_reservado",
  "campo": "imc",
  "mensagem": "O campo 'imc' é calculado automaticamente e não pode ser enviado manualmente."
}
```

---

###  Casos frequentes de erro

* Campo `dependencias` referenciando um campo que não existe.
* Campo `formula` com erro de sintaxe (`if idade > 18 então 'maior'` — inválido).
* Campo calculado `A` depende de campo `B`, que depende de `A`.
* Falta de `precisao` para campos numéricos com casas decimais, gerando arredondamentos inesperados.

---

## 🔀 Validações Transversais e Condicionais

Além das regras específicas por tipo de campo, o sistema de formulários inteligentes deve aplicar **validações contextuais** e **regras condicionais** que impactam:

* A visibilidade dos campos
* A obrigatoriedade condicional
* A reavaliação de fórmulas e dependências
* A integridade lógica de múltiplos campos em conjunto

---

###  Propriedade `condicional`

Todos os campos (inclusive `calculated`) podem possuir a propriedade `condicional`, usada para definir:

* Se o campo **deve aparecer** ou não no formulário
* Se ele **deve ser obrigatório** sob certas condições
* Se o seu valor deve ser **ignorado ou preservado** ao ser ocultado

```json
{
  "id": "nome_mae",
  "label": "Nome da mãe",
  "tipo": "text",
  "obrigatorio": true,
  "condicional": "tipo_registro == 'nascimento'"
}
```

Neste exemplo, o campo só será exibido e exigido se o valor de `tipo_registro` for `"nascimento"`.

---

###  Sintaxe da expressão booleana (`condicional`)

A mini-linguagem lógica aceita os seguintes operadores:

| Operador        | Descrição                       | Exemplo                  |                      |                                      |
| --------------- | ------------------------------- | ------------------------ | -------------------- | ------------------------------------ |
| `==` / `!=`     | Igualdade / diferença           | `sexo == 'feminino'`     |                      |                                      |
| `>` / `<`       | Maior / menor                   | `idade > 18`             |                      |                                      |
| `>=` / `<=`     | Maior ou igual / menor ou igual | `peso <= 120`            |                      |                                      |
| `&&` / \`       |                                 | \`                       | E lógico / OU lógico | `sexo == 'masculino' && idade >= 60` |
| `!`             | Negação                         | `!(ativo)`               |                      |                                      |
| `in` / `not in` | Inclusão em lista               | `estado in ['SP', 'RJ']` |                      |                                      |

**Validação de `condicional`:**

* Referência a campos inexistentes deve gerar erro de schema.
* A linguagem não permite acesso a campos `calculated` que ainda não foram avaliados (ordem importa).
* Expressões inválidas devem gerar erro de parsing.

---

### 🔄 Regras cruzadas entre múltiplos campos

É possível validar valores com **dependência entre dois ou mais campos**. Isso pode ser feito de duas formas:

#### 1. Validação via campo `validacoes` do tipo `comparacao_cruzada`:

```json
"validacoes": [
  {
    "tipo": "comparacao_cruzada",
    "campo_comparado": "peso",
    "operador": ">",
    "mensagem": "A altura deve ser maior que o peso em metros"
  }
]
```

* O campo atual será comparado com `campo_comparado`.
* Operadores válidos: `==`, `!=`, `>`, `<`, `>=`, `<=`.

#### 2. Campo `calculated` com `if(...)` embutido

Possível criar um campo oculto que detecta a inconsistência e usa o valor para gerar alertas, rejeições ou diagnósticos.

---

### 🕵️‍♀️ Rastreabilidade das Condições Avaliadas

* Cada execução de submissão deve registrar:

  * Quais campos foram exibidos ou ocultos
  * Quais campos foram ignorados por estarem invisíveis
  * Quais regras condicionais foram avaliadas como `true` ou `false`

---

###  Tratamento de campos invisíveis

* Campos ocultos por `condicional`:

  * Não devem ser enviados pelo frontend
  * Se enviados, os valores devem ser ignorados
  * Validações como `obrigatorio` devem ser **ignoradas**

---

###  Exemplo de condição com `select` múltipla:

```json
{
  "id": "beneficios",
  "tipo": "select",
  "multipla": true,
  "opcoes": [
    { "label": "Vale Refeição", "value": "vr" },
    { "label": "Vale Transporte", "value": "vt" }
  ]
}
```

Condição válida:

```json
"condicional": "'vr' in beneficios"
```

---

### 📦 Casos críticos que devem ser validados

| Situação                                                   | Esperado                                      |
| ---------------------------------------------------------- | --------------------------------------------- |
| Campo depende de outro ainda não avaliado                  | Deve aguardar a avaliação do campo anterior.  |
| Campo oculto com valor enviado pelo usuário                | Ignorar valor.                                |
| Campo marcado como `obrigatorio`, mas oculto pela condição | Regra de obrigatoriedade é ignorada.          |
| Expressão com erro de sintaxe (`if idade > 18`)            | Deve gerar erro de schema na criação.         |
| Campo depende de `calculated` com ciclo                    | Deve ser rejeitado como dependência circular. |

---

>  Dica: campos `calculated` também podem participar de validações indiretas — se forem usados como fonte de dependência para outro campo com regras severas.

---
##  Entregáveis

- `README.md`: instruções de execução
- `ANALISE.md`: análise e justificativas arquiteturais
- `docs/`: diagrama de entidades e engine reativa e sequencia (UML/Mermaid)
- Dump com pelo menos 2 formulários, incluindo campos dependentes

---

##  Critérios de Avaliação

| Critério                               | Peso |
|----------------------------------------|------|
| Clareza de estrutura e modularidade    | 20%  |
| Correção e execução da engine reativa  | 20%  |
| Estratégia de fallback e rollback      | 15%  |
| Justificativas e ADRs claras           | 15%  |
| Testes e cobertura                      | 10%  |
| Cálculo de indicadores derivados       | 10%  |
| Diagnóstico de inconsistência e estado | 10%  |

---

## 📦 Stack Tecnológica Recomendada

Para garantir consistência na avaliação e facilitar a análise do código, recomendamos o uso das seguintes tecnologias:

**Linguagem e Runtime**
- **TypeScript + Node.js** (preferencial) — Type safety e desenvolvimento mais robusto
- **Java** — Spring Boot para aplicações enterprise robustas

**Banco de Dados**
- **PostgreSQL** (preferencial para produção) ou **SQLite** (aceitável para simplicidade)

**Engine de Cálculo**
- **JavaScript:** mathjs, expr-eval ou similar para avaliação de expressões
- **Python:** SymPy, NumExpr ou implementação customizada
- **Java:** Expression4J, JEXL ou Apache Commons JEXL

**Framework Web**
- **Node.js:** Express.js, Fastify, NestJS ou Koa.js
- **Python:** FastAPI, Django REST Framework ou Flask
- **Java:** Spring Boot, Spring WebFlux ou Quarkus

> **Nota:** Outras tecnologias podem ser utilizadas desde que **justificada a escolha** no ANALISE.md e mantida a qualidade e funcionalidades esperadas.


---

## 🧠 O que Avaliaremos Além do Código

- Clareza do raciocínio e das decisões técnicas
- Capacidade de lidar com lógica encadeada e reativa
- Autonomia para estruturar uma solução bem fundamentada
- Capacidade de comunicar escolhas de arquitetura de forma madura
- Atenção aos detalhes e à consistência do comportamento da engine

---


## ❗ Sobre Plágio e Originalidade

O desafio técnico avalia a capacidade real de resolução de problemas.  
Permitido pesquisar, consultar bibliotecas ou documentação oficial, porém:

- Evitar usar código não compreendido
- Não envie soluções geradas integralmente por ferramentas automáticas sem contextualização
- Valorizada a capacidade de **pensar, decidir e justificar** — mais importante que apenas "funcionar"

---

## 🧠 Enriquecimento Técnico (Padrões e Boas Práticas)

| Item                         | Ação Recomendável                        | Objetivo                                                                 |
|-----------------------------|------------------------------------------|--------------------------------------------------------------------------|
| Validação de ciclos         | Detectar loops como: A depende de B que depende de A | Testar robustez da modelagem e integridade do grafo                     |
| Inversão de controle no parser | Separar construção do AST da execução    | Estimula uso de padrões como Interpreter ou Visitor                      |
| Plugins de validação        | Permitir extensão com validadores customizados | Forçar uso de Strategy / Decorators e princípios de Open/Closed          |

👉 Referência: [Inversão de Controle – Fowler](https://martinfowler.com/bliki/InversionOfControl.html)  
👉 Strategy Pattern: [Refactoring Guru – Strategy](https://refactoring.guru/design-patterns/strategy)  
👉 Decorator Pattern: [Refactoring Guru – Decorator](https://refactoring.guru/design-patterns/decorator)

---

## 📦 Como Enviar Sua Entrega

Para padronizarmos o recebimento e garantir que nada se perca no processo, siga as instruções abaixo:

### 1. **Compactação do Projeto**
Compacte seu projeto em um arquivo `.zip` contendo todo o código-fonte, incluindo o README.md.

### 2. **Nomeação do Arquivo**
Nomear o arquivo com o nome completo (exemplo: `nome_sobrenome_desafio_pleno.zip`).

### 3. **Preparação do E-mail**

**Assunto:** Use o seguinte título padrão:
```
[Entrega Desafio Técnico] Nome Completo – Desenvolvedor(a) Pleno
```
Exemplo: `[Entrega Desafio Técnico] Nome Sobrenome – Desenvolvedor Pleno`

**Corpo do E-mail:**
- Incluir nome completo
- Adicionar, opcionalmente, um breve comentário sobre o envio

### 4. **Opções de Entrega**
Escolha uma das seguintes opções:
- **Anexo:** Anexe o arquivo `.zip` ao e-mail, ou
- **Google Drive:** Compartilhe o link da pasta do Google Drive com permissão de visualização, ou  
- **GitHub:** Envie o link do repositório público no GitHub

**Destinatário:** `igor.conde@sistemafiepe.org.br`

---

### Dúvidas e Suporte

**Tem alguma dúvida sobre o desafio?** 

Disponível um **FAQ** com as perguntas mais comuns durante a implementação, incluindo orientações sobre prazos, ambiente de teste, patterns e diagramas.

** Consulte primeiro:** as perguntas frequentes sobre o projeto


**Boa sorte na implementação!**