# 22/02/26
# Estados do Nmap

  - O que é Nmap: Nmap(Network Mapper) é uma ferramenta comunmente utilizada por ADMs de rede e pentesters quando 
                o assunto é mapear hosts ativos, portas, serviços, firewalls SOs etc.
    

  - Por que utilizam: O Nmap é uma ferramenta de fácil aprendizado, mas isso não quer dizer que é uma ferramenta limitada, pois
                    ela tem flags(opções) que podem fazer a diferença em diferentes cenários e contextos do usuário.
    

 - O que são serviços: Serviços são programas que seguem regras(protocolos) definidos (ftp,ssh,http) para criar uma meio de
                       comunicação entra o cliente(você) e o servidor(alvo).
   
   Todo serviço segue um protoloco(regra), pois são elas que definem como o serviço deve se comportar em relação a rede e ao
   host(tanto cliente como servidor).
   
     Ex:
      - "porta 22 aberta,serviço ativo rodando(SSH)". a porta do host scaneado está ativa e oferecendo um serviço
         (de meio de comunicação criptografada) relacionado acesso remoto.
         Serviços são essenciáis para o port scanning/fingersprint, já que ambas as opções lidam com respostas dos serviços.
        
   
   - Port Scanning: Scannear portas, interpretar o resultado e decidir o que fazer
   - Fingersprint: Técnica utilizada para descocerrta de versões de serviços,SOs.
                    protocolo do serviço para fazer perguntas, e assim, recebendo a resposta do serviço (versão).
     

- O que são "estados do Nmap": Os estados são as respostas que o Nmap recebe após fazer um scan. elas podem variar conforme
                               a flag(opção) utilizada, regras do firewall do host alvo, porta aberta e porta sem serviço.

- Fluxo de dados do Nmap: Internet → Firewall → Sistema Operacional → Serviço
 
  
   - Internet: Dados que sairam de alguma rede. pode ser qualquer coisa, até mesmo um scan.
   - firewall(host alvo): ele que decide o que fazer com esses dados que chegam da internet. Se ele tem regras que permite
                          o tráfego, ele deixa passar para a próxima camada(SO do host alvo), se não, ele pode bloquear (RST) ou
                          simplesmente ignora (DROP). tudo isso se ele for configurado pra fazer isso, se não, é o SO alvo
                          que responde mandando [RST] ou algum outro aviso de rede.
     
     
   - SO: O sistema operacional é que lida com as portas, se ele permite conexão numa porta = ok, se não, não é possível acessar
         o serviço dela(mas para scanners, o que importa mesmo é saber se tem algo, e não acessar diretamente).
     

- Estados básicos do Nmap:
      - Open: Este estado aparece quando o Nmap scaneia uma porta aberta e percebe que tem um serviço ativo esperando por conexões
              e não tem nada bloquando isso(firewall).
              O Nmap então recebe um (SYN-ACK) do server, que significa que o host respondeu a pergunta(SYN) e está pronto pra
              estabelecer uma conexão(isso varia de acordo com a flag escolhida,fique atento).
  
     - Resumo: Sem firewall bloquando comunicação, host ativo, porta aberta e com serviço esperando conexões.
              

  - Closed: Este estado aparece quando o Nmap scaneia uma porta acessível, mas não tem nenhum serviço esperando por conexões.
      - O host então manda um [RST] para quem tentou se conectar ao serviço na porta x.
    
      - Resumo: Sem firewall bloquando comunicação,host ativo,porta acessível mas sem serviço esperando conexões nela.
                O próprio SO alvo responde o scanner com um [RST]("não é pra essa conexão acontecer, encerrando forçadamente").

   - Filtered: O Nmap recebe este estado quando tem algo bloqueando sua comunicação(host,porta,serviço ou firewall).
                - isso pode significar que pode ter algo no host ou porta, mas não tem nada confirmando isso.
                  É como se fosse um "cara... não tenho certeza de que tem algo aí. pode ter ou não ter nada".
     
   - [!] (tcpwrapped) adcional: aparece quando o Nmap estaberlece conmexão com o host, mas não concegue pegar o banner
                                do serviço a tempo (no -sV e em scripts de detecção).
  
      - Isso ocorre por regras de firewall avançadas
      - IDS ou IPS negando entrega de banner (manda RST antes do nmap pegar o banner)
        
         - [!] pode ser burlado usando detecções mais agressiva do nmap (mandando mais probes, assim tento mais chances de alguma
               passar e pegar a versão dos serviço), como no caso de "scripts de discovery".
         
           
            - sempre combinar -sV e scripts quando não se recebe uma respota do serviço(forçar respotas mandando mais probes).
              
         - [!] mais fácil de detectar, por justamente ter mais tentativas/pacotes an rede.
     
      - Resumo: O Nmap tentou receber uma resposta da host/porta, mas por algo estar bloquando a comunicação ou o nmap
                não recebeu respostas convincentes, ele assume com filtered:
                "não recebi uma resposta convincente do servidor alvo. não vou assumir estado algum, pois pode ter algo,
                 pode não ter ou pode haver algo bloqueando a comunicação(firewall)".

- [dicas]: Sempre lembre disso:
  
    - fluxo nmap: Internet -> Firewall -> Sistema Operacional -> Serviço.
     
    - open = host ativo, porta aberta(tem serviço).
     
    - closed = host ativo, porta acessível(ativo passa a sensação de estar aberto, o que não é verdade).
  
    - filtered = "não tenho informação convincento sobre o host porta. vou assumir como filtered(pode ou não ter algo)".

- [!] Meu projeto de montar uma sub-rede terminou. Se quiser dar uma olhada, o link é este aqui:
      https://github.com/tlmtiger117/Projetos/blob/main/Projeto-Sub_Redes.txt
