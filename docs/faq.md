
# ❓ Perguntas Frequentes sobre o Desafio

**Sabemos que este é um desafio complexo e que dúvidas podem surgir durante o desenvolvimento.** Este FAQ foi criado com carinho para ajudar você a ter clareza sobre os pontos mais importantes e se sentir confiante durante sua implementação.

---

## 🔄 **Posso usar qualquer linguagem de programação?**

**Claro que sim!** Entendemos que cada desenvolvedor tem suas forças e preferências tecnológicas. Você pode usar **qualquer linguagem** com a qual se sinta mais confortável e produtivo.

**O que pedimos:**
- Instruções claras de como executar seu projeto (README bem detalhado)
- Código bem documentado para facilitar nossa avaliação
- Justificativa da escolha tecnológica no ANALISE.md

**Nossa recomendação:** TypeScript/Node.js, Java ou Python são ótimas opções, mas a decisão é totalmente sua!

---

## 🧱 **Como devo estruturar e organizar meu projeto?**

 Você tem **liberdade completa** para organizar seu projeto da maneira que fizer mais sentido para sua solução. Como desenvolvedor pleno, confiamos na sua capacidade de tomar decisões arquiteturais sólidas e bem fundamentadas.

**O que importa para nós:**
- Que sua estrutura seja **lógica e consistente**
- Que você **explique suas escolhas** no README.md ou ANALISE.md
- Que facilite a manutenção e evolução do código

**Lembre-se:** Não existe estrutura "certa" ou "errada" - existe a estrutura que melhor atende aos requisitos do seu projeto!

---

## 🧪 **Posso usar mocks nos testes?**

**Sim, e isso demonstra maturidade técnica!** Sabemos que testes bem estruturados são fundamentais em sistemas críticos.

**Nossas recomendações:**
- **Use mocks livremente** para dependências externas (banco, APIs, etc.)
- **Para a engine de cálculo**, priorize testes reais sempre que possível - queremos ver como ela se comporta com dados reais
- **Testes de integração** com mocks são perfeitamente aceitáveis e bem-vindos

---

## 📊 **É obrigatório criar diagramas de arquitetura?**

**Não é obrigatório, mas é altamente recomendado!** Entendemos que diagramas levam tempo, mas um **diagrama de arquitetura** é uma excelente forma de **comunicar seu pensamento sistêmico** e as decisões que tomou.

**O que recomendamos criar:**
- **Diagrama de arquitetura geral** mostrando componentes principais e suas interações
- **Fluxo da engine de cálculo** - como os campos são processados e dependências resolvidas

**Formatos aceitos:**
- **Mermaid** - Fácil de criar e versionar junto com o código
- **C4 Model** - Excelente para mostrar diferentes níveis de abstração
- **UML** - Diagramas de componentes ou sequência
- **Ferramentas visuais** - Draw.io, Lucidchart, Miro

**Por que recomendamos:**
- Facilita nossa compreensão da sua solução arquitetural
- Demonstra capacidade de comunicação técnica (essencial para nível pleno)
- Ajuda você mesmo a organizar as ideias

**Alternativas flexíveis:**
- Um diagrama simples no README
- Diagramas em ferramentas online (Draw.io, Miro)
- Até mesmo um sketch fotografado serve!

**Lembre-se:** O importante é comunicar sua visão, não a ferramenta usada.

## 📩 **Como será o processo de avaliação após a entrega?**

**Nosso processo tem duas etapas que se complementam:**

### **1ª Etapa - Análise Técnica**
Nossa equipe técnica irá **analisar todas as entregas** focando especialmente nas **soluções mais aderentes às regras de negócio** e que demonstrem melhor compreensão dos desafios propostos.

### **2ª Etapa - Conversa Técnica**
Para os candidatos selecionados na primeira etapa, faremos uma **conversa técnica descontraída** com dois objetivos principais:
- **Conhecer você melhor** como profissional e pessoa
- **Conversar sobre seu projeto** e suas implementações

**O que conversaremos:**
- **Suas decisões arquiteturais** - por que escolheu essa abordagem?
- **Como você implementou** as regras de negócio mais complexas?
- **Desafios encontrados** - como resolveu os problemas que surgiram?
- **Seu processo de trabalho** - como você aborda problemas técnicos?
- **Melhorias futuras** - o que faria diferente com mais tempo?

**Nossa filosofia:** Esta **entrevista técnica** é uma conversa genuína entre profissionais. Queremos conhecer seu raciocínio, experiências e forma de trabalhar, enquanto você também pode conhecer melhor nossa equipe, cultura técnica e ambiente de trabalho.

---

## 🕒 **Quanto tempo tenho para desenvolver a solução?**

O prazo será informado no momento do envio do desafio, e foi pensado para permitir que você desenvolva uma solução sólida sem pressa excessiva.

**Nossa recomendação:**
- **Planeje seu tempo** - dedique tempo adequado para análise, implementação e documentação
- **Priorize qualidade sobre quantidade** - é melhor menos funcionalidades bem implementadas
- **Reserve tempo para testes** - eles são fundamentais na avaliação

