# LyriusRP — patch notes completo

## LyriusRpModPlugin 1.0.5 + LyriusReputation 0.14.3

**By RaulH22 and Singapura**

Esta é a visão completa do ecossistema LyriusRP atual: o que o plugin faz, como
o cliente participa e o que mudou nesta entrega. A regra central continua
simples: o servidor decide progresso, reputação, condições e recompensas; o mod
renderiza as interfaces e envia apenas a intenção do jogador.

## A grande novidade da 1.0.5 / 0.14.3

### Inicialização Fabric realmente corrigida

- Corrigido o `IncompatibleClassChangeError` de `FabricLoader.getInstance()`.
- As nove referências do Lyrius ao Fabric Loader agora usam o contrato correto de interface.
- Novo verificador percorre todas as classes do mod e bloqueia uma release incompatível.
- O teste não depende mais de conferir apenas uma classe nem de esperar o jogo crashar.
- O antigo problema de registro duplicado do canal `lyriusrp:json_payload` continua corrigido.

### Atualizador conectado ao GitHub

- O plugin 0.14.3 já traz o endereço do manifesto oficial em sua configuração padrão.
- O catálogo é consultado de forma assíncrona, sem bloquear a thread principal do Paper.
- Jogadores com a opção de atualização ativa recebem a oferta depois do handshake.
- O manifesto controla versão, URL, SHA-256 e texto mostrado ao jogador.
- Somente upgrades são oferecidos; a versão instalada não é rebaixada.
- O download exige HTTPS, tamanho máximo e hash SHA-256 exato.
- O arquivo recebido precisa possuir o ID e a versão Fabric esperados.
- O atualizador confirma que o JAR ainda contém cliente, LyriusRP original e CPM SG.8.
- A assinatura precisa ser da mesma identidade criptográfica da instalação atual.
- A substituição ocorre após o Minecraft fechar, evitando trocar um JAR em uso.

## Reputação e organizações

- Reputação individual persistente por jogador e organização/ilha.
- Organizações com identidade visual, cor e gradiente próprios.
- Progressão por tiers e emblemas, incluindo cobre, prata e ouro.
- Maleta de reputação com visão das organizações e progresso até o próximo rank.
- Histórico de alterações administrativas e operações persistentes.
- Rankings individuais, guildas e consultas administrativas.
- Integração regional com WorldGuard e actionbar configurável.
- Integração de guilda/reino por placeholders do Kingdoms.
- Criação, edição e exclusão de organizações pelo Studio administrativo.
- Template padronizado para adicionar novos emblemas, tiers e animações.

## Emblemas, recompensas e apresentação

- Catálogo de emblemas e recompensas centralizado no servidor.
- Entrega apenas após confirmação autoritativa do servidor.
- Apresentação visual separada da entrega real do item/recompensa.
- Confirmação do cliente e até três tentativas idempotentes para apresentações perdidas.
- Proteção contra repetir a mesma concessão ao reconectar.
- Animação de recebimento e evolução de tier sem consumir ou conceder Totem da Imortalidade.
- Compatibilidade com itens vanilla, ItemsAdder e MMOItems por camada de item.
- Ferramentas administrativas para catálogo, concessão e manutenção de recompensas.

## Missões e diário

- Criador visual de missões com etapas, validação e publicação.
- Missões com objetivos de coleta, fabricação, combate, interação, espera, construção e fala.
- Contadores visíveis de objetivo, quantidade atual e quantidade restante.
- Diário de missões no cliente com navegação, conclusão e abandono confirmado em duas etapas.
- Abandono remove runtime, objetivos e vínculo ativo de forma persistente.
- Limite diário do quadro de missões, padrão de duas missões por jogador.
- Permissões para três, quatro ou quantidade ilimitada por dia.
- Quadro de missões com folhetos ItemsAdder e contrato medieval antes de iniciar.
- A missão só começa depois de o jogador aceitar/selar o contrato.
- Título e subtítulo de conclusão configuráveis.
- Test pack do Grande Forno do Padeiro para validar objetivos compostos.
- Guias de construção e marcadores temporários para etapas com schematic.

## Diálogos cinematográficos

