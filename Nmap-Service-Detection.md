# 16/04/26
# Service-detection:

- Service-detection: Técnica utilizada para tentar descobrir informações de serviços (inclui scans e outras sub-técnicas).

- -sV: Service-detection, utiliza probes específicas para descobrir versões de serviços.
       manda probes específicas para detecção de serviço até alguma revelar a versão dele
  
   - Banner: cabeçalho, é onde mostra infos essenciais na tentativa de conexão no serviço
      (src,dst,sport,dport,payload,versão do programa utilizado por um servido acessado...)

- Flags auxiliares na detecção de serviço:
- [!] "nmap-service-probes": o arquivo que fica na instalação do nmap que contem toda a base de probes utilizada pelo -sV
  
   - 1° "--version-intensity<1 a 9>":
      - permite ajustar a intencidade de probes enviadas para a detecçaõ da versão do serviço.
      - padrão do nmap é 7 probes por tentativa de detecção da versão serviço.

    - 2° "--script=*discovery*": utiliza scripts de de deescoberta de informações para tentarm identificar a versão do programa
          utilizado pelo serviço.
      
    - 3° "-sV --version-all": o "Brute-force" das probes de detecção de versões de programas.
       - utiliza todas as probes de detecção do banco de probes do nmap (nmap-service-probes) para tentar identificar a versão
         do programa utilizado pelo serviço
         
    - 4° "--script banner": script focado em tenatr pegar o banner de serviços. não tenta comparar com o seu banco de probes
          inteligentes (-sV), mas sim, tenta pegar qualquer info que o serviço retorne para o scanner.

       - -sV: probes inteligentes, manda conforme o serviço scaneado(ssh = probes ssh, ftp = probes ftp...)
       - --script banner: "mando o pacote e pego o que o server me mandar espontânamente".
         

- [!] tem  outras opções, e elas estão em: "/usr/share/nmap/scripts/" ou em algo nesse sentido(pode variar conforme a distro/SO)


