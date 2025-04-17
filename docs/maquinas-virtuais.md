# Máquinas Virtuais no Azure

## Conceitos Básicos sobre VMs

### O que é uma Máquina Virtual?

Uma máquina virtual (VM) é uma emulação de software de um computador físico. No Azure, as VMs fornecem infraestrutura sob demanda, escalável e flexível como parte do modelo de Infraestrutura como Serviço (IaaS). Cada VM no Azure executa em hardware físico em datacenters da Microsoft, mas abstrai o hardware subjacente, permitindo maior flexibilidade.

### Casos de Uso para VMs no Azure

- **Migração Lift-and-shift**: Transferência de cargas de trabalho existentes do local para a nuvem
- **Desenvolvimento e teste**: Ambientes isolados que podem ser provisionados/desativados rapidamente
- **Aplicações de alta disponibilidade**: Distribuídas em múltiplas VMs com balanceamento de carga
- **Recuperação de desastres**: VMs replicadas em regiões diferentes
- **Cargas de trabalho específicas**: Big Data, HPC (High-Performance Computing), aplicações legadas
- **Extensão de datacenter**: Integração dos recursos locais com VMs na nuvem

### Responsabilidades no Modelo IaaS

Ao utilizar VMs no Azure, você mantém responsabilidade por:
- Instalação e configuração do sistema operacional
- Aplicação de atualizações e patches de segurança
- Instalação e manutenção de software
- Backup e recuperação de dados
- Configuração de alta disponibilidade
- Monitoramento de desempenho

A Microsoft gerencia:
- Hardware físico subjacente
- Conectividade de rede física
- Energia e refrigeração
- Segurança física do datacenter

## Tipos e Tamanhos de VMs

### Séries de VMs

O Azure oferece diferentes séries de VMs, cada uma otimizada para cargas de trabalho específicas:

| Série | Otimizada para | Casos de uso típicos |
|-------|----------------|---------------------|
| A | Entrada/Básica | Desenvolvimento e teste, servidores web pequenos |
| B | Econômica | Cargas de trabalho com uso intermitente, desenvolvimento |
| D | Uso geral | Aplicações corporativas, bancos de dados pequenos/médios |
| E | Memória | Bancos de dados grandes, análise em memória |
| F | CPU | Jogos, processamento em lote, servidores web |
| G | Grande memória e armazenamento | Grandes bancos de dados, data warehouses |
| H | Alto desempenho | HPC, simulações, análise de risco |
| L | Armazenamento | Big Data, bancos de dados NoSQL, data warehouses |
| M | Memória máxima | Bancos de dados in-memory, análise, SAP HANA |
| N | GPU | AI, deep learning, visualização, rendering |

### Nomenclatura dos Tamanhos

A nomenclatura dos tamanhos de VM segue um padrão que fornece informações sobre suas características:

`[Série]`+`[Tamanho]`+`[Recursos adicionais (opcional)]`

Exemplos:
- **D2s_v3**: Série D, 2 vCPUs, v3 (terceira geração), 's' indica suporte para armazenamento premium
- **B2ms**: Série B, 2 vCPUs, 'm' indica mais memória, 's' para armazenamento premium
- **NC6**: Série N com GPU CUDA, 6 vCPUs

### Considerações para Escolha de Tamanho

- **vCPUs**: Número de processadores virtuais
- **Memória**: RAM disponível (GB)
- **Armazenamento temporário**: Disco local efêmero (GB)
- **Taxa de transferência de E/S**: IOPS máximo para discos
- **Rede**: Largura de banda de rede máxima
- **GPU**: Presença e tipo de GPUs
- **Custo**: Preço por hora/mês

## Sistemas Operacionais Suportados

### Windows Server

O Azure oferece diversas versões do Windows Server:
- Windows Server 2022
- Windows Server 2019
- Windows Server 2016
- Windows Server 2012 R2
- Versões mais antigas para cargas de trabalho legadas

### Linux

Distribuições Linux oficialmente suportadas no Azure:
- Ubuntu
- Red Hat Enterprise Linux
- SUSE Linux Enterprise
- CentOS
- Debian
- Oracle Linux
- Alma Linux
- Rocky Linux
- Flatcar Container Linux

### Licenciamento

- **Imagens do Azure Marketplace**: Incluem o custo de licença no preço da VM
- **Traga sua própria licença (BYOL)**: Utiliza licenças existentes através do Azure Hybrid Benefit
- **Pay as you go**: Pagamento conforme o uso, sem compromisso antecipado

