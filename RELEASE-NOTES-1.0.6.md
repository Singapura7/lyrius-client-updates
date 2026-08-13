# LyriusRpModPlugin 1.0.6 + LyriusReputation 0.14.4

**By RaulH22 and Singapura**

## Hotfix JVM definitivo

O novo log confirmou que a 1.0.5 avançou além do erro original, mas a JVM ainda
rejeitava `LyriusClientMod` com `VerifyError: Illegal type at constant pool
entry 66`. A correção anterior havia alterado a constante para interface sem
alterar a instrução `invokevirtual`, combinação proibida pelo bytecode Java.

A 1.0.6 remove essa ambiguidade: todas as chamadas ao Fabric Loader passam por
um único `FabricLoaderAccess`, compilado contra `FabricLoader` como interface.
As cinco chamadas consumidoras são redirecionadas sem mudar offsets, branches,
stack maps ou o comportamento do mod.

## Trava de release reforçada

- Confere o opcode real de cada chamada JVM, não apenas a constant pool.
- Exige `invokestatic + InterfaceMethodref` para `FabricLoader.getInstance()`.
- Exige `invokeinterface + InterfaceMethodref` para métodos de instância.
- Rejeita chamadas diretas fora do boundary.
- Exige exatamente seis chamadas corretas no boundary e cinco redirecionamentos.
- Valida também Gson 2.11, `Text.literal`, ClientTickEvents, mappings e fallback sem inventário.

## Conteúdo preservado

- LyriusRPMod 1.21.4-0.3.17 completo e embutido no mesmo JAR.
- Logo, panorama, botão LyriusRP, HUD antigo e configurações originais.
- Reputation/Studio, missões, contratos, maleta e diálogos medievais.
- Correções CPM/Emotecraft SG.8.
- Ícone e autoria oficiais: **By RaulH22 and Singapura**.

## Instalação limpa

1. Remova a 1.0.5 e JARs duplicados de LyriusClient, LyriusRPMod ou CPMEmoteFix.
2. Instale somente `LyriusRpModPlugin-1.0.6.jar` no Fabric 1.21.4.
3. No Paper 1.21.4, troque o plugin por `LyriusReputation-0.14.4.jar`.
4. Reinicie cliente e servidor completamente; não use `/reload`.

Os avisos de músicas `.nbs` do Emotecraft, LootBeams e mixins opcionais que
aparecem antes do crash não causaram a falha fatal registrada.
