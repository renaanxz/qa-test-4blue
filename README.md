# Teste técnico QA - 4blue

# Objetivo
Realizar testes exploratórios em um microssistema web contendo:
- Tela de login
- Tela de criação de conta
- Tela de sucesso

# E ao final, responder: 
Quais 2 bugs você corrigiria primeiro e por quê?
Caso tenha, coloque suas sugestões de melhorias para essas telas.

Durante os testes foram analisados:
- Bugs funcionais
- Problemas de experiência do usuário (UX)
- Falhas de segurança

# Sistema testado
https://qa-play-sim.lovable.app/

# Estratégia de Teste
Foi utilizada a abordagem de **Testes Exploratórios**, simulando comportamentos reais de usuários

Os testes incluíram:
- Validação de campos obrigatórios
- Testes com dados inválidos
- Testes de segurança básica
- Testes de navegação
- Testes de experiência do usuário

# Ambiente de Teste
Sistema Operacional: Windows 10
Navegador: Google Chrome
Versão: 145.0.7632.160


# RT001 - TELA DE LOGIN


## BUGS FUNCIONAIS

### CT001
Mensagem de erro inesperada exibida mesmo após login bem-sucedido

### Descrição
Ao realizar login com sucesso, o sistema exibe uma mensagem de erro ("Erro inesperado") no canto inferior direito da tela, apesar do login ter sido concluído corretamente.

### Passos para reproduzir
1. Acessar a tela de Login
2. Inserir credenciais válidas
3. Clicar em Login

### Resultado Atual
Login ocorre normalmente, mas aparece uma mensagem de erro no canto inferior direito.

### Vídeo de reprodução do Bug:
https://www.loom.com/share/e001d4e3c9e44328b361cd4cf619ca10

### Resultado Esperado
Após login bem-sucedido, nenhuma mensagem de erro deveria ser exibida.

### Severidade
Médio

### Prioridade
Alta


### CT002
Botão de Login permite múltiplos cliques durante processamento da requisição

### Descrição
Durante a tentantiva de login com credenciais incorretas, o botão "Entrar" exibe o estado de carregamento ("Entrando..."), porém continua clicável, permitindo que o usuário clique várias vezes e dispare múltiplas requisições de login.

### Passos para reproduzir
1. Acessar a tela de Login
2. Inserir email e/ou senha inválido
3. Clicar no botão "Entrar"
4. Enquanto aparece o status "Entrando...", clicar repetidamente no botão

### Resultado Atual
O botão continua clicável durante o processamento e o sistema dispara múltiplas tentativas de login, resultando em vários pop-ups de erro.

### Vídeo de reprodução do Bug:
https://www.loom.com/share/0aff0fa470c149cfba97598982326d6d

### Resultado Esperado
O botão "Entrar" deveria ser desativado imediatamente após o primeiro clique, permanecendo bloqueado até que o sistema finalize a requisição e apresente a resposta.

### Severidade
Média

### Prioridade
Alta


## PROBLEMAS DE EXPERIÊNCIA DO USUÁRIO (UX)


### CT003
Ausência de opção para visualizar senha durante o Login

### Descrição
Durante o processo de login, não existe opção para visualizar a senha digitada. Isso pode dificuldade a digitação correta da senha caso o usuário cometa algume erro.

### Passos para reproduzir
1. Acessar a tela de Login
2. Inserir qualquer valor no campo senha
3. Verificar se existe opção para mostrar senha

### Resultado Atual
A senha permanece oculta e não existe opção para visualiá-la.

### Resultado Esperado
O sistema deveria oferecer um botão para alternar entre mostrar e ocultar senha.

### Severidade
Baixo

### Prioridade
Baixa


### CT004
Login com senha incorreta não apresenta mensagem clara

### Descrição
Quando o usuário insere uma senha incorreta, o sistema não apresenta uma mensagem clara explicando o erro.

### Passos para reproduzir
1. Acessar a tela de Login
2. Inserir email válido
3. Inserir senha incorreta
4. Clicar em "Entrar"

