### **Organização e Governança na Nuvem com Tags Hierárquicas**

Fala galera! 

Você já tentou descobrir a quem pertence um recurso, quanto ele está gastando, ou encontrar informações que não estão tão óbvias assim? Pois é, sem uma organização clara, essa tarefa vira um verdadeiro pesadelo. É aí que entra o poder das tags: simples, mas essenciais para trazer clareza e controle à sua operação. 😉

Quando comecei a estruturar minhas tags, o objetivo era simples: evitar dores de cabeça, principalmente na hora de rastrear custos e entender quem ou o que estava utilizando determinado recurso. 

Hoje vou compartilhar como eu penso e implemento um sistema de tags na minha infraestrutura de nuvem.

---

### **Por que um Sistema de Tags?**
Se a infraestrutura de nuvem fosse uma cidade, as tags seriam como placas de rua. Elas ajudam a organizar o caos e garantem que você sabe exatamente onde está tudo — e quem é responsável por cada pedacinho. Sem elas, encontrar um recurso é como procurar uma agulha no palheiro.

Mas não basta sair criando tags aleatórias. Elas precisam ter um propósito claro. Afinal, cada tag é uma peça de um quebra-cabeça maior, que vai responder perguntas importantes sobre sua operação.

Minha estrutura de tags é dividida em várias camadas, cada uma projetada para responder a perguntas específicas. Vamos ver como isso funciona na prática?

---

#### **1. Nível Organizacional**
O objetivo aqui é entender quais unidades de negócios estão utilizando recursos e quem é responsável por eles. Isso ajuda a manter a gestão financeira alinhada com as prioridades estratégicas da empresa.

- **BusinessUnit**: Nome da unidade de negócios responsável. Exemplo: `minha-empresa` ou `minha-unidade-negocio`. Ajuda a identificar o impacto financeiro e a responsabilidade de cada unidade.

##### **Perguntas que essas tags respondem:**
- Quem está utilizando mais recursos?
- Qual o impacto financeiro por unidade de negócios?

---

#### **2. Nível Operacional**
Essa camada garante que você saiba onde seus recursos estão e em qual ambiente eles estão rodando.

- **Environment**: Define o ambiente (`prd`, `stg`, `dev`). Determina o contexto operacional do recurso.  
- **Region**: Indica a região geográfica (`us-east-1`, `sa-east-1`). Ajuda a localizar fisicamente os recursos.

##### **Perguntas que essas tags respondem:**
- O recurso está em produção ou desenvolvimento?
- Quais regiões estão consumindo mais recursos?

---

#### **3. Nível Financeiro**
Essas tags são indispensáveis para controlar os custos e garantir que cada time ou projeto saiba exatamente o que está gastando. Aqui estão as tags que utilizo:

- **CostCenter**: Associa recursos a centros de custo específicos. Normalmente, uso valores como `infrastructure` ou `marketing`. Especifica claramente a origem dos gastos.  
- **CostAllocation**: Identifica se os custos são compartilhados ou alocados diretamente. Preencho com valores como `shared` ou `directly`. Facilita a divisão de custos entre times.  
- **CostSplitBasis**: Define a base para o rateio de custos de recursos compartilhados, especificando qual tag será usada para calcular o rateio proporcional. Por exemplo, se uma VPC for compartilhada, o custo pode ser dividido proporcionalmente com base na tag **Application**, atribuindo valores às respectivas aplicações.

##### **Perguntas que essas tags respondem:**
- Como os custos estão sendo distribuídos?
- Quem paga a conta?
- Qual a lógica utilizada para rateio de recursos compartilhados?

---

#### **4. Camadas de Aplicação e Infraestrutura**
Aqui entra a granularidade para gerenciar projetos e equipes específicas.

- **Project**: Nome do projeto (`migration-project`). Facilita o rastreamento de iniciativas específicas.  
- **Team**: Time responsável (`team-infra`). Define a equipe diretamente ligada ao recurso.  
- **EscalationContact**: Contato para incidentes (`soc-level-1`). Garante uma resposta rápida em caso de problemas.  
- **Application**: Nome da aplicação (`ecommerce-platform`). Identifica o sistema associado ao recurso.  
- **Lifecycle**: Fase do recurso (`active`, `decommissioned`). Determina a etapa atual do recurso.  
- **Criticality**: Criticidade do recurso (`high`, `medium`, `low`). Ajuda a priorizar a gestão.  
- **Owner**: Responsável direto pelo recurso (`caio-marcatti`). Define a responsabilidade individual ou de time.  
- **ResourceGroup**: Agrupamento lógico de recursos (`frontend`, `backend`). Organiza recursos com um propósito comum.  
- **Product**: Produto associado ao recurso (`ecommerce`, `crm`). Ajuda a rastrear o impacto no portfólio.

##### **Perguntas que essas tags respondem:**
- Quem é responsável por cada recurso?
- Quais projetos estão consumindo mais recursos?

Embora as tags **Project** e **Product** sejam úteis para rastrear recursos dedicados a iniciativas específicas, **não devem ser usadas em recursos compartilhados**. Isso evita associações incorretas e potenciais problemas de governança financeira.

---

#### **5. Camada de Dados**
Essa camada foca na governança, conformidade e segurança dos dados.

- **DataType**: Tipo de dado (`personal`, `sensitive`). Especifica a natureza dos dados armazenados.  
- **Compliance**: Regulamentações aplicáveis (`lgpd`, `gdpr`). Identifica os padrões legais aplicáveis.  
- **DataOwnership**: Responsável pelos dados (`customer-12345`). Define o proprietário direto dos dados.  
- **DataConfidentiality**: Confidencialidade dos dados (`restricted`, `public`). Avalia os níveis de segurança necessários.  
- **DataRetention**: Período de retenção (`short-term`, `long-term`). Define o tempo de armazenamento permitido.  
- **DataLifecycle**: Fase do ciclo de vida dos dados (`active`, `archived`). Determina o status atual do conjunto de dados.

##### **Perguntas que essas tags respondem:**
- Quais dados são críticos e precisam de maior proteção?
- Os dados atendem às regulamentações necessárias?

---

### **Tantas Tags Assim? Por Quê?**
Eu sei, parece um monte de tags, né? Dá até pra se perder! Mas cada conjunto de tags atende a um contexto específico. Poderia separar tudo isso em três artigos diferentes, mas aí pensei: "Ah, melhor entregar o pacote completo de uma vez!" Afinal, por mais que a gente ame (ou odeie) tags, elas são essenciais pra uma infraestrutura bem organizada.

Para facilitar a compreensão, incluí uma visualização que detalha a arquitetura completa das tags. Isso torna mais claro como as diferentes camadas se conectam e interagem.

![Arquitetura de Tags](../tag-architecture.svg)

---

### **Aprendizados e Reflexões**

Implementar esse sistema me trouxe uma clareza enorme sobre como os recursos estão sendo usados. A grande lição é que a revisão periódica das tags é fundamental, porque a infraestrutura está sempre evoluindo.

Outro ponto importante: não dá pra fazer isso sozinho. Envolver DevOps, FinOps e Negócios é essencial pra garantir que todo mundo esteja alinhado.

---

E Você? Agora quero saber: como você organiza seus recursos na nuvem? Tá usando tags? Se não, o que tá te segurando? Bora trocar ideias nos comentários e, quem sabe, criar juntos um sistema ainda melhor! 🚀

Me conta aí! 😊