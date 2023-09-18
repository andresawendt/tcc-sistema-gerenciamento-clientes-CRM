# sistemaGerenciamentoClientes_CRM
Análise de requisitos para a construção de um sistema de gerenciamento de clientes - parte 1 do Projeto Integrador do Curso Técnico de Desenvolvimento de Sistemas do SENAC.

## 1. APRESENTAÇÃO
O objetivo principal desse projeto é apresentar e documentar uma proposta de desenvolvimento de uma ferramenta para gerenciamento de clientes de um Centro de Empreendedorismo e Inovação.

## 2. DESCRIÇÃO DO PROJETO
  O Centro de Empreendedorismo e Inovação trabalha com soluções inovadoras para a bioeconomia amazônica. São 3 os principais produtos do Centro: Programa Germinar, Programa Florescer e o Programa Frutificar. Todos os produtos são trilhas de desenvolvimento e aceleração inovadora e empreendedora que tem como principais clientes grandes e médias empresas. 
  Hoje, a gestão dos dados e informações desses clientes é feita em diferentes abas de uma planilha no Excel, o que tem gerado uma série de problemas, dado as limitações da ferramenta. Utilizando uma lógica de funil de vendas, os vendedores registram na tabela os potenciais clientes que representam uma oportunidade de venda. A partir disso, a gestão e acompanhamento dessa oportunidade é feita pela atualização de uma coluna na tabela do registro que identifica o momento do funil de vendas no qual a oportunidade está.  O funil de vendas é a representação do processo comercial da empresa, e este é dividido em quatro etapas:
    Etapa 1 - Oportunidade: os dados do potencial cliente são cadastrados na planilha e o mesmo é identificado como oportunidade.
    Etapa 2 - Contato realizado: momento em que foi feito um primeiro contato com a oportunidade.
    Etapa 3 - Envio de orçamento: momento em que após o contato feito, a oportunidade recebe um orçamento do produto que deseja adquirir.
    Etapa 4 - Venda efetivada: momento em que a oportunidade aceita o orçamento e efetiva a compra, tornando-se um cliente.
  Cada uma dessas etapas é uma opção de seleção no campo “Status” da tabela no Excel. Durante o processo de vendas, a oportunidade pode demonstrar desinteresse em dar continuidade na compra, e quando isso acontece, a coluna de status no registro da mesma, é atualizada para “perda”.
  Cada oportunidade tem um vendedor responsável que irá fazer o seu acompanhamento, contudo, o processo comercial tem um único gerente. O gerente, por sua vez, é quem acompanhará o funil de vendas, uma vez que é ele o responsável por identificar oportunidades de melhoria nas etapas do processo. Além disso, é responsabilidade do gerente também, elaborar relatórios mensais de resultado para a diretoria. Atualmente, para elaborar os relatórios o gerente leva bastante tempo para poder cruzar os dados e manipulá-los para evitar duplicidade de informações, contudo, dada as limitações da ferramenta utilizada, é frequente a falta de integridade de alguns dados, o que compromete parcialmente os resultados. 
  Buscando resolver esse problema e facilitar o acesso às informações sobre o processo comercial, a equipe de Dados e Sistemas do CEV, está planejando o desenvolvimento de um Sistema de Gerenciamento de Clientes.  Esse sistema terá um banco de dados relacional para armazenar e gerenciar todas as informações dos clientes e produtos comercializados. Ao longo deste documento, será detalhado o planejamento desse sistema, englobando desde o uso do banco de dados relacional para armazenamento dos dados até as funcionalidades que estarão disponíveis para os usuários nessa versão 1.0 do sistema. 

## 3. DESCRIÇÃO DOS USUÁRIOS
Os usuários do sistema se dividem em três grupos:
- Administrador do Banco de Dados (DBA): Possui acesso a todas as configurações do sistema, sendo responsável por estruturar os bancos de dados, administrar os dados e conceder permissões de acesso aos usuários. 
- Gerente: É o responsável pela gestão e acompanhamento do processo comercial. Para isso, necessita otimizar a coleta de dados que o ajudem a identificar oportunidades de melhoria e acompanhar resultados. 
- Vendedor: É o responsável por cadastrar oportunidades, contatá-las e convertê-las em clientes. O vendedor é quem realiza o acompanhamento das oportunidades ao longo do funil de vendas.

## 4. NECESSIDADES OBSERVADAS E REGRAS DE NEGÓCIO
Algumas necessidades e regras de negócio identificadas no levantamento de requisitos para construção do sistema:
Junto de cada cadastro, deve ser armazenado o histórico do cliente no funil comercial.
As vendas são B2B, por isso é necessário que na solicitação de dados de cadastro do cliente, seja solicitado o ponto focal de contato na empresa. 
O sistema deve permitir que possam ser aplicados filtros de busca para possíveis agrupamentos, como por exemplo, filtrar apenas os contatos que tenham seu status como “Contato realizado”. 

