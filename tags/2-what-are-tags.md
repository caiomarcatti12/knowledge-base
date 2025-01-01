### 2. O que são Tags?

As **tags** são metadados em formato de pares de chave e valor que podem ser atribuídos a recursos na nuvem para identificá-los e organizá-los. Elas servem como etiquetas digitais, permitindo classificar e categorizar recursos de forma clara e padronizada. Uma tag é composta por:

- **Chave:** Um identificador descritivo que define o propósito da tag. Exemplo: `Environment`, `Owner`, `Project`.
- **Valor:** O dado associado à chave, que detalha ou especifica a informação. Exemplo: `Production`, `John Doe`, `Ecommerce`.

Por exemplo, ao criar uma instância de servidor em nuvem, pode-se aplicar as seguintes tags:

- `Environment=Development`
- `Owner=EquipeDeTI`
- `CostCenter=12345`

Essas tags ajudam a identificar o ambiente da instância (Desenvolvimento), o time responsável (TI) e o centro de custo associado (12345).

#### Benefícios Fundamentais

O uso de tags oferece várias vantagens, incluindo:

1. **Organização de Recursos:**
    - Facilita a identificação de recursos em ambientes complexos.
    - Ajuda a categorizar ativos por função, projeto, localização ou equipe.

2. **Rastreamento de Custos:**
    - Permite associar custos específicos a projetos ou departamentos.
    - Auxilia na criação de relatórios detalhados de gastos.

3. **Automatização:**
    - Tags podem ser usadas para disparar regras automáticas em sistemas baseados em políticas ou scripts.
    - Exemplo: desligar instâncias com a tag `Environment=Testing` após um determinado horário.

4. **Governança e Conformidade:**
    - Facilita a adesão às políticas de segurança e governança corporativa.
    - Possibilita o monitoramento e a auditoria de recursos com base nas tags atribuídas.

#### Limitações das Tags
Embora sejam extremamente úteis, as tags também possuem limitações:

- Podem ser aplicadas apenas a recursos suportados pela plataforma de nuvem.
- Dependem de uma estrutura de nomenclatura consistente para evitar ambiguidades.
- Não têm impacto funcional direto nos recursos, funcionando apenas como metadados.

#### Exemplos de Uso Prático

1. **Identificação de Ambientes:**
    - `Environment=Production`
    - `Environment=Development`

2. **Gerenciamento de Projetos:**
    - `Project=WebApp`
    - `Project=DataPipeline`

3. **Segurança:**
    - `ConfidentialityLevel=High`
    - `Owner=SecurityTeam`

4. **Cálculo de Custos:**
    - `CostCenter=001`
    - `Department=Marketing`

As tags são um recurso fundamental para manter a gestão e a operação em nuvem eficientes. No próximo capítulo, exploraremos os motivos para utilizá-las de forma estratégica e os objetivos que podem ser alcançados por meio de sua implementação.

