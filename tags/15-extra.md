### **Extra: Como eu penso e implemento**

Eu sempre busco implementar um sistema de tags hierárquico em minha infraestrutura de nuvem. Este sistema é pensado para facilitar a gestão, rastreabilidade e governança dos recursos, com base em uma estrutura lógica e organizada. Abaixo, explico as camadas e as perguntas que essas tags ajudam a responder.

---

### **Nível Organizacional**

No nível organizacional, utilizo tags para categorizar recursos de acordo com as unidades de negócios e responsabilidades organizacionais. Com essas tags, posso responder perguntas como:

- Quais unidades de negócios estão utilizando recursos?
- Quem é responsável pelos custos associados a cada unidade?

As tags que uso neste contexto incluem:

- **BusinessUnit** - Nome ou abreviação da unidade de negócios responsável pelo recurso. Essa tag é utilizada pelas equipes de FinOps e Gestão de Negócios. Normalmente, preencho com valores como `minha-empresa` ou `minha-unidade-negocio`.

---

### **Nível Operacional**

No nível operacional, as tags ajudam a identificar onde e como os recursos estão sendo utilizados. Essas tags respondem perguntas como:

- Quais recursos estão em produção, desenvolvimento ou homologação?
- Em quais regiões geográficas os recursos estão localizados?

As tags que uso são:

- **Environment** - Define o ambiente operacional onde o recurso está implantado. Utilizo valores como `prd` (produção), `stg` (homologação) e `dev` (desenvolvimento). Essa tag é essencial para as equipes de DevOps e SRE.

- **Region** - Indica a região geográfica onde o recurso está localizado. Costumo usar valores como `us-east-1` ou `sa-east-1`. Essa tag é amplamente utilizada pelas equipes de Infraestrutura e DevOps.

---

### **Nível Financeiro**

As tags financeiras são indispensáveis para rastrear custos e garantir uma divisão clara das despesas. Elas ajudam a responder perguntas como:

- Quais são os custos associados a cada centro de custo?
- Como os custos estão sendo divididos entre equipes ou projetos?

As principais tags que aplico são:

- **CostCenter** - Associa recursos a centros de custo específicos. Normalmente uso valores como `infrastructure` ou `marketing`. Essa tag é amplamente utilizada por FinOps.

- **CostAllocation** - Identifica se os custos são compartilhados ou alocados diretamente. Preencho com valores como `shared` ou `directly`.

- **CostSplitBasis** - Define a base para o rateio de custos de recursos compartilhados, especificando qual tag será usada para calcular o rateio proporcional. Por exemplo, se uma VPC for compartilhada, o custo pode ser dividido proporcionalmente com base na tag Application, atribuindo valores às respectivas aplicações.

---

### **Camadas de Aplicação**

Essas tags fornecem granularidade adicional para gerenciar recursos específicos de projetos e equipes. Elas respondem perguntas como:

- Quais projetos estão utilizando mais recursos?
- Quem é o responsável direto por cada recurso?
- Quais recursos são críticos para operações específicas?

As tags que uso incluem:

- **Project** - Nome ou identificador do projeto específico. Utilizo valores como `MigrationProject` ou `AI-Initiative`. Essa tag é útil para identificar custos e esforços associados a projetos específicos.

- **Team** - Indica o time responsável direto pelo recurso. Costumo preencher com valores como `Team-Infra`. Isso ajuda a organizar responsabilidades dentro da organização.

- **EscalationContact** - Fornece o contato de referência para incidentes relacionados ao recurso, como `SOC-Level-1` ou `Team-DevOps`. Essa tag é essencial para equipes de suporte e resposta a incidentes.

- **Application** - Nome da aplicação associada ao recurso. Geralmente uso valores como `EcommercePlatform`. Essa tag é valiosa para identificar aplicações críticas.

- **Lifecycle** - Define a fase do ciclo de vida do recurso, como `Active` ou `Decommissioned`. Essa tag auxilia no planejamento de desativação de recursos.

- **Criticality** - Determina o nível de criticidade do recurso. Preencho com valores como `High`, `Medium` ou `Low`. Isso ajuda a priorizar recursos em situações de crise.

- **Owner** - Nome do responsável direto pelo recurso. Geralmente, preencho com o nome do colaborador ou time, como `caio-marcatti`.

- **ResourceGroup** - Agrupa recursos relacionados que servem a um propósito comum. Utilizo valores como `Frontend` ou `Backend`. Isso facilita a organização e a gestão de recursos.

- **Product** - Nome ou identificador do produto associado ao recurso. Utilizo valores como `Ecommerce` ou `CRM`. Essa tag ajuda a rastrear investimentos em produtos específicos.


