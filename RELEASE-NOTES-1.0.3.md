# LyriusRpModPlugin 1.0.3 — A União Definitiva

Esta é a versão em que o Lyrius volta a ser **um pacote de verdade**. O Studio e o sistema de reputação não substituem mais o antigo LyriusRP: agora os dois coexistem dentro do mesmo JAR, junto com a correção CPM/Emotecraft SG.8.

## Destaques

- **LyriusRP original restaurado:** logo, panorama, botão LyriusRP, HUD, relógio, sede, temperatura, almas, peso, stamina, mochila e configurações antigas.
- **Configuração nova corrigida:** a tela vazia foi eliminada; o fundo não encobre mais os controles.
- **Duas configurações completas:** opções do Reputation/Studio e botão para abrir as opções originais do LyriusRP.
- **CPM + Emotecraft SG.8 integrado:** correção de curvas, previews e isolamento de estado por entidade/renderização.
- **GUI administrativa restaurada:** temas de inventário essenciais são reativados automaticamente em configurações antigas quebradas.
- **BetonQuest com revisão segura:** botão para revisar todas as conversas, cancelar entradas problemáticas, preservar backups e converter somente as aprovadas.
- **Recognizer dentro do plugin principal:** canal JSON, inventário de mods, verificações, efeitos, vanish e `/lrp` sem carregar um segundo plugin.
- **Atualização profissional:** manifesto HTTPS, SHA-256, somente upgrade, assinatura digital e bloqueio de release parcial.

## Correções importantes

- Corrigida a ordem de renderização de todas as telas customizadas.
- Corrigido retorno ao Mod Menu e acesso à configuração original.
- Preservado o ícone oficial solicitado do LyriusRpModPlugin.
- Créditos atualizados para **By RaulH22 and Singapura**.
- O banco MySQL continua preparado para `node-01.lyriusrp.com:3306/s12_ilha_singa`, mantendo `XXXXXX` como senha substituível.

## Instalação

1. Remova JARs antigos duplicados do LyriusRPMod, CPMEmoteFix e LyriusClient.
2. Instale apenas `LyriusRpModPlugin-1.0.3.jar` no cliente.
3. Instale `LyriusReputation-0.14.1.jar` no servidor.
4. Copie o addon ItemsAdder e execute `/iazip`.
5. Reinicie o servidor por completo; não use `/reload`.

## Atualização automática

Hospede o JAR assinado em HTTPS, publique `latest.json` com versão, URL, SHA-256 e notas, e informe o endereço em `client-update.manifest-url`. Jogadores em versão inferior recebem a oferta assim que o handshake do mod termina.
