## 0.3.0-beta.32 — 2026-11-06

Pedido do Jorge: duas proteções para o firmware.

- **Código para instalar**: no cartão **Firmware** (Sistema), à direita de **Enviar ficheiro**, um
  campo para o código de 6 algarismos **da versão nova**. Vale para **Instalar** (do GitHub) e para
  **Enviar ficheiro**. Quem o confere é a placa, não só o portal. Para um ficheiro, usa a **marca da
  versão** que o firmware passa a trazer (`FW_VER_MARK` = `[[Intelitherm-FWVER=<versão>@<data>]]`,
  em `config.h` com `FW_DATE`). Com o código errado, recusa sem ativar nada. Um ficheiro anterior a
  esta versão não traz a marca e só se grava pelo USB. A imagem do GitHub tem de trazer a mesma
  versão que o `latest.json`.
- **Código de 1.º arranque**: no primeiro arranque de cada versão, gravada de qualquer forma, um
  ecrã com teclado numérico pede um código de 6 algarismos. Até estar certo, não liga a rede nem os
  sensores, e a saída fica desligada. Depois fica guardado e não volta a pedir nessa versão. Ao fim
  de 3 códigos errados, espera 30 s.
- `POST /api/update/install` e `POST /api/ota` pedem `code=NNNNNN`.
- `tools/release.py` usa sempre `FW_DATE` como data do `latest.json`, confere a marca e escreve no
  terminal os códigos da versão (recusa publicar se as notas os trouxerem).
- Esta instala-se ainda sem o código para instalar (a beta.31 não o pede); as seguintes já o pedem.