---

## 📅 **Posso entregar antes do prazo final?**

Se você terminar antes do prazo, pode enviar sua solução a qualquer momento. Não há vantagem ou desvantagem em entregar antes ou no prazo final.

**O que importa para nós:**
- **Qualidade da solução** entregue
- **Completude da documentação**
- **Funcionamento correto** do sistema


---

## ⏰ **O que fazer se não conseguir implementar todos os requisitos no prazo?**

É melhor entregar uma solução **parcial mas bem feita** do que não entregar nada ou entregar algo mal implementado.

**Nossa estratégia recomendada:**
1. **Priorize os requisitos core** - engine de cálculo funcional é essencial
2. **Documente o que fez** e o que não conseguiu implementar
3. **Explique suas escolhas** no ANALISE.md - por que priorizou certas funcionalidades?
4. **Liste próximos passos** - como completaria a solução com mais tempo?

**Lembre-se:** Valorizamos **honestidade e maturidade técnica**. Saber priorizar e comunicar limitações é uma competência importante de um desenvolvedor pleno.

---

## 🖥️ **Em que ambiente vocês vão testar minha solução?**

**Testamos em ambiente limpo similar ao de produção** para garantir que sua solução funciona fora do seu ambiente de desenvolvimento.

**Ambiente de teste típico:**
- **Sistema operacional:** Linux (Ubuntu/CentOS) ou macOS
- **Docker:** Se você fornecer docker-compose, usaremos ele
- **Dependências:** Apenas as que você documentar no README

**Por isso é crucial:**
- **README detalhado** com instruções de instalação
- **Listar todas as dependências** necessárias
- **Testar em ambiente limpo** antes de entregar


---

## 📊 **Preciso fornecer dados de exemplo/seed?**

**Sim, e isso será um grande diferencial!** Dados de exemplo facilitam muito nossa avaliação e demonstram que você pensou na experiência de quem vai testar sua solução.

**O que recomendamos incluir:**
- **Formulários de exemplo** que demonstrem diferentes funcionalidades
- **Scripts de seed** para popular o banco com dados iniciais
- **Cenários de teste** documentados para mostrar como usar sua solução
- **Dados que explorem casos complexos** - formulários com dependências, validações, etc.

**Formatos aceitos:**
- Scripts SQL ou de migração
- Arquivos JSON/YAML com dados
- Comando específico no README para carregar dados

**Lembre-se:** Facilite nossa vida - quanto mais simples for testar sua solução, melhor será nossa experiência avaliando ela!

---

## 📋 **Como devo documentar as dependências do projeto?**

**Documentação clara de dependências é essencial!** Queremos conseguir rodar sua solução sem adivinhar o que precisa ser instalado.

**Dependências de sistema:**
- **Versões específicas** de Node.js, Python, Java, etc.
- **Banco de dados** e versão necessária
- **Ferramentas adicionais** (Redis, etc.)

**Dependências do projeto:**
- **package.json, requirements.txt, pom.xml** bem configurados
- **Lock files** incluídos (package-lock.json, yarn.lock, etc.)

**Documentação no README:**
```markdown
## Pré-requisitos
- Node.js 18+ 
- PostgreSQL 14+
- Docker (opcional)

## Instalação
1. npm install
2. cp .env.example .env
3. npm run migration
4. npm run seed
```

---

## 🎨 **Quais Design Patterns devo usar no projeto?**

**A escolha dos patterns é sua!** Como desenvolvedor pleno, esperamos que você **analise o problema** e **escolha os patterns** que melhor atendem aos requisitos específicos do seu projeto.

**Nossa abordagem:**
- **Não prescrevemos patterns específicos** - queremos ver seu raciocínio arquitetural
- **Foque na adequação ao problema** - use patterns que realmente agregam valor
- **Justifique suas escolhas** no ANALISE.md - por que escolheu cada pattern?

**O que valorizamos:**
- **Aplicação consciente** - patterns usados no contexto certo
- **Não over-engineering** - evite patterns desnecessários para parecer sofisticado
- **Justificativa clara** - explique o problema que cada pattern resolve
- **Trade-offs documentados** - o que você ganhou e perdeu com cada escolha

**Dica:** É melhor usar **2-3 patterns bem aplicados** com justificativas sólidas do que usar muitos patterns sem necessidade real.

**Lembre-se:** Não existe conjunto "certo" de patterns para este desafio - existe o conjunto que **melhor atende à sua solução específica**.

---

## 💭 **Ainda tem dúvidas?**

**É completamente normal!** Este é um desafio que simula problemas reais e complexos.

**Como podemos ajudar:**
📧 **E-mail:** igor.conde@sistemafiepe.org.br
💡 **Dica:** Seja específico em sua dúvida para um retorno mais preciso

**Lembre-se:** Estamos aqui para que você tenha sucesso. Não hesite em perguntar!
