# 15/04/26
# Comandos alternativos para Host-Discovery

- Host-Discovery: Técnica de enviar probes (pacotes de testes) para receber alguma reação que prove que o host está ativo.
   - Essa técnica não é "port-scanning"(não manda pacotes para portas), mas sim para a tabela tcp do host (lida com conexões).

- Fases de scan do Nmap: O Nmap utiliza pacotes específicos apra cada parte do scan (host,portas,serviços,firewall.SO)
   - O fluxo seria assim:
     
      - 1° Host-discovery: Manda pacotes específficos para testar a reação do host
           (manda pacotes na porta para receber uma resposta do host)
     
      - 2° Port-Scanin: Manda pacotes específicos para a porta com a intenção de interpretar o estado dela
                        (open, closed, filtered...)
        
      - 3° Service-Detection: Manda pacotes específicos para tentar descobrir a versão de um programa utilizado por um serviço
                              na porta do host alvo (programa = quem interpreta os dados enviados e recebidos na comunicação).
        
      - 4° OS-Detection: Tenta descobrir o SO do alvo (útil quando se descobre um CVE, mas precisa ver se o SO bate com tipo
                         da falha). falhas windows talvez não funcionem em falhas linux/unix.



-  Host-Discovery (Descoberta de hosts/dispositivos).
-  [!] Os comandos abaixo deve ser utilizados em ultimo caso, quando o host não reponde normalmente.
  
   - nmap -PE alvo
      - ICMP Echo (ping tradicional) → verifica se o host responde a ping
        
   - nmap -PP alvo
      - ICMP Timestamp → pergunta o horário do host (às vezes passa quando ping é bloqueado)
        
   - nmap -PM alvo
      - ICMP Netmask → pergunta a máscara de rede (legado, raro hoje)
        
   - nmap -PS80,443 alvo
      - TCP SYN ping → envia SYN para portas específicas e usa a resposta como prova de vida
        
   - nmap -PA80,443 alvo
      - TCP ACK ping → envia ACK “inesperado”, útil contra firewall stateful
        
   - nmap -PU53,161 alvo
      - UDP ping → usa resposta ICMP (port unreachable) pra detectar host ativo
        
   - nmap -PR 192.168.0.0/24
      - ARP scan → descobre hosts na LAN via MAC address (mais confiável em rede local)
        
   - nmap -PE -PP -PS80,443 -PA443 -PU53 alvo
      - Combinação de probes → aumenta chance de resposta usando múltiplos métodos
        
   - nmap -Pn alvo
      - Ignora host discovery → assume que o host está ativo
     
   - Extras úteis
      - nmap -PS22,80,443,3389 alvo
         - SYN ping em portas comuns → melhora taxa de acerto
           
     - nmap -PA443 alvo
        - ACK focado → útil quando SYN é bloqueado
          
     - nmap -PU53 alvo
        - UDP em DNS → comum gerar resposta mesmo com filtros



      


