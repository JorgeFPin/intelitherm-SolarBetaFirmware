# intelitherm-SolarBetaFirmware
Solar PCB Monitor Beta Firmware

Versões do firmware do **Intelitherm© ESP S3 PLUS Energy Monitor** (Freenove FNK0104B, ESP32-S3,
ecrã de 2,8") para a atualização sem o cabo. Autor: Jorge Pinheiro.

| Placa | Ficheiro |
|---|---|
| FNK0104B 2,8" (sozinha ou na placa base v1.0) | `solar_monitor.ino.bin` |

**Atualizar:** no portal do monitor, *Sistema → Firmware → Procurar atualizações*. O monitor lê o
`latest.json`, descarrega só o ficheiro do seu modelo e confere o tamanho, o SHA-256, o chip e a
marca do modelo antes de o gravar. Também se pode descarregar o `.ino.bin` daqui e enviá-lo no
mesmo cartão (*Enviar ficheiro*). Para instalar é preciso o código da versão.

As versões estão em `firmware/v<versão>/`, com as novidades em `NOTAS.md`. Estes ficheiros são só
a aplicação (0x10000): o registo e as definições ficam. A primeira gravação de uma placa nova faz-se
pelo USB.

Desde a 0.3.0-beta.32, cada versão pede no primeiro arranque um código de ativação, escrito no ecrã
da placa. Até lá a placa não liga a rede, os sensores nem a saída.

Gerado com `firmware/tools/release.py` do repositório do projeto.
