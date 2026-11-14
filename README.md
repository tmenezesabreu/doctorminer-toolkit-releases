# Doctor Miner Toolkit

Gerenciamento de mineradoras ASIC para Windows e Linux. Ele encontra as máquinas na rede, mostra a saúde de cada uma, lê os logs e aponta problemas, controla temperatura e corrente, e pede suporte à Doctor Miner com um clique.

## Baixar

Pegue a versão mais recente em **[Releases](../../releases/latest)**:

| Sistema | Arquivo |
|---|---|
| Windows 10/11 (instalador) | `doctor-miner-toolkit-<versão>-windows-x64-setup.exe` |
| Windows (portátil, sem instalar) | `doctor-miner-toolkit-<versão>-windows-x64.exe` |
| Linux x86-64 (Ubuntu 20.04, Debian 11 ou mais novo) | `doctor-miner-toolkit-<versão>-linux-x64.tar.gz` |
| Agente para controladoras ARM (Vnish, Braiins OS) | `doctor-miner-agent-<versão>.tar.gz` |

### Windows

O instalador ainda não é assinado digitalmente, então o Windows pode mostrar "O Windows protegeu o computador". Para instalar, clique em **Mais informações** e depois em **Executar assim mesmo**.

### Agente nas controladoras

O pacote do agente traz os binários ARMv7 e ARM64, o instalador e os scripts de boot. Na controladora, com o código da farm gerado pela NOC:

```bash
tar xzf doctor-miner-agent-*.tar.gz
cd doctor-miner-agent-*/
DM_FARM_CODE=ABCD-EFGH sh install.sh
```

No Braiins OS o agente passa a iniciar com a máquina. No Vnish isso depende do firmware com o agente no pacote; o `LEIAME.md` do pacote explica.

### Linux

```bash
tar xzf doctor-miner-toolkit-*-linux-x64.tar.gz
cd doctor-miner-toolkit-*-linux-x64
./install.sh            # instala para o seu usuário, com atalho no menu (sem sudo)
```

Também dá para abrir sem instalar, com `./doctor-miner-toolkit`.

## O que ele faz

- **Conta Doctor Miner:** entre com login e senha para guardar a configuração no servidor e usá-la em qualquer computador, ou continue sem login.
- **Máquinas:** encontra por faixa de IP as máquinas Antminer com firmware de fábrica, Vnish, Braiins OS, LuxOS e Hashcore, e também Whatsminer e Avalon. Mostra hashrate, consumo, temperatura, placas e ventoinhas.
- **Saúde:** marca a máquina que precisa de atenção e diz por quê. Lê os logs da própria máquina e aponta placa sem chips, falha de ventoinha, quedas de pool e reinícios.
- **Linha do tempo:** guarda para cada máquina os reinícios, quedas, ocorrências nos logs e operações feitas.
- **Mesmo modelo:** compara cada máquina com as outras do mesmo modelo, considerando o perfil de potência de cada uma.
- **Mudanças fora do app:** avisa quando pool, throttle, alvo de potência ou firmware muda sem ter sido pelo app. Troca de pool é a marca clássica de malware em ASIC.
- **Controles automáticos:** temperatura (só reduz acima de 80 °C por padrão) e corrente pelo disjuntor. Vêm desligados.
- **Dispositivos:** tomadas, relés, disjuntores Wi-Fi e sensores Shelly, Tasmota e Tuya, com busca automática na rede.
- **Pools da conta:** até 5 pools guardadas na conta, pools recomendadas e opção de manter as pools nas máquinas.
- **Planejador:** cabos, circuitos e potência em frases, e possibilidades de compra para o valor que você quer investir.
- **Agente da farm:** com o código que a NOC da Doctor Miner passa, o computador vira o agente da farm e a NOC opera tudo remotamente (aba "Código da farm" na tela inicial).
- **Agente nas controladoras:** o mesmo agente, sem janela, roda na controladora da própria mineradora; vários agentes na mesma farm se revezam, e um assume se o outro parar.
- **Suporte:** monta um pacote com tudo o que o técnico precisa e envia à Doctor Miner. No plano gerenciado, a NOC da Doctor Miner acompanha e opera a farm pelo computador em que você permitir.
- **Telegram:** alertas e resumo diário da farm.

As regras e os controles funcionam só com o app aberto.