## 5. REQUISITOS FUNCIONAIS
Foi realizado um levantamento dos requisitos funcionais que o sistema deve possuir. São esses:
## [RF001] Autenticar usuários 
Ator: Gerentes e Vendedores
Descrição: O sistema deverá apresentar uma tela inicial que solicitará ao usuário seu login e sua senha. Ao efetuar seu login, será exibido ao usuário uma nova tela com o menu de opções.

## [RF002] Acessar menu  de opções
Ator: Gerentes e Vendedores
Descrição: O sistema apresentará uma tela com um menu de opções ao usuário, sendo essas: 1) Buscar clientes; 2) Cadastrar clientes; 3) Editar cadastro de cliente; e 4) Finalizar sessão. Ao digitar algumas das opções 1,2 ou 3, o sistema direcionará o usuário para uma tela de acordo com a opção desejada. Se o usuário escolher a opção 4, será exibida na tela, a seguinte mensagem ao usuário: “Sua sessão foi finalizada”, e com isso, o sistema se encerrará.

## [RF003] Buscar clientes
Ator: Gerentes e Vendedores
Descrição: Ao escolher a opção “1) Buscar clientes”, será solicitado ao usuário que ele digite CNPJ do cliente que está buscando. O sistema irá consultar no seu banco de dados se o dado informado já existe. 
Caso o sistema encontre o CNPJ informado, será exibida na tela as informações de cadastro do cliente. Em seguida, o sistema deverá perguntar ao usuário se o mesmo deseja retornar ao menu principal. Se a resposta for “Sim”, o menu de opções será exibido na tela. Se a resposta for “Não”, será exibida na tela, a seguinte mensagem ao usuário: “Sua sessão foi finalizada”, e com isso, o sistema se encerrará. 
Caso o sistema não encontre o CNPJ informado, será exibida na tela a seguinte mensagem: “Cliente não cadastrado”. Em seguida, o sistema deverá perguntar ao usuário se o mesmo deseja retornar ao menu principal. Se a resposta for “Sim”, o menu de opções será exibido na tela. Se a resposta for “Não”,, será exibida na tela, a seguinte mensagem ao usuário: “Sua sessão foi finalizada”, e com isso, o sistema se encerrará. 

## [RF004] Cadastrar clientes
Ator: Gerente e Vendedores
Descrição: Ao escolher a opção “2) Cadastrar clientes”, será exibida na tela uma mensagem para que o usuário digite os dados do cliente a ser cadastrado. 
	Após finalizar o cadastro dos dados do cliente, o sistema deverá exibir na tela a seguinte mensagem: “Você deseja salvar o cadastro?”. Se a resposta for “Sim”, o sistema retornará na tela a seguinte mensagem: “Cliente cadastrado com sucesso”, e em seguida, o sistema deverá perguntar ao usuário se o mesmo deseja retornar ao menu principal. Se a resposta for “Sim”, o menu de opções será exibido na tela. Se a resposta for “Não”, será exibida na tela, a seguinte mensagem ao usuário: “Sua sessão foi finalizada”, e com isso, o sistema se encerrará. 

## [RF005] Editar cadastro de cliente
Ator: Gerente e Vendedores
Descrição: Ao escolher a opção “3) Editar cadastro de cliente”, o sistema solicitará que o usuário informe o CNPJ do cadastro que ele deseja atualizar. O sistema irá consultar se o CNPJ informado está cadastrado no seu banco de dados, e caso o CNPJ seja encontrado, as informações do cadastro deverão ser exibidas na tela. Em seguida, o usuário deverá selecionar o campo que deseja atualizar no cadastro, e após isso, deverá clicar no botão de “Salvar atualização”. Será retornada na tela a seguinte mensagem ao usuário: “Atualização registrada com sucesso.” Caso o usuário deseje cancelar a atualização do cadastro, ele poderá clicar no botão “Cancelar atualização”.  Em seguida, o sistema deverá perguntar ao usuário se o mesmo deseja retornar ao menu principal. Se a resposta for “Sim”, o menu de opções será exibido na tela. Se a resposta for “Não”, será exibida na tela, a seguinte mensagem ao usuário: “Sua sessão foi finalizada”, e com isso, o sistema se encerrará. 

## [RF006]  Filtrar cadastros 
Ator: Gerente
Descrição: No canto superior da tela, deverá ser exibido um botão “Filtros”, no qual o usuário poderá escolher os campos pelos quais deseja filtrar as informações que aparecerão na tela.

