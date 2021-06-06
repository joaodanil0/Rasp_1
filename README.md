# Configuração do USB serial raspberry pi 3 b

## Dispositivos utilizados
 - [X] Placa FTDI FT232RL Conversor USB Serial - [link](https://www.filipeflop.com/produto/placa-ftdi-ft232rl-conversor-usb-serial/)

## Conexões

## Imagem utilizada
- [X] raspios-buster-armhf-lite - [link](https://downloads.raspberrypi.org/raspios_lite_armhf_latest)

## Passos

1. Flashar a imagem do raspios no cartão SD
2. Depois de flashado, o cartão SD terá 2 partições (**/boot** e o **/rootfs**), execute os passos a seguir ainda com o cartão SD no computador.
3. Na partição **/boot**, abra o arquivo *config.txt* e adicione no final do arquivo
> enable_uart=1
4. Ainda na partição **/boot**, abra o arquivo *cmdline.txt* e verifique se existe o trecho abaixo
> console=serial0,115200 console=tty1 

5. Remova o cartão e coloque no raspberry (*não ligue o raspberry ainda*)

6. No terminal linux, é necessário descobrir qual porta USB o *FTDI FT232RL* está associado. Antes de plugar o *FTDI FT232RL* na porta usb, rode o camando
> ls /dev/ttyUSB*

verifique o resultado.

Agora plugue o *FTDI FT232RL* e rode o comando acima novamente, o novo ttyUSB**x** que aparecer é o do *FTDI FT232RL*. No meu caso é o **/dev/ttyUSB0**.

7. Agora rode o camando
> cat /dev/ttyUSB0

Talvez o ~~sudo~~ seja nessário

8. Ligue a raspberry e as linhas do kernel devem aparecer até o momento de login.