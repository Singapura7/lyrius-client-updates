# LyriusRpModPlugin 1.0.4 + LyriusReputation 0.14.2

## A build que fecha o ciclo

Esta atualização consolida o LyriusRP antigo, o Reputation/Studio e a correção CPM/Emotecraft SG.8 no mesmo cliente, preservando as interfaces e opções anteriores.

### Correções críticas

- Eliminado o crash `Packet type ... lyriusrp:json_payload is already registered`.
- O canal legado passa a ter um único proprietário quando o LyriusRPMod oficial está embutido.
- Pasta correta restaurada: `plugins/LyriusRpModPlugin/config.yml`.
- Migração compatível das pastas temporárias antigas, sem apagar configuração válida.
- Cor-base do HUD administrativo controlada pelo servidor e persistida no cliente por `server-id`.
- A mudança de cor é reenviada aos jogadores conectados após reload administrativo.
- Emblemas e evolução cobre/prata/ouro usam confirmação e três tentativas idempotentes.
- Diálogos começam filtrados pela ilha atual e podem alternar para todas.
- Retorno das confirmações de exclusão e conversão do Studio corrigido.

### NPCs, backups e ItemsAdder

- Nova categoria **Profissão**: Ocultista, Ferreiro, Artesão, Minerador, Fazendeiro e Médico.
- Novos ícones de Loja e Missão importante.
- Backups centralizados em `plugins/LyriusReputationBackups/`.
- Administração: `/repadmin backups status|intervalo <min>|limpar|apagar CONFIRM`.
- Fontes/tags e assets de reputação atualizados.
- Convenção `emblema_<organizacao>_<tier>` para novas organizações.
- Handoff de teleporte de NPC entre ilhas via MySQL e comando de proxy configurável.

### Segurança e atualização

- Cliente 1.0.4 e plugin 0.14.2 assinados com RSA/SHA-256.
- Manifesto HTTPS com versão, URL, SHA-256 e notas.
- Somente versões superiores são oferecidas.
- O source e a chave privada não são publicados neste repositório público.
- Créditos: **By RaulH22 and Singapura**.

### Instalação

1. Remova JARs antigos duplicados de LyriusClient, LyriusRPMod e CPMEmoteFix.
2. Instale `LyriusRpModPlugin-1.0.4.jar` no cliente.
3. Instale `LyriusReputation-0.14.2.jar` no Paper.
4. Extraia o addon ItemsAdder e execute `/iazip`.
5. Troque `XXXXXX` pela senha real, preferencialmente via variável de ambiente.
6. Use um `network-sync.server-id` único em cada ilha e reinicie por completo.

A build, os JARs, a assinatura, JSON, YAML, PNG e referências de runtime foram verificados. A autenticação MySQL real e o proxy entre ilhas exigem homologação no servidor.