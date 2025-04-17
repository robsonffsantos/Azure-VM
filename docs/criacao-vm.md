# Criação e Configuração de uma Máquina Virtual no Microsoft Azure

## Preparação e requisitos

Antes de iniciar a criação de uma máquina virtual (VM) no Azure, certifique-se de que você possui:

- Uma conta Microsoft Azure ativa
- Créditos suficientes ou forma de pagamento configurada
- Conhecimento básico sobre o tipo de VM necessária para seu caso de uso
- Compreensão dos requisitos técnicos (CPU, memória, armazenamento)
- Navegador web atualizado
- Conexão estável com a internet

## Processo detalhado de criação

1. **Acesse o Portal Azure**
   - Entre no [Portal Azure](https://portal.azure.com) com suas credenciais
   - No dashboard principal, clique em "Criar um recurso"

2. **Selecionando a VM**
   - Na barra de pesquisa, digite "Máquina Virtual"
   - Selecione "Máquina Virtual" nos resultados
   - Clique em "Criar"

3. **Configuração básica**
   - Selecione sua assinatura Azure
   - Crie um novo grupo de recursos ou selecione um existente
   - Forneça um nome para sua VM
   - Escolha a região onde deseja implantar a VM
   - Selecione as opções de disponibilidade conforme necessário
   - Escolha a imagem do sistema operacional (Windows Server, Ubuntu, etc.)
   - Configure o tamanho da VM (selecione com base nos requisitos de CPU, RAM)

4. **Configurações de administrador**
   - Para VMs Windows: crie um nome de usuário e senha
   - Para VMs Linux: configure nome de usuário e senha ou chave SSH
   - Configure portas de entrada (geralmente RDP para Windows ou SSH para Linux)

5. **Discos**
   - Selecione o tipo de disco (SSD Premium, SSD Standard, HDD Standard)
   - Configure o tamanho do disco do sistema operacional
   - Adicione discos de dados adicionais, se necessário

6. **Rede**
   - Selecione ou crie uma rede virtual
   - Configure a sub-rede
   - Defina o endereço IP (dinâmico ou estático)
   - Configure o grupo de segurança de rede para controlar o tráfego

7. **Gerenciamento**
   - Configure opções de monitoramento
   - Defina diagnósticos de inicialização
   - Configure identidades gerenciadas (se necessário)
   - Configure backup automático (opcional)

8. **Revisão e criação**
   - Revise todas as configurações selecionadas
   - Verifique se a validação foi aprovada
   - Clique em "Criar" para iniciar a implantação da VM

## Configurações essenciais

Após a criação da VM, é importante configurar os seguintes aspectos:

### Segurança
- **Atualize o sistema operacional** para as últimas versões
- **Configure o firewall** tanto no nível do Azure quanto do sistema operacional
- **Instale software antivírus/antimalware** (para VMs Windows)
- **Implemente o acesso just-in-time** para aumentar a segurança

### Conectividade
- **Configure o DNS** conforme necessário
- **Configure endpoints** para serviços específicos
- **Configure VPN** se necessária comunicação segura

### Escalabilidade
- **Configure conjuntos de dimensionamento** se precisar escalar horizontalmente
- **Configure regras de autoescalabilidade** baseadas em métricas

### Backup e recuperação
- **Configure backup regular** da VM
- **Defina políticas de retenção** para os backups
- **Teste procedimentos de recuperação**

## Verificação e validação

Após a criação e configuração da VM, realize os seguintes passos para garantir que tudo está funcionando corretamente:

1. **Conecte-se à VM**
   - Para Windows: use RDP (Remote Desktop Protocol)
   - Para Linux: use SSH (Secure Shell)

2. **Verifique os recursos**
   - Confirme se CPU, memória e armazenamento estão corretos
   - Verifique se o sistema operacional foi instalado corretamente

3. **Teste a conectividade**
   - Verifique se é possível acessar a internet a partir da VM
   - Teste a comunicação entre VMs, se aplicável
   - Valide as regras de firewall

4. **Monitore o desempenho**
   - Verifique o Monitor do Azure para métricas de desempenho
   - Configure alertas para condições críticas
   - Revise os logs de diagnóstico

5. **Documente a configuração**
   - Anote todas as configurações importantes
   - Documente procedimentos de acesso e manutenção
   - Mantenha um registro de alterações realizadas