## 6. REQUISITOS NÃO FUNCIONAIS
Foram identificados alguns requisitos para melhorar o funcionamento do sistema, apesar de não serem imprescindíveis para o seu funcionamento. São esses: 
## [RNF001] Cadastrar etapas do processo comercial
	Ator: Gerente
	Descrição: Essa funcionalidade inclui no menu principal do sistema, uma nova opção para os gerentes: “Cadastrar nova etapa do processo comercial”. Além das etapas que já vem configuradas com o sistema (Oportunidade, Contato realizado, Orçamento enviado e Venda efetivada), essa função permite que o Gerente possa criar novas etapas no processo comercial, alterando a estrutura de armazenamento das informações. 

## [RNF002] Cadastrar vendedores
	Ator: Gerente
	Descrição: Essa funcionalidade inclui no menu principal do sistema, a opção de “Cadastrar vendedores”. Além dos vendedores que já vem configuradas como opções do sistema, essa função permite que o Gerente possa efetuar novos cadastros de vendedores, caso haja mudanças na equipe comercial. 
 
## [RNF003] Cadastrar produtos
	Ator: Gerente
	Descrição: Essa funcionalidade inclui no menu principal do sistema, a opção de “Cadastrar produtos”. Além dos produtos já cadastrados na estrutura do sistema, essa função permite que o gerente possa cadastrar novas opções de produtos a serem selecionados, caso haja alterações no portfólio de ofertas da empresa. 

## [RNF004] Exportar dashboard
Ator: Gerentes
	Descrição: Essa funcionalidade permite que as informações registradas no sistema, sejam agrupadas e formem um dashboard que possa ser exportado em formato PDF pelo sistema.  

## [RNF005] Integrar com o WhatsApp Web - aplicativo de mensagem
Ator: Vendedores
	Descrição: O sistema oferece uma API que permite a sua integração com o whatsapp web do vendedor. Assim, quando o vendedor acessa os dados de telefone whatsapp cadastrado, ao clicar no ícone do telefone, uma nova tela deverá aparecer, direcionando o vendedor para a janela de conversa com o cliente já no aplicativo de mensagem Isso torna mais fácil a interação do vendedor com o cliente, uma vez que retira a necessidade do vendedor ter que digitar o telefone em seu celular, salvar o contato, buscar pelo contato no aplicativo de mensagem  para enfim enviar mensagem. Com a integração, basta um clique para que a mensagem seja enviada diretamente ao cliente.

## 7. TELAS PREVISTAS

## 7.1. TELA 1: Autenticação de usuários 
Descrição: O sistema deverá apresentar uma tela inicial com três campos para o usuário informar seu nome, seu email e sua senha.  
Registros a serem armazenados: email do usuário e senha do usuário.

## 7.2. TELA 2: Menu de opções
Descrição: O sistema deverá apresentar uma tela com um menu de opções, sendo essas: 1) Buscar clientes; 2) Cadastrar clientes; 3) Gerenciar clientes; e 4) Finalizar sessão. O sistema deverá possuir um campo para registrar a opção escolhida pelo usuário.
Registro a ser armazenado: opção de escolha.

## 7.3 TELA 3: Busca de clientes
Descrição: Caso a opção de escolha na tela 2 seja “1) Buscar clientes”, o sistema deverá direcionar o usuário para uma tela com um campo de pesquisa no qual o usuário deverá informar o CNPJ a ser consultado.
Registro a ser armazenado: cnpj.

## 7.4. TELA 4: Cadastro de clientes
Descrição: Caso a opção de escolha na tela 2 seja “2) Cadastrar clientes”, o sistema deverá direcionar o usuário para uma tela com campos para cadastro das informações do cliente. 
Registros a serem armazenados: cnpj, nome da empresa, nome do contato focal, telefone da empresa, email da empresa, cidade da empresa, uf da empresa, responsável, status no funil de vendas, produto e observação. 

## 8. TECNOLOGIAS PREVISTAS
Para desenvolvimento do Sistema, algumas tecnologias serão necessárias e já estão previstas no projeto. Entre as tecnologias estão:
MySQL: construção dos bancos para armazenamento das informações.
SQL: consulta e manipulação dos dados.
Java: desenvolvimento de APIs e interações no frontend.
Figma: desenvolvimento de interface do usuário.
Hospedagem e infraestrutura: no momento, hospedagem do sistema em servidores locais, e posterior migração para serviço de nuvem no Amazon Web Services (AWS).

## 9.DIAGRAMA ER DO SISTEMA E DICIONÁRIO DE DADOS
## 9.1. Diagrama Entidade Relacionamento
<img src="https://github.com/andresawendt/sistemaGerenciamentoClientes_CRM/blob/5f90f8e8ca4133f2af33c33aab7e35949e53336e/MODELO%20BANCO%20DE%20DADOS.png" width=450> 

## 9.2. Dicionário de Dados 
<img 
