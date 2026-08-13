# LyriusRpModPlugin 1.0.5 + LyriusReputation 0.14.3

**By RaulH22 and Singapura**

## Hotfix de inicialização

Esta versão corrige o crash que ocorria antes do menu principal no Fabric Loader
0.19.3. A build 1.0.4 possuía chamadas ao `FabricLoader` gravadas como se ele
fosse uma classe concreta; em execução ele é uma interface, causando
`IncompatibleClassChangeError` durante `LyriusClientMod.onInitializeClient`.

A 1.0.5 corrige todas as nove referências e adiciona uma trava de release que
analisa todas as classes Lyrius. Uma build com esse contrato binário incorreto
agora é rejeitada antes de ser distribuída.

## Pacote unificado preservado

- LyriusRPMod 1.21.4-0.3.17 completo permanece embutido no mesmo JAR.
- Logo, panorama, botão LyriusRP, HUD antigo e configurações originais continuam presentes.
- LyriusReputation/Studio continua responsável pelas interfaces medievais, missões, contratos, maleta e diálogos.
- Compatibilidade CPM/Emotecraft SG.8 continua integrada.
- Ícone e autoria permanecem como definidos pelo LyriusRP: **By RaulH22 and Singapura**.

## Atualização oficial pelo GitHub

- Manifesto oficial em `latest.json`.
- Download oferecido somente quando a versão publicada é superior à instalada.
- URL obrigatoriamente HTTPS.
- Validação do SHA-256 antes da instalação.
- Validação do ID e da versão interna do mod.
- Bloqueio de pacote parcial sem LyriusRP, Reputation ou CPM SG.8.
- Verificação do mesmo certificado de assinatura da instalação atual.
- Troca do JAR somente depois que o Minecraft é encerrado.

## Instalação

1. Remova a build 1.0.4 e qualquer JAR antigo duplicado de LyriusClient, LyriusRPMod ou CPMEmoteFix.
2. Instale somente `LyriusRpModPlugin-1.0.5.jar` no cliente Fabric 1.21.4.
3. Instale `LyriusReputation-0.14.3.jar` no Paper 1.21.4.
4. Não use `/reload`; reinicie cliente e servidor por completo.

O aviso do Emotecraft sobre músicas `.nbs` com instrumentos personalizados não
foi a causa deste crash. O erro fatal corrigido era a referência binária do
Fabric Loader.