### Resultado Atual
O sistema apresenta mensagem padrão ("Conta não encontrada. Crie uma conta primeiro.")

### Vídeo de reprodução do Bug:
https://www.loom.com/share/f446e2e58fb5407f82303b814cb3852f

### Resultado Esperado
O sistema deveria exibir mensagem clara como:
"Email ou senha incorretos."

### Severidade
Média

### Prioridade
Média


## FALHAS DE SEGURANÇA

### CT005
Campos de Login aceitam qualquer tipo de caractere e textos extremamentes longos

### Descrição
Os campos de email e senha aceitam qualquer tipo de caractere e não possuem limite de caracteres, permitindo inserção de dados inválidos ou extremamente longos.

### Passos para reproduzir
1. Acessar a tela de Login
2. Inserir valores como: 
@@@@
aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa

### Resultado Atual
O sistema aceita qualquer valor inserido.

### Resultado Esperado
Os campos deveriam validar os dados e possuir limite de caracteres.

### Severidade
Médio

### Prioridade
Média


### CT006
Login com espaços antes ou depois do email

### Descrição
O sistema permite tentativa de login quando o email contém espaços antes ou depois do texto, podendo causar inconsistências na autenticação.

### Passos para reproduzir
1. Acessar a tela de Login
2. No campo email, digitar: " usuario@email.com " (com espaço antes e depois)
3. Inserir a senha correta
4. Clicar em Entrar

### Resultado Atual
O sistema processa o login sem remover automaticamente os espaços.

### Resultado Esperado
O sistema deveria remover automaticamente espaços antes ou depois do email ou impedir o envio do formulário.

### Severidade
Média

### Prioridade
Média


### CT007
Login sensível a letras maiúsculas no email

### Descrição
O sistema diferencia letras maiúsculas e minúsculas no campo de email durante o login.

### Passos para reproduzir
1. Acessar a tela de Login
2. Inserir o email cadastrado em letras maiúsculas ou misturadas
Exemplo: USUARIO@email.com
3. Inserir a senha correta
4. Clicar em Entrar

### Resultado Atual
O sistema não reconhece o email e impede o login.

### Resultado Esperado
O sistema deveria tratar o email como case-insensitive, permitindo login independentemente de letras maiúsculas ou minúsculas.

### Severidade
Média

### Prioridade
Alta


# RT002 - TELA DE CADASTRO


## BUGS FUNCIONAIS

### CT008
Sistema permite criação de contas duplicadas

### Descrição
O sistema permite criar múltiplas contas utilizando o mesmo email.

### Passos para reproduzir
1. Criar uma conta com determinado email
2. Acessar novamente a tela de cadastro
3. Inserir os mesmos dados
4. Criar nova conta

### Resultado Atual
A conta é criada novamente com o mesmo email.

### Vídeo de reprodução do Bug:
https://www.loom.com/share/c55752e41044418292b55a4d1e228d2c

### Resultado Esperado
O sistema deveria impedir a criação de contas duplicadas

### Severidade
Alto

### Prioridade
Alta


### CT009
Sistema permite criação de conta com campos vazios

### Descrição
O sistema permite criar conta mesmo quando os campos não são preenchidos.

### Passos para reproduzir
1. Acessar a tela de cadastro
2. Inserir apenas espaços nos campos ou deixar em branco
3. Criar conta

### Resultado Atual
A conta é criada mesmo sem dados válidos.

### Vídeo de reprodução do Bug:
https://www.loom.com/share/a9f713dde0f940f08c846d2dea165f6b

### Resultado Esperado
O sistema deveria validar os campos obrigatórios.

### Severidade
Alto

### Prioridade
Alta


### CT010
Campo confirmar senha não valida igualdade

### Descrição
O sistema permite prosseguir com o cadastro mesmo quando os campos senha e confirmar senha possuem valores diferentes.

