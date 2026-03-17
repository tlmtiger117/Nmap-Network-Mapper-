# 16/03/26
# --Packet-Trace

- O que é: É uma flag do Nmap onde sua função é basicamente mostrar todo tráfego geredo pela ferramenta. Isso inclui:

  
- Seu diferencial: Essa flag é tipo um "snnifer interno" do Nmap, pois mostra TODOS os pacotes enviados e recebidos
                   durante a execução da tool com alguns detalhes adcionais relacionados ao scanner.
  

- Detalhes que aparecem ao usar o comando:
  
   - Pacote enviado e recebido (SENT/RECV)
     
   - Protocolo utilizado
     
   - Porta de envio e destino
     
   - Flags TCP da comunicação(SYN,SYN-ACK,ACK...)
     
   - TTL(Time-to-life): Por quantos Roteadores o pacote pode passar antes de ser descartado
     
   - MSS(Maximum Segment Size): Partes expecíficas do pacote TCP(Flags,Portas,mss,window,payload,id...)
     
   - win/window: Máximo de tamanho de dados que o host pode receber durante a comunicação(antes e depois de um ACK).
 
   - seq: número que identifica a posição dos dados na conexão TCP
      - Ordena os pacotes(entrega na ordem certa)
      - Detecta perdas(algum MSS do pacote)
      - retransmitir dados corretamente(mandou, não respondeu, mandou de novo)
     
   - id: Endereço do pacote IP(PROTO-IP). Responsável por reconstruir pacotes de envio Fragmentados(ou ao menos, saber de quem é).
     
   - iplen: Tamanho do conteúdo transportado pelo pacote ip(header IP,header TCP, payload)
     
   - [?] Header: Dados princiapis do pacote(quem envia,recebe,estado do pacote,ttl(IP),Flags,payload,porta(no TCP)...

     
- Outras flags do Nmap que eu achei interessante aqui nesse outro arquivo:
   - [https://github.com/tlmtiger117/Ideias/blob/main/Flags_Nmap.md]
 




  
