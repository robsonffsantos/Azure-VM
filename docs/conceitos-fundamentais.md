# Conceitos Fundamentais do Azure

## O que é Microsoft Azure?

Microsoft Azure é uma plataforma de computação em nuvem criada pela Microsoft que oferece uma ampla gama de serviços, desde infraestrutura básica como servidores virtuais, armazenamento e redes, até serviços avançados como inteligência artificial, aprendizado de máquina e IoT. O Azure permite que empresas e desenvolvedores criem, implantem e gerenciem aplicativos e serviços através de uma rede global de datacenters gerenciados pela Microsoft.

## Modelos de Serviço em Nuvem

O Azure oferece os três principais modelos de serviço em nuvem:

### IaaS (Infraestrutura como Serviço)
- **Definição**: Fornece infraestrutura de computação virtualizada sob demanda
- **Responsabilidade do cliente**: SO, middleware, aplicativos, dados
- **Responsabilidade da Microsoft**: Hardware físico, rede, virtualização
- **Exemplos no Azure**: Máquinas Virtuais, Redes Virtuais, Armazenamento

### PaaS (Plataforma como Serviço)
- **Definição**: Ambiente para desenvolvimento, teste e implantação de aplicativos
- **Responsabilidade do cliente**: Aplicativos e dados
- **Responsabilidade da Microsoft**: Hardware físico, rede, virtualização, SO, middleware
- **Exemplos no Azure**: App Service, Functions, Logic Apps

### SaaS (Software como Serviço)
- **Definição**: Aplicativos completos entregues pela internet
- **Responsabilidade do cliente**: Apenas os dados e acesso
- **Responsabilidade da Microsoft**: Toda a pilha de infraestrutura e aplicativo
- **Exemplos no Azure**: Microsoft 365, Dynamics 365

## Vantagens da Computação em Nuvem

### Econômicas
- **Modelo de pagamento por uso**: Redução de gastos de capital (CapEx) para gastos operacionais (OpEx)
- **Economia de escala**: Custos reduzidos devido à infraestrutura compartilhada
- **Eliminação de custos de manutenção**: Sem necessidade de manter datacenters físicos

### Técnicas
- **Escalabilidade**: Capacidade de aumentar ou diminuir recursos conforme a demanda
- **Elasticidade**: Ajuste automático de recursos baseado no uso
- **Alta disponibilidade**: SLAs garantidos para vários serviços
- **Agilidade**: Implantação rápida de recursos (minutos vs. semanas/meses)
- **Recuperação de desastres**: Recursos distribuídos geograficamente

### Estratégicas
- **Foco no negócio**: Redução da necessidade de gerenciar infraestrutura
- **Inovação acelerada**: Acesso rápido a tecnologias emergentes
- **Alcance global**: Presença em regiões em todo o mundo sem infraestrutura própria

## Estrutura Geográfica do Azure

### Regiões
Uma região é uma área geográfica que contém pelo menos um datacenter, possivelmente vários datacenters próximos e interconectados. O Azure seleciona inteligentemente os datacenters dentro de uma região para otimizar a disponibilidade.

**Exemplos de regiões**:
- East US (Virginia)
- West Europe (Holanda)
- Southeast Asia (Singapura)
- Brazil South (São Paulo)

### Zonas de Disponibilidade
Localizações físicas separadas dentro de uma região do Azure. Cada zona de disponibilidade é composta por um ou mais datacenters equipados com energia, refrigeração e rede independentes.

**Características**:
- Isolamento físico entre zonas
- Se uma zona ficar inativa, as outras continuam funcionando
- Conectadas por rede privada de alta velocidade

### Pares de Regiões
Regiões do Azure são organizadas em pares dentro da mesma geografia (como EUA, Europa ou Ásia). Isso garante:

- Distância física mínima de 300 milhas (quando possível)
- Atualizações planejadas aplicadas sequencialmente
- Prioridade de recuperação para uma região do par em caso de desastre

**Exemplos de pares de regiões**:
- East US e West US
- North Europe (Irlanda) e West Europe (Holanda)

## Recursos e Grupos de Recursos

### Recursos
Um recurso é um item gerenciável disponível no Azure. Exemplos:
- Máquinas virtuais
- Contas de armazenamento
- Bancos de dados
- Redes virtuais

### Grupos de Recursos
Um grupo de recursos é um contêiner lógico que armazena recursos relacionados para uma solução Azure. Características importantes:

- **Organização lógica**: Agrupamento de recursos relacionados
- **Ciclo de vida**: Recursos compartilham o mesmo ciclo de vida
- **Escopo para aplicação de permissões**: Controle de acesso no nível do grupo
- **Escopo para faturamento**: Facilita a análise de custos

## Azure Resource Manager (ARM)

O Azure Resource Manager é o serviço de implantação e gerenciamento para o Azure, fornecendo uma camada de gerenciamento que permite criar, atualizar e excluir recursos.

**Benefícios**:
- Gerenciamento de recursos como grupo
- Implantação, gerenciamento e monitoramento consistentes
- Controle de acesso baseado em função (RBAC)
- Aplicação de tags para organização lógica
- Clareza de faturamento por tags ou grupos