### Passos para reproduzir
1. Acessar a tela de cadastro
2. Preencher todos os campos
3. Inserir senha: 123456
4. Inserir confirmar senha: 654321
5. Clicar em "Criar conta"

### Resultado Atual
O sistema aceita o cadastro mesmo com senhas diferentes.

### Vídeo de reprodução do Bug:
https://www.loom.com/share/cdf38f751dd74e8fa6572d7f6152b1dc

### Resultado Esperado
O sistema deveria impedir o cadastro e exibir mensagem:
"As senhas não coincidem."

### Severidade
Alta

### Prioridade
Alta



## PROBLEMAS DE EXPERIÊNCIA DO USUÁRIO (UX) 

### CT011
Ausência de opção para visualizar senha durante cadastro

### Descrição
Durante o processo de cadastro, não existe opção para visualizar a senha digitada, o que pode dificultar o preenchimento correto.

### Passos para reproduzir
1. Acessar a tela de cadastro
2. Inserir valores no campo senha

### Resultado Atual
A senha permanece oculta sem opção de visualização.

### Resultado Esperado
O sistema deveria permitir alternar entre mostrar e ocultar senha.

### Severidade
Baixo

### Prioridade
Baixa


### CT012
Não existe indicador de força da senha

### Descrição
O sistema não apresenta indicador visual que informe ao usuário se a senha criada é fraca ou forte.

### Passos para reproduzir
1. Acessar a tela de cadastro
2. Inserir uma senha simples como 123456

### Resultado Atual
O sistema não apresenta nenhuma indicação sobre a segurança da senha.

### Resultado Esperado
O sistema deveria exibir um indicador de força da senha (fraca, média, forte).

### Severidade
Baixa

### Prioridade
Baixa


### CT013
Campos não indicam obrigatoriedade

### Descrição
Os campos do formulário não indicam quais são obrigatórios para preenchimento.

### Passos para reproduzir
1. Acessar a tela de cadastro
2. Observar os campos do formulário

### Resultado Atual
O sistema não indica quais campos são obrigatórios.

### Resultado Esperado
Os campos obrigatórios deveriam possuir indicação visual (exemplo: * ou mensagem).

### Severidade
Baixa

### Prioridade
Baixa


## FALHAS DE SEGURANÇA

### CT014
Campo nome aceita qualquer tipo de caractere

### Descrição
O campo nome aceita números e caracteres especiais sem validação.

### Passos para reproduzir
1. Acessar a tela de cadastro
2. Inserir valores no campo nome como:
123@@@###

### Resultado Atual
O sistema aceita o valor inserido

### Resultado Esperado
O campo deveria aceitar apenas letras ou formatos válidos.

### Severidade
Médio

### Prioridade
Média


### CT015
Campo telefone aceita qualquer formato

### Descrição
O campo telefone aceita letras e caracteres especiais.

### Passos para reproduzir
1. Acessar a tela de cadastro
2. Inserir valores no campo telefone como:
abcde
@@@@
123abc

### Resultado Atual
O sistema aceita o valor inserido

### Resultado Esperado
O campo deveria aceitar apenas números com formato válido

### Severidade
Médio

### Prioridade
Média


### CT016
Campo email aceita formato inválido

### Descrição
O campo email aceita valores que não correspondem a um formato válido de email.

### Passos para reproduzir
1. Acessar a tela de cadastro
2. Inserir valores no campo email como:
teste
teste@
@email
123456

### Resultado Atual
O sistema aceita o email inválido.

### Resultado Esperado
O sistema deveria validar o formato correto de email.

### Severidade
Alto

### Prioridade
Alta


### CT017
Campos senha aceitam valores extremamente fracos

### Descrição
Os campos de senha não possuem critérios mínimos de segurança.

### Passos para reproduzir
1. Acessar a tela de cadastro
2. Inserir senhas como: 
1
123
abc

### Resultado Atual
Conta criada com senha fraca.

### Resultado Esperado
O sistema deveria exigir critérios mínimos de segurança.

### Severidade
Alto

