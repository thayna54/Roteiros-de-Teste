<img src="https://qph.fs.quoracdn.net/main-qimg-7f98dd9dae16cb011521074368ef90d1" width="123px" alt="verifica.me" align="right">

Teste 1 - Intimação Eletrônica
=====

**Descrição do cliente:** 
Pendências sobre intimação eletrônica.

**Dados Reprodução em Base TRE3-** 

Versão:

Base de dados/IP (Origem e Destino)/Alias: 

Usuário:

Foro: 

**Critérios de Aceite:** 
Alterando o tipo de participação da parte no processo após a emissão de uma intimação, deve alterar também registro de cdtipoparte na tabela eedtselecaoato. 

**Cenário de teste:** 
Cadastrar um processo, emitir uma intimação eletrônica e depois alterar tipo das partes

**DADO QUE**

O usuário possui um processo

**E**

Cadastra as partes com os respectivos tipos (Ativo, Passivo...)

**E**

Emite um ato (Intimação Eletrônica)

**E**

Altera tipo de participação

**ENTÃO**

A rotina deixa de processar a intimação eletrônica pois ainda consta com o tipo de participação antigo na eedtselecaoato.


**Caso de teste:**
No cadastro de partes do processo, após a emissão da intimação eletrônica, é alterado Tipo de Parte da parte intimada e ocorre erro de processamento da rotina não alterando cdtipoparte na eedtselecaoato como está na efpgparte.

**Passo a Passo**

**1** - Via SAJPG5, criar um processo

**2** - Adicionar no processo uma parte vinculada a um convênio (123) e uma parte comum (321)

**3** - Emitir uma decisão para o processo (Modelo Y)

**4** - Gerar um ato a partir dessa decisão

**5** - Rodar rotina intimacaocontingencia

**6** - Confirmar se processou corretamente (Print da tela)

**7** - Alterar tipo de participação da parte intimada via tela de Partes e Representantes (Print da tela)

**8** - Inserir na base net, na tabela enetatousuario, o dtintimacao para a rotina processar (Print da tela)

**9** - Rodar rotina iniciodeprazo


**Resultado Esperado:**
Aparecer erro de Intimação Eletrônica nas pendencias do processo e nas tabelas esajpendenciaprazo e esajmensagemobjeto.



***

Teste 2 - Configuração de Colunas
=====

**Problema:**
No ADM está disponível coluna para para inserção, porém na Configuração de Colunas no fluxo de Trabalho (SAJPG5), ela não aparece.

**Dados Reprodução em Base Local -** 

Versão: 

Base de dados/IP (Origem e Destino)/Alias: 

Usuário:

Foro: 

**Cenário 1 -** 
Comportamento da configuração do fluxo quando a checkbox "Criar configuração personalizada de colunas" não está marcada

**DADO QUE**

O usuário acessa no ADMPG5 o Apoio> Fluxo de Trabalho> "Painel de Configuração do Processo Digital"

**E**

Seleciona o fluxo desejado

**E**

Seleciona a versão atual do fluxo

**E**

Na versão do fluxo escolhida seleciona uma fila de trabalho

**E**

Na fila de trabalho selecionada, a checkbox "Criar configuração personalizada de colunas" não está marcada

**E**

Na consulta do fluxo via SAJPG5, clicar com o botão direito do mouse na barra de colunas e escolher a opção "Configurar Colunas", 

**ENTÃO**

Apenas as colunas da seção "Todas" ficam disponíveis

**Caso de teste 1:** 
Na opção "Configurar Colunas" no fluxo de trabalho (Print da tela) deve mostrar SOMENTE colunas mostradas no agrupamento TODAS 'com checkbox Painel de Configuração do Processo Digital desmarcado'(Print da tela).

**Pré-condição:**
O usuário acessa no ADMPG5 o Apoio> Fluxo de Trabalho> "Painel de Configuração do Processo Digital" e na fila de trabalho selecionada, a checkbox "Criar configuração personalizada de colunas" não deve estar marcada - (Print da tela).

**Critérios de Aceite:** 
Disponibilizar no ADMPG5 somente o que o usuário consegue adicionar no fluxo de trabalho (SAJPG5).

**Passo a Passo**

**1** - Via SAJPG5, acessar módulo Andamento

**2** - Acessar Fluxo de Trabalho

**3** - Selecionar Fluxo Todos ou Cível - Atos (Somente exemplo)

**4** - Seleciona Subfluxo Processo> Fila Inicial - Ag. Análise do Cartório - Urgente

**5** - Com o lado direito do Mouse na barra de colunas, selecionar opção Configurar Colunas

**6** - Na tela (Configurar Colunas), pesquisar coluna Nome da Parte (coluna exemplo)

**Resultado Esperado:** 
Encontrar coluna disponível na opção TODAS (Print da tela) e localizar coluna no "Configurar Coluna" no Fluxo de trabalho (Print da tela).


**Cenário 2:** 
Comportamento da configuração do fluxo quando a checkbox "Criar configuração personalizada de colunas" está marcada

**DADO QUE**

O usuário acessa no ADMPG5 o Apoio> Fluxo de Trabalho> "Painel de Configuração do Processo Digital"

**E**

Seleciona o fluxo desejado

**E**

Seleciona a versão atual do fluxo

**E**

Na versão do fluxo escolhida seleciona uma fila de trabalho

**E**

Na fila de trabalho selecionada, a checkbox "Criar configuração personalizada de colunas" está marcada (Print da tela)

**E**

Na consulta do fluxo via SAJPG5, ao clicar com o botão direito do mouse na barra de colunas

**E**

Escolher a opção "Configurar Colunas"  (Print da tela) , 

**ENTÃO**

Não mostra todas as colunas que estão disponíveis no agrupamento TODAS (Print da tela).

**Caso de teste 2:**
Na opção "Configurar Colunas" no fluxo de trabalho (Print da tela) não deve mostrar colunas mostradas no agrupamento TODAS 'com checkbox Painel de Configuração do Processo Digital marcado' (Print da tela).

**Pré-condição:** 
O usuário acessa no ADMPG5 o Apoio> Fluxo de Trabalho> "Painel de Configuração do Processo Digital" e na fila de trabalho selecionada, a checkbox "Criar configuração personalizada de colunas" deve estar marcada - (Print da tela).

**Critérios de Aceite:** 
Checkbox "Criar configuração personalizada de colunas" marcada, não deve mostrar todas as colunas do agrupamento TODAS.

**Passo a Passo** 

**1** - Via SAJPG5, acessar módulo Andamento

**2** - Acessar Fluxo de Trabalho

**3** - Selecionar Fluxo Todos ou Cível - Atos (Somente exemplo)

**4** - Seleciona Subfluxo Processo> Fila Inicial - Ag. Análise do Cartório - Urgente

**5** - Com o lado direito do Mouse na barra de colunas, selecionar opção Configurar Colunas

**6** - Na tela (Configurar Colunas), pesquisar coluna Nome da Parte (coluna exemplo)

**Resultado Esperado:** 
Encontrar coluna disponível na opção TODAS (Print da tela) e não localizar coluna no "Configurar Coluna" no Fluxo de trabalho (Print da tela).
