# Lyrius RP Made It 1.0.52 — Updater Real

Esta versão corrige o mecanismo de autoatualização do cliente.

- Remove o uso inválido de `redirectInput(Redirect.DISCARD)` que gerava `Redirect invalid for reading: WRITE`.
- Inicia o helper externo de atualização antes do Minecraft encerrar.
- O helper aguarda o PID do Minecraft terminar e só então substitui o JAR.
- Usa backup, retry e rollback em Windows e Linux.
- Registra `ARMED`, `OK` ou `ERROR` em `config/lyriusclient-update/install-status.txt`.
- A versão atual é lida do próprio `fabric.mod.json`, sem número hardcoded.
- Mantém validação de HTTPS, SHA-256 e assinatura da identidade oficial do Lyrius.

A partir da 1.0.52, futuras versões podem ser instaladas automaticamente pelo próprio Made It após o jogador aceitar a atualização e fechar o Minecraft.