### Prioridade
Alta


### CT018
Campos do formulário não possuem limite de caracteres

### Descrição
Os campos permitem inserção de textos extremamente longos.

### Passos para reproduzir
1. Acessar a tela de cadastro
2. Inserir texto muito longo em qualquer campo

### Resultado Atual
O sistema aceita valores sem limite.

### Resultado Esperado
Os campos deveriam possuir limite de caracteres apropriado.

### Severidade
Alto

### Prioridade
Alta


### CT019
Sistema permite colar senha diferente no campo confirmar senha sem alerta

### Descrição
O sistema permite colar uma senha diferente no campo confirmar senha sem realizar validação imediata.

### Passos para reproduzir
1. Acessar a tela de cadastro
2. Inserir senha: senha123
3. Colar outra senha no campo confirmar senha
4. Continuar preenchendo o formulário

### Resultado Atual
O sistema não alerta imediatamente que as senhas são diferentes.

### Resultado Esperado
O sistema deveria validar automaticamente e alertar quando as senhas forem diferentes.

### Severidade
Alta

### Prioridade
Alta


### CT020
Cadastro permite email com letras maiúsculas criando duplicidade

### Descrição
O sistema permite cadastrar contas duplicadas utilizando variações de maiúsculas no email.

### Passos para reproduzir
1. Acessar a tela de cadastro
2. Criar conta com email: usuario@email.com
3. Tentar criar nova conta com: Usuario@email.com

### Resultado Atual
O sistema permite a criação de duas contas diferentes.

### Resultado Esperado
O sistema deveria normalizar o email e impedir duplicidade.

### Severidade
Alta

### Prioridade
Alta



# RT003 - TELA SIMPLES DE SUCESSO


## PROBLEMAS DE EXPERIÊNCIA DO USUÁRIO (UX) 

### CT021
Tela pós-login apresenta apenas a opção ''Sair da conta''

### Descrição
Após realizar login com sucesso, a tela exibida apresenta apenas um botão de "Sair da Conta", sem outras funcionalidades para o usuário.

### Passos para reproduzir
1. Acessar a tela de Login
2. Realizar login com credenciais válidas
3. Aguardar redirecionamento

### Resultado Atual
A tela apresenta apenas o botão Sair da Conta, sem outra funcionalidade.

### Vídeo de reprodução do Bug:
https://www.loom.com/share/e75c59a5ef124b73a774cc5f8b44efd9

### Resultado Esperado
A tela deveria apresentar outras funcionalidades e informações adicionais ao usuário logado.

### Severidade
Baixo

### Prioridade
Baixa


# 1. Quais 2 bugs você corrigiria primeiro e por quê?
  # CT010 - Campo confirmar senha não valida igualdade
  Pois permite que usuários se cadastrem com senhas diferentes, comprometendo o funcionamento básico do cadastro e podendo impedir o login posterior.
  
  # CT020 - Cadastro permite email com letras maiúsculas criando duplicidade
  Pois isso pode gerar múltiplas contas para o mesmo usuário e causar inconsistências na base de dados do sistema.
  
# 2. Caso tenha, coloque suas sugestões de melhorias para essas telas.
  - Adicionar um indicador visual que informe ao usuário se a senha criada é fraca, média ou forte, incentivando a criação de senhas mais seguras.
  - Incluir um ícone para mostrar ou ocultar a senha nos campos de senha durante o login e cadastro, facilitando a verificação do que foi digitado pelo usuário.
  - Melhorar validações dos campos do formulário, aceitando apenas formatos adequados
  - Indicar campos obrigatórios, como asterisco (*) ou mensagens de validação
  - Desabilitar botões durante requisições ("Entrar" ou "Cadastrar")
  - Melhorar feedback ao usuário, permitindo que todas as mensagens de erro sejam claras e objetivas
  - Padronizar tratamento de emails, removendo espaços extras e tratando letras maiúsculas e minúsculas da mesma forma, evitando problemas de autenticação e duplicidade de contas.
