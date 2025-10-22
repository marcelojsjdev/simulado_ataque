# simulado_ataque
Desafio DIO - Cyber Security

Desenvolvi conhechimentos de ferramentas e códigos
Como realizar os pentestes utilizando o Kali e Metasploitable, utilizando as ferramentas:
-NMAP
  Comandos:
    nmap -sV -p 21,22,80 <ip_alvo>
    O que faz: Scanea as portas 21,22,80 e tenta mostrar quais as versões do serviço
    
-Criar wordlist
  echo -e "123\n5443\nmsfadmin >pass.txt
  echo -e "msfadmin\nuser\nadmin" >user.txt

-MEDUSA
  comando:
    medusa -h <ip_alvo> -U user.txt -P pass.txt -M ftp -t 6
    O que faz:
      -h: Host
      -U: lista de usuarios
      -P: lista de senha
      -M: Serviço
      -t: Threads
    * Na linha que retornar [SUCCESS] é quando a ferramenta consegue ter acesso ao alvo

-Meduza - Simulando combinações de usuário e senha em sites

1 - Criar uma lista
   Criação de Dicionários: Para um ataque de força bruta, você precisará de:
    Lista de Usuários (user.txt): Um arquivo de texto contendo possíveis nomes de usuário (ex: admin, user, root, msfadmin).
    Lista de Senhas (pass.txt): Um arquivo de texto contendo uma lista de senhas comuns ou esperadas (ex: password, 123456, admin, toor).
2 - Para iniciar o simulado de ataque deve utilizar o comando:
    medusa -h <ENDEREÇO_ALVO> -U <caminho_lista_usuario> -P <caminho_lista_pass> -M http \
    -m PAGE: ‘caminho_da_pagina’ \
    -m FORM: ‘username=^USER^&password=^PASS^&Login=Login’ \
    -m ‘FAIL=Login failed’ -t 6

*Verificar com as variáveis de requisição, exemplo utilizado foram username,password e Login.
  
-Enum4Linux - Enumeração de Serviços SMB/NFS
  Como Usar o Enum4Linux:
  O Enum4Linux é uma ferramenta baseada em linha de comando e geralmente já vem pré-instalada no Kali Linux.
  
  Abrir o Terminal no Kali Linux: Todos os comandos do Enum4Linux serão executados a partir do terminal.
  Identificar o Endereço IP do Alvo: Você precisará do endereço IP da máquina Metasploitable (ou qualquer outra máquina Linux com serviços SMB/NFS ativos) que você deseja enumerar.
  Comandos de Enumeração com Enum4Linux:
  Varredura Básica: Este comando tenta enumerar o máximo de informações possível com as opções padrão.enum4linux <IP_DO_ALVO>
  
  Exemplo: enum4linux 192.168.56.101
  
  Enumeração de Usuários: Para focar na enumeração de usuários.enum4linux -U <IP_DO_ALVO>
  Enumeração de Grupos: Para focar na enumeração de grupos.enum4linux -G <IP_DO_ALVO>
  Enumeração de Compartilhamentos: Para listar os compartilhamentos de rede.enum4linux -S <IP_DO_ALVO>
  Todas as Informações Detalhadas: Para uma enumeração mais exaustiva, combinando várias opções.enum4linux -a <IP_DO_ALVO>