- HUD medieval nativa do mod, sem transformar respostas em inventário.
- Texto digitado, animações, escurecimento, escala e redução de movimento configuráveis.
- Temas por organização, incluindo a identidade Hakuna.
- Respostas com seleção, navegação e rolagem lenta do texto selecionado.
- Sessões controladas pelo servidor e fechamento por Esc, Shift, distância e eventos do jogador.
- Bloqueio opcional de conversa durante combate.
- Fallback em chat Lyrius para jogadores sem a tela nativa disponível.
- Aviso para jogador sem o mod quando a fala não puder ser exibida corretamente.
- Editor em mapa mental para nós, respostas, condições, eventos e ligações.
- Histórico, simulação, revisão e publicação de conversas.
- Filtro inicial pela ilha atual, com opção de visualizar conversas das outras ilhas.
- Integração com BetonQuest e revisão assistida das conversas antigas.
- Conversões problemáticas podem ser canceladas individualmente antes da publicação.
- Backup antes de alterar pacotes externos do BetonQuest.

## Studio administrativo

- Central administrativa visual para organizações, NPCs, missões, diálogos e recompensas.
- Mapa mental com inspector lateral e conexões entre blocos.
- Operações incrementais para reduzir tráfego e reconstruções completas.
- Confirmação para ações sensíveis e entradas administrativas.
- Whitelist de comandos para impedir recompensa/timeline com comando arbitrário.
- Painéis separados de diagnóstico, desempenho e analytics.
- Ferramentas técnicas ficam fora do hub normal para não poluir a experiência administrativa.
- Layout do Studio e preferências do administrador podem ser persistidos.

## NPCs e Citizens

- Cadastro, inspeção, spawn, despawn, movimento e teleporte de NPCs Citizens.
- Vínculo de NPC com organização, diálogo, saudação, despedida e missão.
- Marcadores visuais de missão acima do NPC, com alcance e altura configuráveis.
- Categorias organizadas e tipo de NPC reversível para “Sem tipo”.
- Categoria **Profissão** com Ocultista, Ferreiro, Artesão, Minerador, Fazendeiro e Médico.
- Tipos visuais para Loja, Missão e outras funções administrativas.
- Integração de skin com Citizens, SkinsRestorer e suporte a perfil/cabeça.
- Auditoria das mudanças administrativas feitas nos NPCs.
- Índice global e rotinas centralizadas, evitando uma task separada para cada NPC.
- Registro de presença dos NPCs por ilha no banco central.
- Solicitação de teleporte até NPC de outra ilha com handoff via MySQL e proxy.
- Cada servidor mantém um `network-sync.server-id` único, mas administradores podem consultar a rede completa.

## Rede entre ilhas e banco de dados

- Suporte a MySQL central ou SQLite local.
- Pool JDBC com limite, timeout de empréstimo, validação e detecção de vazamento.
- Circuit breaker e backpressure para não transformar falha de banco em avalanche de conexões.
- Migrações de schema com backup de segurança.
- Importação opcional de uma instalação SQLite para MySQL.
- Documentos compartilhados compactados e sincronizados entre servidores.
- Heartbeat das ilhas e catálogo de NPCs conectados.
- Progresso, reputação e estado persistidos no banco autoritativo.
- Credenciais podem vir de variáveis de ambiente, evitando senha real no arquivo.
- A operação real entre ilhas depende de senha válida, IDs únicos e comando correto do proxy.

## Backups organizados

- Backups separados da pasta principal em `plugins/LyriusReputationBackups/`.
- Categorias próprias para banco, configurações e alterações externas.
- Intervalo, retenção e idade máxima configuráveis.
- Apenas uma rotina de backup é executada por vez.
- Backups podem ser adiados sob pressão do banco.
- Comandos para status, alteração de intervalo, limpeza e exclusão confirmada.
- Migração das rotinas antigas sem misturar snapshots com dados ativos do Reputation.

## HUD e identidade visual

- HUD administrativo medieval com tema-base definido pelo servidor.
- Cor, início e fim do gradiente configuráveis em `client-bridge.base-hud-theme`.
- A preferência é enviada ao entrar e após reload administrativo.
- O cliente salva a cor por `server-id` e mantém o valor até o servidor enviar outro.
- Organizações continuam usando suas próprias cores e gradientes.
- Escala do diálogo, densidade, animações, texto digitado e acessibilidade continuam configuráveis.
- Interfaces preservam as faixas e cantos medievais sem a camada translúcida excessiva.

