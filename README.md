
TV-PT
============

CANAIS-> PORTUGAL
RÁDIO -> PORTUGAL

REQUERIMENTOS
-----

- [Bash](https://www.gnu.org/software/bash/)
- [mpv](https://mpv.io/)

Se precisar de ajuda, verifique [INSTALAR DEPÊNDENCIAS](#installing-dependencies).


TV
-----

```bash
$ ./TV-PT.SH 
1) RTP 1           7) TVI24              13) SIC Internacional
2) RTP 2           8) RTP Memoria        14) ARTV
3) SIC             9) RTP Madeira        15) Porto Canal
4) TVI            10) RTP Acores         16) Euronews
5) RTP 3          11) RTP Africa         17) Kuriakos TV
6) SIC Noticias   12) RTP Internacional
Qual canal de TV quer ver?
```

RÁDIO
-----

```bash
$ ./RADIO-PT.SH
1) Antena1       6) Kiss FM     11) Orbital     16) RUC
2) Antena2       7) M80         12) Oxigénio    17) Smooth
3) Antena3       8) Mega Hits   13) Radar       18) TSF
4) Cidade FM     9) MEO Music   14) Renascenca  19) Vodafone
5) Comercial    10) Nova Era    15) RFM         20) Zero
Qual canal de RÁDIO quer ver?
```


INSTALAR DEPÊNDENCIAS
-----

```bash
# Debian / Ubuntu
$ apt-get install mpv
```

```bash
# Arch Linux
$ pacman -S mpv
```

```bash
# Mac OS X (two alternatives)
$ brew install mpv
$ port install mpv
```

Como capturar fluxos RTMP
-----

Para isso precisará de `iptables` e `rtmpdump`.

```bash
#redireciona o tráfego RTMP de saída para localhost
$ iptables -t nat -A OUTPUT -p tcp --dport 1935 -j REDIRECT
```

```bash
# iniciar rtmpsrv
$ rtmpsrv
```

Abra uma página da web contendo mídia transmitida por RTMP.
As solicitações RTMP serão capturadas por `iptables` e registradas por `rtmpsrv`.

```bash
#remove o redirecionamento do tráfego RTMP de saída
$ iptables -t nat -D OUTPUT -p tcp --dport 1935 -j REDIRECT
```
