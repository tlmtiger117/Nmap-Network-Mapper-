# 05/03/26
# Scan-delay no Nmap


- Ferramentas: Nmap(netwok mapper), wireshark(sniffer de pacotes).
   - Nmap: Scanner de rede, utilisado para descobrir infosmações numa rede
   - Wireshark: Scniffer("capturador de pacotes"), consegue ver todo tráfego que está passando pela rede.


- Flag Nmap: --scan-delay
   - Função: Cria um tempo de espera entre cada scan feito pelo nmap, ex:
      "Scannear 2 portas, mas a cada conexão/Probe terminada, esperar 'x' tempo para a próxima conexão/Probe."
     
   - Essa opção te permite expecificar o tempo exato de espera do scanner (Horas, minutos, segundos e milisegundos).
     
   - Utilizada Diminuir a velocidade entre cada conexão/Probe, dificultado correlacionar um scan a um comportamento suspeito.
     
   - Se combinar-mos com outras opções como --max-parallelism(como já mostrei antes), fica ainda mais difícil diferenciar
      comportamento padrão de scan.
     
   - [link para meu estudo de paralelismo]: https://github.com/tlmtiger117/Nmap-Network-Mapper-/blob/main/Nmap_Paralelismo.md
     

- Como detectar esse tipo de scan:
   - 1° Teste o comportamento da tool(utilise ela e observer seu comportamento padrão)
   - 2° Tamanho de pacotes, isso entrega muito, pois o nmap sempre utiliza os mesmos tamanhos de pacotes.
   - 3° Flags diferentes: O Nmap tem flags diferentes, por isso, sempre testar as mais comuns (-sS,-sT,-sA) para entender
         como elas recebem respostas do host, por que o host entrega "x" repostas e como detectar esse tipo de
         comportamento(Wireshark pra analise em tempo real de pacotes) e firewall pra testar regras expecíficas pra isso.
     

- [Dica]: Percebi que pode ser interessante indetificas as camadas onde cada tipo de scan atua(modelo OSI) pra entender
           onde o scan começa e onde ele deve terminar(isso ajuda a entender onde você está errando).


  