## LyriusRPMod original preservado

- O LyriusRPMod 1.21.4-0.3.17 permanece inteiro dentro do JAR unificado.
- Logo LyriusRP, panorama, botão principal e identidade da tela inicial são preservados.
- Relógio, sede, temperatura, almas, peso, stamina, mochila e HUD antigo continuam disponíveis.
- A tela de configurações do Mod Menu expõe as opções do Reputation e as opções originais do LyriusRP.
- A configuração do recognizer continua em `plugins/LyriusRpModPlugin/config.yml`.
- Pastas antigas são migradas sem sobrescrever uma configuração correta já existente.
- Inventário de mods, dados de resource packs, efeitos, vanish e ferramentas administrativas continuam integrados ao plugin principal.

## CPM e Emotecraft SG.8

- Correções de bend entre Customizable Player Models e Player Animator/Emotecraft.
- Estado de curvatura isolado por renderização para evitar vazamento entre entidades.
- Proteções para preview e renderização de modelos CPM.
- Compatibilidade incluída no JAR unificado, sem precisar instalar o antigo CPMEmoteFix separadamente.
- Emotes de NPC no servidor permanecem desativados por padrão nesta release; a compatibilidade visual do cliente continua ativa.

## ItemsAdder

- Namespace `lyrius_reputation` com itens, fontes e interfaces próprios.
- Ícones administrativos para voltar, avançar, fechar, publicar, configurar e adicionar.
- Emblemas, organizações, quadro de missão, diário, contrato, selo e fichas visuais.
- Ícones de profissões e nova exclamação para NPC/missão importante.
- Migração opcional de itens de recompensa gerados anteriormente.
- O plugin continua funcional sem ItemsAdder; a integração é uma camada visual opcional.

## Compatibilidade e segurança

- Paper 1.21.4 e Java 21 no servidor.
- Fabric 1.21.4, Java 21 e Fabric Loader 0.16.10 ou superior no cliente.
- Ponte com Citizens, BetonQuest, ItemsAdder, PlaceholderAPI, WorldGuard, Kingdoms, SkinsRestorer, MMOItems e ImperialCoin/Vault quando disponíveis.
- Limite de pacotes por segundo na ponte do cliente.
- Handshake e exigência opcional do mod com tempo de tolerância.
- O cliente nunca concede reputação, conclui objetivo ou entrega recompensa sozinho.
- JARs assinados e checksums publicados para detectar alterações.
- A chave privada de assinatura nunca acompanha source, release ou certificado público.
- Integrações de DTLTraders e lojas avançadas permanecem arquivadas/desativadas por padrão nesta versão.

## Pastas finais

```text
plugins/LyriusRpModPlugin/       # recognizer e compatibilidade LyriusRP antiga
plugins/LyriusReputation/        # reputação, Studio, missões, diálogos e banco
plugins/LyriusReputationBackups/ # snapshots e backups centralizados
```

## Comandos principais

- `/reputacao` ou `/rep`: abre a maleta do jogador.
- `/repadmin`: abre o Studio administrativo e seus subcomandos.
- `/lrep`: atalho administrativo e ferramentas do BetonQuest.
- `/lnpc`: administração de NPCs, skins, categorias e eventos.
- `/lyriusplugin` ou `/lrp`: inspeção do cliente e mecanismos LyriusRP integrados.
- `/repadmin backups status|intervalo <min>|limpar|apagar CONFIRM`: manutenção de backups.

## Instalação limpa

1. Apague somente os JARs antigos duplicados; preserve as pastas de configuração.
2. Coloque `LyriusRpModPlugin-1.0.5.jar` na pasta `mods` do cliente.
3. Coloque `LyriusReputation-0.14.3.jar` na pasta `plugins` do Paper.
4. Instale/atualize o addon ItemsAdder e execute a regeneração do resource pack.
5. Substitua `XXXXXX` ou configure `LYRIUS_REPUTATION_DB_PASSWORD`.
6. Defina um `network-sync.server-id` diferente em cada ilha.
7. Reinicie completamente; não use `/reload`.

Esta entrega foi montada para conservar o que já funcionava e fechar o crash de
inicialização sem retirar a identidade do LyriusRP original.