## Imagens e Discos

### Tipos de Imagens

**1. Imagens do Azure Marketplace**
- Imagens pré-configuradas fornecidas pela Microsoft e parceiros
- Sistemas operacionais puros ou com software pré-instalado
- Atualizadas regularmente com patches de segurança

**2. Imagens personalizadas**
- Criadas a partir de VMs existentes
- Incluem personalizações, aplicativos e configurações
- Armazenadas na Biblioteca de Imagens Compartilhadas ou como VHDs

**3. Biblioteca de Imagens Compartilhadas**
- Repositório para gerenciar e compartilhar imagens
- Suporte para versões e replicação entre regiões
- Compartilhamento entre assinaturas e locatários

### Tipos de Discos no Azure

**1. Discos do SO**
- Contém o sistema operacional
- Limitado a 2048 GB
- Criado automaticamente ao provisionar uma VM

**2. Discos de dados**
- Armazenam dados da aplicação
- Até 32 TB por disco
- Até 64 discos por VM (dependendo do tamanho)

**3. Disco temporário**
- Armazenamento local efêmero
- Dados perdidos durante reinicializações/desalocações
- Não deve ser usado para dados persistentes

### Tipos de Armazenamento para Discos

**1. Standard HDD**
- Discos baseados em HDD
- Menor custo, menor desempenho
- Para cargas de trabalho insensíveis à latência

**2. Standard SSD**
- Discos SSD de nível básico
- Melhor consistência que HDDs
- Para servidores web, aplicações leves

**3. Premium SSD**
- Alto desempenho, baixa latência
- Garantias de IOPS e throughput
- Para cargas de trabalho de produção

**4. Ultra Disk**
- Maior desempenho disponível
- IOPS e throughput configuráveis
- Para cargas de trabalho críticas como SAP HANA, bancos de dados

| Tipo | IOPS máx. | Throughput máx. | Tamanhos | Casos de uso |
|------|-----------|----------------|----------|--------------|
| Standard HDD | 2000 | 500 MB/s | 32 GB - 32 TB | Armazenamento não crítico |
| Standard SSD | 6000 | 750 MB/s | 4 GB - 32 TB | Servidores web, dev/test |
| Premium SSD | 20000 | 900 MB/s | 4 GB - 32 TB | Bancos de dados, produção |
| Ultra Disk | 160000 | 2000 MB/s | 4 GB - 64 TB | SAP HANA, cargas críticas |

## Disponibilidade e Escalabilidade

### Conjuntos de Disponibilidade

Um agrupamento lógico de VMs que permite ao Azure entender como sua aplicação está estruturada para fornecer redundância e disponibilidade.

**Domínios de falha (FD)**
- Representam um rack físico no datacenter
- VMs em diferentes domínios de falha estão em hardware separado

**Domínios de atualização (UD)**
- Representam grupos de VMs e hardware físico que podem ser reiniciados ao mesmo tempo
- Permitem atualizações sem tempo de inatividade total

### Zonas de Disponibilidade

- Locais fisicamente separados dentro de uma região do Azure
- Cada zona tem energia, refrigeração e rede independentes
- VMs distribuídas em zonas protegem contra falhas em nível de datacenter

### Conjuntos de Escala de VMs (VMSS)

- Grupo de VMs idênticas com balanceamento de carga
- Escala automática baseada em demanda ou cronograma
- Ideal para aplicações sem estado como servidores web

## Considerações de Custo

### Fatores que Afetam o Custo

1. **Tamanho da VM**: vCPUs, memória e recursos determinam o preço base
2. **Tipo de disco**: Standard HDD < Standard SSD < Premium SSD < Ultra Disk
3. **Região do Azure**: Os preços variam por região geográfica
4. **Sistema operacional**: Windows adiciona custo de licença (a menos que BYOL)
5. **Uso da rede**: Transferência de dados de saída é cobrada após certos limites
6. **Opções de pagamento**: Pay-as-you-go vs. Reserved Instances

### Opções de Economia

1. **Reserved VM Instances**: Compromisso de 1 ou 3 anos para economizar até 72%
2. **Azure Hybrid Benefit**: Use licenças Windows Server ou SQL Server existentes
3. **Spot VMs**: VMs com grande desconto, mas que podem ser desalocadas a qualquer momento
4. **B-series VMs**: Para cargas de trabalho com uso intermitente
5. **Auto-shutdown**: Programar desligamento automático para ambientes não-produtivos
