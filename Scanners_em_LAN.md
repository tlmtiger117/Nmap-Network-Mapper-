# 03/03/26
# Scanners em redes LAN

- Ferramenta utilizada: Nmap(netwok-mapper),Wireshark(sniffer/capturador de pacotes de rede).
   - Nmap: Responsável pela simulação do cliente comum e dos atacantes.
   - Wireshark: Responsável pala caça ativa e análise de pacotes de rede.
  
- Flags Nmap utilizadas para o Scanner-em-LAN:
   - -vv: verbouse, mostra infos adcionais em tempo real do que o Nmap está fazendo no momento.
     
   - -PR: ARP-PING, utiliza o portocolo ARP para descobrir hosts na rede LAN, ex:
      - "ip x, se você estiver na minha rede LAN, manda seu MAC pra gente poder trocar dados em LAN (Ethernet)".

   - -sn: no-port-scan: não scaneia portas, mas sim, hosts.
        
   - -n: Sem resolução de domínios. Como isso é totalemnte dispensável nesse contexto, retira-lo deixa o nmap mais rápido
         por naõ precisar fazer algo que não existe em uma camada.

   - T0 a T5: Expecifica o tempo de espera entre cada tentativa de scan(quanto maior o número, menor o tempo de espera entre
              cada tentativa de conexão.

   - --scan-delay: Parecido com o -T, mas muito mais versátil por você mesmo poder expecificar o tempo de espera entre cada
                   conexão(segundos,minutos,horas e até dias).

- Prática: Simulei comportamento padrão de uma pergunta ARP, a de um atacante inesperiente e o de um intermediário.

- ARP-padrão: Não aparce com frequência numa rede, pois os dispositivos já tem uma tabela temporária de "com quem eu já convesei"
              e isso é armazenado na tabela arp, comando(linux):
               - "arp -a".
       
   - Tem somente um ARP request(pergunta) e um reply(reposta).
   - Tamanho dos pacotes: Request(42 bytes), reply(60 bytes), por ter adcionado o seu MAC(payload ao pacote de reposta).
        - Os tamanhos sçao os mesmos nos exemplos seguintes.
   - Tempo: rápido, por ser somente em um host(-n potencializa isso).

- ARP-scan-iniciante:
   - Comando: nmap -PR -sn 192.168.1.0/24
   - Não mostra o por trás do nmap, e ainda por cima, scaneia a rede inteira(isso é claramente um sinal de scan).
   - Não tem --scan-delay(tempo de espera entre uma tentaiva de conexão e outra)m deixa mais claro que é um scanner.
   - [!] Um Sniffer(captura captura pacotes) ou IDS(intrusion Detectaion system) pode alertar que algo está acontecendo na rede.
   - [!] O scanner por já seber o próprio MAC, naõ scaneia a sim mesmo. Isso no tráfego do wireshark, é possível ver um
         "ip pulado", não mostrando o host que fez o scan.

- ARP-scan-intermediário:
   - Comando: nmap -vv -PR -sn --scan-delay 192.168.1.x(ou 192.168.1.x,x1,x2) pra scanerar vários ips expecificados.
   - Mostra o por trás do Nmap.
   - Tem tempo de espera entre tentativas de conexão.
   - [!] Sniffers e IDS tem difuculdades de identificas, mas isso não significa que não possam ser vistos
   - [!] o "ip pulado" acontece aqui também(sempre aocntece quando se trada de ARP-request).

- [resumo]: Sempre vai existir um geito novo de burlar ou de detectar, por isso, é sempre bom estar atualizado e estudando
            sobre "como burlar/testar a invasão" e "como detectar ou miticar os vetores de ataques".
       


     
         
  
   