Nota: a tag `Project` e `Product` não deve ser usada em recursos compartilhados para evitar associações erradas. 

---

### **Camada de Infraestrutura**

Na camada de infraestrutura, as tags ajudam a organizar recursos físicos ou virtuais de suporte à aplicação. Com essas tags, posso responder perguntas como:

- Quais times são responsáveis por quais componentes da infraestrutura?
- Como os recursos de infraestrutura estão organizados por criticidade e ciclo de vida?

As tags que uso incluem:

- **Project** - Nome ou identificador do projeto específico. Utilizo valores como `MigrationProject` ou `AI-Initiative`. Essa tag é útil para identificar custos e esforços associados a projetos específicos.

- **Team** - Indica o time responsável direto pelo recurso. Costumo preencher com valores como `Team-Infra`. Isso ajuda a organizar responsabilidades dentro da organização.

- **EscalationContact** - Fornece o contato de referência para incidentes relacionados ao recurso, como `SOC-Level-1` ou `Team-DevOps`. Essa tag é essencial para equipes de suporte e resposta a incidentes.

- **Lifecycle** - Define a fase do ciclo de vida do recurso, como `Active` ou `Decommissioned`. Essa tag auxilia no planejamento de desativação de recursos.

- **Criticality** - Determina o nível de criticidade do recurso. Preencho com valores como `High`, `Medium` ou `Low`. Isso ajuda a priorizar recursos em situações de crise.

- **Owner** - Nome do responsável direto pelo recurso. Geralmente, preencho com o nome do colaborador ou time, como `caio-marcatti`.

- **ResourceGroup** - Agrupa recursos relacionados que servem a um propósito comum. Utilizo valores como `Frontend` ou `Backend`. Isso facilita a organização e a gestão de recursos.

- **Product** - Nome ou identificador do produto associado ao recurso. Utilizo valores como `Ecommerce` ou `CRM`. Essa tag ajuda a rastrear investimentos em produtos específicos.

Nota: a tag `Project` e `Product` não deve ser usada em recursos compartilhados para evitar associações erradas.
---

### **Camada de Dados**

Na camada de dados, as tags garantem governança, conformidade e segurança. Elas ajudam a responder perguntas como:

- Quais dados possuem alta confidencialidade?
- Quais dados estão sujeitos a regulamentações específicas?
- Quem é o responsável pelos dados armazenados?

As tags que utilizo nesta camada incluem:

- **DataType** - Define o tipo de dado armazenado, como `Personal` ou `Sensitive`. Essa tag é importante para classificação e proteção de dados.

- **Compliance** - Indica quais regulamentações o dado atende, como `LGPD` ou `GDPR`. Essa tag é essencial para auditorias e conformidade legal.

- **DataOwnership** - Identifica o proprietário ou grupo relacionado ao dado. Costumo usar valores como `Customer-12345` ou `Group-Marketing`.

- **DataConfidentiality** - Define o nível de confidencialidade do dado, como `Restricted` ou `Public`. Essa tag é útil para classificar o impacto de vazamentos.

- **DataRetention** - Define o período de retenção obrigatório ou recomendado. Utilizo valores como `ShortTerm` ou `LongTerm`. Essa tag é essencial para planos de backup e recuperação.

- **DataLifecycle** - Define a fase do ciclo de vida do dado, como `Active` ou `Archived`. Isso ajuda a planejar arquivamentos ou exclusões.

---

### **Perguntas que consigo responder com essa estrutura**

Com essas tags, consigo responder perguntas práticas em diferentes contextos:

- **Arquitetura:**
   - Como rastrear recursos por ambiente ou região? Uso tags como `Environment` e `Region`.
   - Como os dados são distribuídos entre projetos e times? Uso tags como `Project` e `Team`.

- **DevOps:**
   - Existem políticas consistentes de ciclo de vida? Uso tags como `Lifecycle`.
   - Como distribuir custos corretamente? Uso tags como `CostCenter` e `CostSplitBasis`.

- **Segurança:**
   - Quais dados possuem alta confidencialidade? Uso tags como `Criticality` e `DataConfidentiality`.
   - Como identificar quem é responsável por incidentes? Uso tags como `EscalationContact`.

---

### **Visualização da Arquitetura de Tags**

Para facilitar a compreensão, incluí uma visualização em SVG que detalha a arquitetura completa das tags. Isso torna mais claro como as diferentes camadas se conectam e interagem.

![Arquitetura de Tags](tag-architecture.svg)

Essa abordagem prática e organizada me ajuda a garantir rastreabilidade, governança e eficiência operacional, além de promover conformidade com regulamentações importantes. Ao adotar essas práticas, consigo gerenciar recursos de forma eficaz e escalável.

