# 04/03/26
# Paralelismo Nmap(Conexões e Probes simultâneas)

# Nmap(Network-Mapper): Scanner de rede utilizado para descoberta de host,SO,portas,serviços e firewalls.

- O que é paralellismo:Paralelismo nada mais é do que 2 ou mais coisas acontecendo ao mesmo tempo(nesse contexto, os scans)

- Flag-Nmap(sinal):--max-parallelism<n>

   - Define quantas Probes ou conexões o nmap irá executar simuntâneamente(ao mesmo tempo).
   - É ajustável, ou seja, o usuário que define quantas conexões ou Probes ele vai querer.

- O que são conexões e Probes:
  
   - Conexões: É o momento em que um cliente(user) estabelece conexão com um server para mandar e receber dados.
      - Para isso, ele precisa passar pelo HAND-SHAKE do TCP(manda pergunta, server responde, cliente confirma conexão).

   - Probes: É uma pacote utilizado simplsmente para testar a reação de um host,porta ou firewall.
      - Ele não completa o HAND-SHAKE, apenas manda o pacote, recebe a respota e recusa estabelecer conexão com o server.

- [DICAS]: Sempre tenha cuidado ao expecificar vários alvos(hosts ou portas), pois isso pode acabar perdendo pacotes.
          Isso aconteceu comigo quando usei espaçamento na hora de expecificas 2 portas(nunca façam isso),pois o nmap interpreta 
          esse espaçamento como um outro alvo(host ou porta).


          
  


