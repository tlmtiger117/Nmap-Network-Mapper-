# 24/02/26
# Host discovery(Descoberta de hosts)

  O que é: "Host-discovery" é uma técnica utilizada por scanners para mapear dispositivos numa rede (não portas, e sim hosts)
  
   - Como aplicar essa técnica: Utilize a ferramenta de rede Nmap(Network mapper) com as seguintes flags(opções):
   - Comando completo: nmap -vv -PR -sn 192.168.1.0/24
     
     ."-vv": Verbouse, mostra infos extrar do que está contecendo por trás do scan(indispensável, na minha opnião)
       
     ."-PR": Expecifica para o nmap utilizar o ARP-ping(técnica de dedscoberta de hosts em redes LAN) para iniciar o scanner.
       
     ."sn": "no-port-scan", utilizado para scannerar hosts, não portas.
     
     ."192.168.1.": É o endereço sa sua rede. o "0/24" é o limite do hosts do endereço da rede(quantos hosts pode ter na rede).
     
     ."arp -a"(linux): Comando complmentar, mostrar o MAC de dispositivos que você teve contato recentimente.
       ele é temporário, mas muito útil rpa ver quem está se comunicando com você numa rede.
         
       
       
  - [!] Esse "192.168.1.0/24" é o endereço da sua rede, ele pode variar). para confirmar o seu endereço utilize,
        o comando "ip a" e veja o nome da sua interface (Ex: eth0,enp0s3 entre outros). se quiser algo mais explicadinho/resumido,
        tenho um arquivo explicando o fluxo de uma rede/sub rede:
    
  - link: https://github.com/tlmtiger117/docs/blob/main/Fluxo_da_Sub_Rede.md

[Relato]: Descobri isso hoje estudando no meu LAB(rede interna controlada). algo simples(mandar nmap e olhar no wireshark), pode
          revelar coisas que nem pensavamos antes...






          
