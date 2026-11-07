## 0.3.0-beta.33 — 2026-11-07

Pedidos do Jorge: a bateria interna dizia "a carregar" sem cabo, e no repositório público só
ficam versões protegidas com o código de 1.º arranque.

- **Bateria interna (correção):** a placa ficou 21 h em "USB, a carregar" enquanto descarregava
  (4150 → 3770 mV). Tinha arrancado com a bateria cheia e sem cabo, e a regra presumia o
  carregador acima de 4,15 V. A descida só a tirava daí acima de 1,5 mV/min, e esta placa desce
  ~0,8 mV/min. Agora:
  - sem PC, arranca sempre em **bateria**; o carregador de parede vê-se pelo salto da tensão ao
    ligar (ou ao voltar a carregar);
  - o histórico guarda a **média de cada minuto**, e a tendência vê descidas de uma fração de
    mV/min;
  - **"a carregar"** só com a tensão a não descer (mais de 0,3 mV/min a descer: a carga acabou ou
    já não há USB);
  - abaixo de 4,00 V, com o USB presumido e a tensão a não subir, passa a **bateria** (com USB, o
    TP4054 está a carregar e a tensão sobe sempre);
  - a tendência só conta os minutos depois do último salto ou mudança, por isso ligar o
    carregador com a bateria a descer não volta logo a "bateria".
  - Novo em `tests/lipo_test.cpp`: o caso da placa do Jorge, o carregador ligado a meio da
    descarga, o cabo tirado sem salto e o dente de serra com a carga terminada.
  - Ao arrancar no carregador com a bateria cheia, mostra "bateria" até o TP4054 voltar a
    carregar.
- As versões 0.3.0-beta.27 a beta.31, sem essa proteção, saíram do repositório público. Fica a
  partir da beta.32.
- **Marca da proteção** `FW_BOOT_MARK` (`[[Intelitherm-BOOTCODE=1]]`, em `config.h`): só existe
  no firmware com o código de 1.º arranque. `tools/release.py` recusa publicar um ficheiro sem ela.
