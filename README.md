# Script Auto - Script de Automação para Instalação de Pacotes

## Visão Geral do Projeto

Este é um script de automação em bash (`install.sh`) projetado para simplificar a instalação de pacotes em diferentes distribuições Linux. O script suporta as principais famílias de distribuições, incluindo sistemas baseados em Ubuntu/Debian, Arch Linux e derivados, e inclui tratamento especial para pacotes do AUR (Arquivo de Usuário do Arch - Arch User Repository).

### Principais Recursos

- **Suporte a múltiplas distribuições**: Detecta automaticamente a distribuição Linux e utiliza os gerenciadores de pacotes apropriados (apt para Ubuntu/Debian, pacman para sistemas baseados em Arch)
- **Integração com AUR**: Tratamento especial para usuários do Arch Linux para instalar pacotes do AUR usando `yay`
- **Listas abrangentes de pacotes**: Listas predefinidas de pacotes comumente usados em categorias (desenvolvimento, multimídia, utilitários, etc.)
- **Suporte a AppImage**: Integração com AppImageSup para gerenciar aplicações AppImage
- **Tratamento de erros**: Lida graciosamente com pacotes ausentes e falhas de instalação
- **Impõe privilégios de root**: Garante que o script seja executado com as permissões apropriadas

### Arquitetura

O script segue uma abordagem modular com:
- Listas principais de pacotes para repositórios oficiais
- Listas separadas para pacotes do AUR (sistemas baseados em Arch)
- Lógica de detecção de distribuição
- Funções específicas de instalação por plataforma
- Mecanismos de relatório de erro

## Compilação e Execução

### Pré-requisitos
- Privilégios de root (o script deve ser executado com `sudo`)
- Conexão à internet para download dos pacotes

### Uso
```bash
sudo ./install.sh
```

### Configuração
O script contém três arrays principais de pacotes que podem ser personalizados:
- `PACOTES`: Pacotes de repositório oficial (comuns a todas as distros)
- `AUR_PACOTES`: Pacotes do AUR (para sistemas baseados em Arch)
- `APPIMAGE`: Aplicações AppImage

Para personalizar a instalação, edite esses arrays no script antes de executar.

### Distribuições Suportadas
- Distribuições Ubuntu e baseadas no Ubuntu
- Distribuições Debian e baseadas no Debian
- Arch Linux e derivados (CachyOS, EndeavourOS, etc.)

## Convenções de Desenvolvimento

### Estilo de Codificação
- Escrito em bash seguindo conformidade POSIX sempre que possível
- Usa `set -e` para tratamento de erros
- Inclui comentários detalhados em português (brasileiro)
- Design modular de funções para diferentes métodos de instalação

### Práticas de Teste
- Validação de detecção de distribuição
- Verificação de existência de pacotes antes de tentativas de instalação
- Verificação de códigos de erro para instalações do AUR

### Diretrizes de Contribuição
- Adicione novos pacotes ao array apropriado (`PACOTES`, `AUR_PACOTES` ou `APPIMAGE`)
- Mantenha ordenação alfabética ou lógica dentro dos arrays
- Garanta que os pacotes estejam disponíveis nos repositórios-alvo
- Teste em múltiplas famílias de distribuição sempre que possível

## Estrutura do Projeto
- `install.sh`: Script principal de automação
- `README.md`: Documentação abrangente do projeto (este arquivo)

## Notas Adicionais
- O script instala automaticamente o `yay` se ainda não estiver presente em sistemas baseados em Arch
- As listas de pacotes podem ser modificadas para atender às necessidades individuais
- O script fornece relatórios detalhados de instalação, incluindo pacotes ignorados
- Inclui configuração automática do repositório Flathub para aplicações Flatpak
