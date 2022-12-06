3- Especificações  Casos de uso 


Nome : Realizar Cadastro
ID: 001
Objetivo : Coletar dados do usuário que serão usados pelo sistema 
Atores: Consumidores e Administradores

Descrição do Fluxo Principal:
Usuário realiza o primeiro acesso no sistema 
Sistema Apresenta tela inicial 
Usuário  preenche o formulário de cadastro 
Usuário  submete o formulário
Sistema envia e-mail com link de confirmação de criação da conta
Usuário confirma e-mail.
Usuário se torna apto a realizar login
Pré condições 
Usuário não tem acesso ao sistema
Usuário tem email válido 
Pós condições 
Usuário é apto a realizar login 
Disparador 
Botão de ‘Cadastre-se’ na tela inicial do sistema 
Cenário Alternativo 1 - Email do Usuário Já Cadastrado
Usuário já tinha email cadastrado 
Sistema apresenta mensagem ao usuário “Email já cadastrado”
Usuário é encaminhado para o login 



Nome : Solicitar Pedido de Coleta
ID: 002
Objetivo: Disponibilizar dispositivos para o descarte correto 
Atores: Consumidores

Descrição do Fluxo Principal 
Consumidor tem dispositivo(s) que gostaria de descartar corretamente 
Consumidor realiza cadastro 
Sistema apresenta tela de cadastro 
Usuário faz login no app 
Consumidor localiza pontos de coleta em sua cidade e abre o pedido 
Pré condições 
Consumidor tem pontos de coleta em sua cidade 
Consumidor tem conta no app 
Pós condições 
Solicitação é encaminhada para aprovação do administrador
Disparador 
Ação do usuário autenticado e com pontos de coleta nas proximidades
Cenários Alternativo 1 - Usuário Sem Login
Usuário não tem login 
Sistema abre a tela de cadastro
Cenários Alternativo 2 - Sem Pontos De Coletas Próximo
Não existem pontos de coleta próximos ao usuário
O sistema apresenta a mensagem “Infelizmente não existem pontos de coleta nas suas proximidades. Tente Novamente Mais Tarde ”


Nome : Receber moedinhas 
ID: 003
Objetivo : Ser recompensado pela coleta aprovada pelo administrador 
Atores: Consumidores
 
Descrição do Fluxo Principal:
Solicitação de pedido de coleta é aceito pelo administrador 
Sistema credita moedinhas na conta do consumidor 
Pré condições 
Usuário autenticado como cliente fez uma coleta com sucesso
Pós condições 
Usuário recebe quantidade moedinhas respectivas ao dispositivo coletado
Disparador 
Operação de coleta feita com sucesso 
Cenários Alternativos 
Não se aplica
