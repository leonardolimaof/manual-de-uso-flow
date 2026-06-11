# Manual do Sistema BGTech Flow

**Plataforma de Gerenciamento e Alocação para Eventos Educacionais**

---

## Sumário

1. [Visão Geral do Sistema](#1-visão-geral-do-sistema)
2. [Hierarquia de Usuários e Permissões](#2-hierarquia-de-usuários-e-permissões)
3. [Fluxo Completo do Sistema (Passo a Passo)](#3-fluxo-completo-do-sistema-passo-a-passo)
4. [Módulo de Autenticação](#4-módulo-de-autenticação)
5. [Módulo de Eventos](#5-módulo-de-eventos)
6. [Módulo de Locais (Escolas)](#6-módulo-de-locais-escolas)
7. [Módulo de Colaboradores](#7-módulo-de-colaboradores)
8. [Módulo de Convites](#8-módulo-de-convites)
9. [Módulo de Alocação](#9-módulo-de-alocação)
10. [Módulo de Candidatos](#10-módulo-de-candidatos)
11. [Módulo de Funções/Cargos](#11-módulo-de-funçõescargos)
12. [Módulo de Relatórios](#12-módulo-de-relatórios)
13. [Funcionalidades do Aplicativo Mobile](#13-funcionalidades-do-aplicativo-mobile)
14. [Glossário](#14-glossário)

---

## 1. Visão Geral do Sistema

O **BGTech Flow** é um sistema desenvolvido para organizar e gerenciar eventos educacionais de grande porte, como concursos públicos, processos seletivos e avaliações aplicadas em escolas.

### O que o sistema resolve

Organizar um evento que envolve várias escolas, centenas de profissionais (aplicadores, fiscais, coordenadores) e milhares de participantes é uma tarefa complicada. O BGTech Flow simplifica todo esse processo:

- **Cadastro e organização** de eventos, escolas, salas, profissionais e participantes
- **Envio de convites** com aceite ou recusa por link
- **Distribuição de profissionais** nas salas e escolas
- **Alocação de coordenadores** para cada local
- **Alocação de participantes (candidatos)** nas salas respeitando a lotação máxima
- **Geração de relatórios** em PDF e planilha
- **Confirmação de presença** no dia do evento
- **Controle de gastos** com valor previsto e valor realizado

### Para quem foi feito

O BGTech Flow foi desenvolvido para a **Consulpam**, empresa que realiza concursos públicos, processos seletivos e avaliações em parceria com prefeituras e escolas municipais.

---

## 2. Hierarquia de Usuários e Permissões

O sistema possui **dois níveis de hierarquia**: o primeiro define o que você pode fazer dentro da plataforma, o segundo define qual a sua função dentro de um evento específico.

### 2.1 Papéis dentro da plataforma

| Papel | O que pode fazer |
|---|---|
| **ADMIN** | **Tudo.** Pode criar e editar eventos, cadastrar escolas, definir funções, alocar profissionais, gerar convites e ver dados financeiros. |
| **FINANCEIRO** | **Ver dados e gerar relatórios.** Pode visualizar informações do evento e gerar relatórios em planilha. **Não pode** alocar ninguém nem gerenciar convites. |
| **PARTICIPANTE** | **Acesso básico.** Pode ver seus eventos, seu perfil e suas informações. |

### 2.2 Papéis dentro de um evento

| Papel | Descrição | Pode alocar pessoas? | Pode convidar? |
|---|---|---|---|---|
| **GERAL** | Coordenador Geral. Supervisiona todas as escolas e toda a equipe do evento. | Sim | Sim |
| **LOCAL** | Coordenador de uma escola específica. Cuida da equipe da sua escola. | Sim (apenas na sua escola) | Sim (limitado) |
| **COLABORADOR** | Profissional que trabalha no evento (aplicador, fiscal). **Não acessa o sistema** - apenas recebe convite por e-mail. | Não | Não |
| **SCHOOL** | Representante da escola no evento. | Não | Não |

### 2.3 O que cada um pode fazer

> **Importante**: O **COLABORADOR** (simples) **não acessa o sistema**. Ele apenas recebe o convite por e-mail e responde se aceita ou recusa. Por isso, não há permissões de sistema para ele.

| Funcionalidade | ADMIN | FINANCEIRO | GERAL | LOCAL |
|---|---|---|---|---|
| Criar ou editar Eventos | Sim | - | - | - |
| Cadastrar Escolas | Sim | - | - | - |
| Cadastrar Funções/Cargos | Sim | - | - | - |
| Cadastrar Colaboradores | Sim | - | Sim | Sim |
| Gerar Convites | Sim | - | Sim | Sim |
| Alocar Coordenadores | Sim | - | Sim | - |
| Alocar Colaboradores | Sim | - | Sim | Sim |
| Alocar Candidatos | Sim | - | - | - |
| Confirmar Presença | Sim | - | Sim | Sim |
| Remover Alocação | Sim | - | Sim | Sim |
| Ver Métricas do Evento | Sim | Sim | Sim | Sim |
| Gerar Relatório PDF | Sim | - | Sim | Sim |
| Gerar Relatório Planilha | Sim | Sim | Sim | Sim |
| Anexar Edital | Sim | - | - | - |
| Editar Próprio Perfil | Sim | Sim | Sim | Sim |

### 2.4 Regras para convidar pessoas

- **ADMIN** pode convidar qualquer pessoa para qualquer função
- **GERAL** pode convidar pessoas para as funções LOCAL e COLABORADOR
- **LOCAL** só pode convidar pessoas para a função COLABORADOR
- **COLABORADOR** não pode convidar ninguém

---

## 3. Fluxo Completo do Sistema (Passo a Passo)

### 3.1 Visão Geral

```
Antes do evento:
  1. ADMIN cadastra o Evento
  2. ADMIN cadastra os Locais (Escolas) com as Salas
  3. ADMIN cadastra as Funções/Cargos
  4. ADMIN/GERAL/LOCAL cadastram os Colaboradores
  5. ADMIN/GERAL/LOCAL enviam Convites para os Colaboradores participarem
  6. Colaboradores recebem e-mail com link para Aceitar ou Recusar

Alocação (distribuição da equipe):
  7. ADMIN/GERAL alocam Coordenadores LOCAIS para cada escola
  8. ADMIN/GERAL/LOCAL distribuem Colaboradores nas Salas ou Área Externa
  9. ADMIN aloca Candidatos (alunos) nas Salas

Durante o evento:
  10. Presença dos Colaboradores é confirmada

Depois do evento:
  11. Geração de relatórios (PDF ou Planilha)
  12. Desalocação de colaboradores (se precisar)
```

---

### 3.2 Passo a Passo Detalhado

#### PASSO 1: Entrar no Sistema

**Quem faz:** Qualquer usuário cadastrado (ADMIN, FINANCEIRO, PARTICIPANTE)

**Como fazer:**
1. Acesse o endereço do sistema BGTech Flow
2. Na tela de entrada, digite seu **e-mail** e **senha**
3. Clique em "Entrar"

**O que acontece:**
- O sistema confere se seus dados estão corretos
- Se for o **primeiro acesso**, o sistema vai pedir para você criar uma senha nova
- Você é direcionado para a tela de **Selecionar Evento**

**Primeiro Acesso:**
1. Após o login, aparecerá uma janela de **primeiro acesso**
2. Digite a **senha atual** e a **nova senha**
3. A senha precisa ter no mínimo 6 caracteres
4. Depois de confirmar, você segue para a tela principal

**Esqueceu a senha?**
1. Na tela de entrada, clique em "Esqueceu sua senha?"
2. Informe seu e-mail
3. Você receberá um **código de 6 números** no e-mail
4. Digite o código na tela de verificação
5. Crie uma nova senha

---

#### PASSO 2: Selecionar um Evento

**Quem faz:** Todos os usuários

**Como fazer:**
1. Depois de entrar, você será direcionado para a tela **"Selecionar Evento"**
2. Uma lista mostra todos os eventos que você pode acessar
3. Clique no evento desejado para trabalhar nele

**O que acontece:**
- O evento escolhido fica como "evento ativo"
- O destino após a escolha depende do seu papel:
  - **FINANCEIRO**: vai para a página de **Colaboradores**
  - **Demais papéis**: vai para o **Painel Principal (Dashboard)** do evento

---

#### PASSO 3: Painel Principal - Acompanhamento de Convites

**Quem faz:** ADMIN, GERAL, LOCAL

**O que é:** O Painel Principal é a primeira tela depois que você seleciona um evento. Ele mostra:

**Indicadores:**
- **Convites Enviados**: total de convites gerados
- **Convites Aceitos**: quantos foram aceitos
- **Convites Pendentes**: quantos ainda aguardam resposta
- **Convites Recusados**: quantos foram recusados

**Lista de Convites Enviados:**
Mostra todos os convites que você gerou, com:
- Nome do convidado
- Função (COLABORADOR, LOCAL, GERAL)
- Situação (Pendente, Aceito, Recusado)
- Data de validade
- Opção para reenviar o convite

**Regra:**
- **ADMIN**: enxerga **todos** os convites do evento
- **GERAL/LOCAL**: enxerga apenas os convites que **você mesmo enviou**

---

#### PASSO 4: Cadastrar um Evento

**Quem faz:** Somente ADMIN

**Como fazer:**
1. No menu lateral, clique em **"Eventos"**
2. Clique no botão **"Adicionar Evento"**
3. Preencha o formulário:
   - **Nome do evento** (obrigatório)
   - **Descrição** (obrigatório)
   - **Tipo de evento** (escolha entre os tipos cadastrados)
   - **Data de início** e **Data de término**
   - **Horário de início** e **Horário de término**
   - **Valor base** (quanto o evento pode gastar)
   - **Selecionar Estados** (quais estados fazem parte)
   - **Selecionar Municípios** (quais cidades participantes)
4. Opcional: anexe o **Edital** do evento (arquivo PDF)
5. Clique em **"Salvar"**

**Editar Evento:**
1. Na lista de eventos, clique no evento desejado
2. Na página de detalhes, clique em "Editar" para alterar os dados
3. É possível mudar os municípios vinculados

**Vincular ou Desvincular Escolas ao Evento:**
1. Na página de detalhes do evento, vá em "Locais Cadastrados"
2. Clique em "Gerenciar Locais"
3. Marque ou desmarque as escolas que deseja vincular ou remover
4. Confirme a operação

---

#### PASSO 5: Cadastrar um Local (Escola)

**Quem faz:** ADMIN

**Como fazer:**
1. No menu lateral, clique em **"Locais"**
2. Clique em **"Adicionar Local"**
3. Preencha:
   - **Nome do local** (obrigatório)
   - **Tipo de escola** (obrigatório - ex: Municipal, Estadual)
   - **CNPJ** (opcional)
   - **Telefone** (opcional)
   - **Nome do gestor** (obrigatório)
   - **E-mail do gestor** (obrigatório)
   - **Equipe necessária** (quantas pessoas precisa para este local)
   - **Endereço**: CEP (preenche automaticamente), Logradouro, Número, Bairro, Cidade, Estado
4. Opcional: adicione **Salas** clicando em "Adicionar Sala":
   - Nome da sala
   - Capacidade (quantas pessoas cabem)
   - Código da sala
   - Andar
5. Clique em **"Salvar"**

**Gerenciar Salas:**
Na página de detalhes do local:
- A seção **"Salas Cadastradas"** lista todas as salas com nome, código, andar e capacidade
- Você pode adicionar, editar ou remover salas

---

#### PASSO 6: Cadastrar Funções/Cargos

**Quem faz:** ADMIN

**O que são:** As funções (ou cargos) definem os tipos de trabalho que os profissionais vão exercer. Exemplos: "Aplicador", "Fiscal de Sala", "Portaria", "Coordenação".

**Como fazer:**
1. No menu lateral, clique em **"Funções"**
2. Clique em **"Adicionar Função"**
3. Preencha:
   - **Nome** (ex: Aplicador)
   - **Descrição** (ex: Aplica a prova na sala)
   - **Valor** (quanto a pessoa vai receber por este trabalho)
   - **Local de atuação**:
     - **Sala**: função exercida dentro de uma sala de aula
     - **Escola**: função exercida na área externa da escola
   - **Situação**: ativo ou inativo
4. Clique em **"Salvar"**

**Importante:** Na hora de alocar as pessoas, a função precisa ser compatível:
- Alocação em **sala** → funções com local de atuação **Sala**
- Alocação em **área externa** → funções com local de atuação **Escola**

---

#### PASSO 7: Cadastrar Colaboradores

**Quem faz:** ADMIN, GERAL, LOCAL

**O que são:** Colaboradores são as pessoas que vão trabalhar no evento (aplicadores, fiscais, etc.).

**Como fazer:**
1. No menu lateral, clique em **"Colaboradores"**
2. Clique em **"Adicionar Colaborador"**
3. Preencha:
   - **Nome completo** (obrigatório)
   - **CPF** (obrigatório)
   - **E-mail** (obrigatório para quem vai ser coordenador LOCAL ou GERAL)
   - **Telefone** (obrigatório)
   - **Endereço** (opcional): CEP, Logradouro, Número, Bairro, Cidade, Estado
   - **Dados bancários** (opcional): Banco, Agência, Conta, Chave PIX
4. Clique em **"Salvar"**

**Visualizar Colaborador:**
1. Na lista, clique sobre um colaborador para ver os detalhes
2. A página exibe: nome, CPF, e-mail, telefone, endereço e dados bancários

---

#### PASSO 8: Enviar Convites

**Quem faz:** ADMIN, GERAL, LOCAL

**Quando:** Depois que o colaborador já está cadastrado e o evento está ativo.

**Como fazer:**
1. No **Painel Principal**, clique em **"Convidar Colaborador"**
2. Ou na tela de **Colaboradores**, selecione alguém e clique em "Convidar"
3. Aparece uma janela com:
   - **Dados do evento** (para conferência)
   - **Dados do colaborador** (nome, e-mail, CPF, telefone)
   - **Função do colaborador** (escolha):
     - **Colaborador Simples** (COLABORADOR) - função operacional
     - **Coordenador Local** (LOCAL) - coordenador de escola
     - **Coordenador Geral** (GERAL) - coordenador geral
4. Clique em **"Convidar"**

**Regras importantes:**
- Se a função for **GERAL** ou **LOCAL**, o **e-mail é obrigatório**
- Para **COLABORADOR**, o e-mail é opcional
- Uma pessoa só pode ser convidada **uma vez** para o mesmo evento
- O convite **vence em 5 dias**

**O que acontece:**
- O convite fica com status **Pendente**
- Se a pessoa tem e-mail, ela recebe uma mensagem com o link para aceitar ou recusar

---

#### PASSO 9: Aceitar ou Recusar um Convite (para quem foi convidado)

**Quem faz:** Pessoa que recebeu o convite

**Como fazer:**
1. Você recebe um e-mail com o link de confirmação
2. Clique no link. Você será direcionado para a página de confirmação
3. A tela mostra:
   - **"Confirmação de Convite"**
   - Mensagem: "Você recebeu um convite para participar de um evento. Deseja confirmar sua participação?"
   - Botões: **"Confirmar"** ou **"Recusar"**
4. Clique em **"Confirmar"** para aceitar ou **"Recusar"** para recusar

**O que acontece ao aceitar:**
- O convite muda para **Aceito**
- Você fica vinculado ao evento com a função escolhida
- Se for coordenador (GERAL ou LOCAL), o sistema cria automaticamente seu acesso à plataforma

**O que acontece ao recusar:**
- O convite muda para **Recusado**
- Você não participa do evento

**Convite vencido:**
Se o convite passou de 5 dias, ele aparece como **Vencido** e não pode mais ser respondido.

**Gerenciamento manual (para ADMIN):**
O ADMIN pode forçar a aceitação ou recusa de qualquer convite diretamente pelo Painel.

---

#### PASSO 10: Alocar Coordenadores Locais

**Quem faz:** ADMIN, GERAL

**Quando:** Depois do evento configurado, escolas vinculadas e pessoas com função LOCAL já terem aceitado o convite.

**Como fazer:**
1. Vá para a página de detalhes do **Local** (clique no local no menu "Locais")
2. Na seção **"Alocar Coordenador"**, clique em **"Alocar"**
3. Uma janela aparece com:
   - Nome do local
   - Lista de **Coordenadores** disponíveis (quem aceitou convite como LOCAL)
   - Campo de **Remuneração** (quanto vai receber)
4. Selecione o coordenador e informe o valor
5. Clique em **"Salvar"**

**O que acontece:**
- O coordenador é vinculado à escola
- Ele aparece na lista **"Coordenadores Alocados"**
- Para remover, clique no ícone de lixeira

**Regras:**
- Um coordenador só pode ser alocado **uma vez** por evento em cada escola
- Apenas ADMIN e GERAL podem fazer isso
- LOCAL não pode alocar coordenadores

---

#### PASSO 11: Alocar Colaboradores nas Salas

**Quem faz:** ADMIN, GERAL, LOCAL

**Quando:** Depois que os colaboradores aceitaram o convite com função COLABORADOR.

**Como fazer:**
1. Vá para a página de detalhes do **Local**
2. Na seção **"Salas Cadastradas"**, localize a sala desejada e clique em **"Alocar"**
3. Uma janela aparece com:
   - Nome do local e da sala
   - Lista de **Colaboradores** disponíveis
   - Lista de **Funções** (apenas funções com local de atuação Sala)

**Alocação em Área Externa (sem sala específica):**
1. Na seção **"Alocação na Área Externa"**, clique em **"Alocar"**
2. A janela mostra:
   - Nome do local
   - Lista de **Colaboradores** disponíveis
   - Lista de **Funções** (apenas funções com local de atuação Escola)

**O que acontece:**
- O colaborador é vinculado ao evento, escola e sala
- A função escolhida é registrada
- Ele aparece na lista **"Colaboradores Alocados"**

**Regras:**
- O número de colaboradores não pode passar do limite definido na escola
- Funções de Sala só podem ser usadas em salas
- Funções de Escola só podem ser usadas na área externa
- **FINANCEIRO** não vê as opções de alocação

---

#### PASSO 12: Alocar Candidatos (Participantes)

**Quem faz:** ADMIN

**O que são:** Candidatos são os participantes que vão fazer a prova ou avaliação. Eles podem ser importados de uma planilha e alocados nas salas.

**Como fazer:**
1. No menu lateral, clique em **"Candidatos"**
2. Faça o **upload de uma planilha** (arquivo .xlsx) com os dados dos candidatos:
   - Nome completo
   - CPF
   - E-mail
   - Telefone
   - Número de inscrição
3. Após o upload, os candidatos aparecem na lista

**Alocar um candidato:**
1. Na lista, clique em **"Alocar"** ao lado do candidato desejado
2. Escolha:
   - **Evento**
   - **Local (Escola)**
   - **Sala** (opcional)
3. O sistema verifica:
   - Se o candidato já não foi alocado antes
   - Se a sala tem espaço disponível
4. Clique em **"Confirmar"**

**O que acontece:**
- O candidato é vinculado ao evento, escola e sala
- Se tiver e-mail, ele recebe as informações da escola onde fará a prova

---

#### PASSO 13: Confirmar Presença

**Quem faz:** ADMIN, GERAL, LOCAL

**Quando:** Durante o evento, para registrar quais colaboradores compareceram.

**Como fazer:**
1. Vá para a página de detalhes do **Local**
2. Na seção **"Colaboradores Alocados"**, localize o colaborador
3. Clique em **"Confirmar Presença"**

**O que acontece:**
- O status do colaborador muda para "Presente"
- Isso pode ser usado para controle de pagamento

---

#### PASSO 14: Remover Alocação

**Quem faz:** ADMIN, GERAL, LOCAL

**Quando:** Quando um colaborador ou coordenador precisa ser removido.

**Como fazer (Colaborador):**
1. Vá para a página de detalhes do **Local**
2. Na seção **"Colaboradores Alocados"**, localize a pessoa
3. Clique no ícone de **lixeira** para remover

**Como fazer (Coordenador):**
1. Na seção **"Coordenadores Alocados"**, localize o coordenador
2. Clique no ícone de **lixeira**

**O que acontece:**
- A pessoa é desvinculada daquela função
- Ela fica disponível para ser alocada em outro lugar

---

#### PASSO 15: Gerar Relatórios

**Quem faz:** ADMIN, GERAL, LOCAL (PDF) | FINANCEIRO (Planilha)

**Quando:** A qualquer momento para acompanhamento, ou no final do evento.

**Como fazer:**
1. Vá para a página de detalhes do **Local**
2. Na seção **"Colaboradores Alocados"**, clique em **"Baixar Relatório"**

**Tipos de Relatório:**

**Relatório em PDF (para ADMIN, GERAL, LOCAL):**
Documento com:
- Nome da escola, tipo, CNPJ e telefone
- Nome do evento
- Lista dos colaboradores alocados, suas funções e salas
- Data de impressão e quem gerou

**Relatório em Planilha (para FINANCEIRO):**
Arquivo Excel (.xlsx) com:
- Dados organizados dos colaboradores alocados
- Ideal para controle financeiro e folha de pagamento

---

#### PASSO 16: Gerenciar seu Perfil

**Quem faz:** ADMIN, GERAL, LOCAL, FINANCEIRO

**Como fazer:**
1. No menu lateral, clique em **"Perfil"**
2. Veja suas informações:
   - Nome, e-mail, CPF, telefone
   - Foto (se tiver)
   - Endereço (se cadastrado)
   - Dados bancários (se cadastrado)
3. Clique em **"Editar Perfil"** para alterar seus dados
4. Clique em **"Alterar Senha"** para mudar a senha

---

#### PASSO 17: Visualizar Informações do Evento

**Quem faz:** ADMIN, FINANCEIRO, GERAL, LOCAL

**Como fazer:**
1. Na lista de eventos, clique sobre um evento
2. A página de detalhes mostra:

**Seção "Detalhes do Evento":**
- Nome, descrição, tipo
- Valor previsto e valor gasto (visível apenas para ADMIN)
- Período e horário
- Municípios participantes
- Edital em PDF (para visualizar ou baixar)

**Seção "Locais Cadastrados":**
- Lista de escolas vinculadas ao evento
- Para cada escola: tipo, número de salas, capacidade total

**Seção "Colaboradores do Evento":**
- Lista de todos os colaboradores vinculados ao evento

**Resumo de Locais:**
- Total de Salas, Capacidade Total, Locais Participantes

**Resumo de Colaboradores:**
- Colaboradores Necessários, Colaboradores Disponíveis, Colaboradores Alocados

---

## 4. Módulo de Autenticação

### 4.1 Entrar (Login)
- Informe seu e-mail e senha na tela inicial
- Se os dados estiverem corretos, você entra no sistema
- Se for o primeiro acesso, será solicitada a criação de uma nova senha

### 4.2 Sair (Logout)
- Clique na opção de sair no menu lateral ou no seu perfil
- Você volta para a tela de entrada

### 4.3 Alterar Senha
- Acesse seu Perfil
- Clique em "Alterar Senha"
- Digite a senha atual e a nova senha

### 4.4 Recuperar Senha
- **Solicitar código**: informe seu e-mail para receber um código de 6 números
- **Verificar código**: digite o código recebido
- **Confirmar nova senha**: crie uma nova senha

---

## 5. Módulo de Eventos

### 5.1 Dados de um Evento
| Campo | Descrição | Obrigatório |
|---|---|---|
| Nome | Nome do evento | Sim |
| Descrição | Descrição do evento | Sim |
| Tipo | Concurso, Processo Seletivo, etc. | Sim |
| Data de início | Quando começa | Sim |
| Data de término | Quando termina | Sim |
| Horário de início | Horário de abertura | Sim |
| Horário de término | Horário de encerramento | Sim |
| Valor base | Orçamento previsto | Sim |
| Localidades | Estados e Municípios participantes | Sim |
| Edital | Arquivo PDF com as regras | Não |

### 5.2 Tipos de Evento
Servem para categorizar os eventos. Exemplos: "Concurso Público", "Processo Seletivo", "Avaliação Diagnóstica".

### 5.3 Estados e Municípios
O evento pode abranger vários estados e municípios. A lista é carregada automaticamente com base nos dados oficiais do IBGE.

---

## 6. Módulo de Locais (Escolas)

### 6.1 Dados de um Local
| Campo | Descrição | Obrigatório |
|---|---|---|
| Nome | Nome da escola | Sim |
| Tipo | Municipal, Estadual, etc. | Sim |
| CNPJ | CNPJ da escola | Não |
| Telefone | Telefone de contato | Não |
| Nome do gestor | Responsável pela escola | Sim |
| E-mail do gestor | E-mail do responsável | Sim |
| Equipe necessária | Quantos colaboradores precisa | Sim |
| Endereço | Endereço completo | Sim |
| Salas | Lista de salas da escola | Não |

### 6.2 Salas
| Campo | Descrição | Obrigatório |
|---|---|---|
| Nome | Nome ou número da sala | Sim |
| Capacidade | Máximo de pessoas na sala | Sim |
| Código | Identificador da sala | Sim |
| Andar | Andar onde fica a sala | Sim |

### 6.3 Andares
Gerenciados pelo ADMIN. Exemplos: "Térreo", "1º Andar", "2º Andar".

---

## 7. Módulo de Colaboradores

### 7.1 Dados do Colaborador
| Campo | Descrição | Obrigatório |
|---|---|---|
| Nome completo | Nome da pessoa | Sim |
| CPF | CPF | Sim |
| E-mail | E-mail | Não (obrigatório se for coordenador) |
| Telefone | Telefone de contato | Sim |
| Endereço | Endereço completo | Não |
| Banco | Código do banco | Não |
| Agência | Agência bancária | Não |
| Conta | Número da conta | Não |
| Chave PIX | Chave para pagamento | Não |

---

## 8. Módulo de Convites

### 8.1 Situações do Convite
| Situação | O que significa |
|---|---|
| Pendente | Aguardando resposta da pessoa |
| Aceito | A pessoa aceitou participar |
| Recusado | A pessoa recusou |
| Vencido | O convite passou do prazo (5 dias) |

### 8.2 Como funciona o convite
1. ADMIN/GERAL/LOCAL envia o convite pelo sistema
2. A pessoa recebe um e-mail com o link
3. A pessoa acessa o link e aceita ou recusa
4. Se aceitar, fica vinculada ao evento
5. Se não responder em 5 dias, o convite vence

### 8.3 Quem pode convidar quem
- **ADMIN**: convida qualquer pessoa
- **GERAL**: convida para LOCAL e COLABORADOR
- **LOCAL**: convida apenas para COLABORADOR
- **COLABORADOR**: não convida ninguém

---

## 9. Módulo de Alocação

### 9.1 Tipos de Alocação

**Alocação de Coordenador:**
- Vincula um coordenador LOCAL a uma escola
- Registra o valor da remuneração

**Alocação de Colaborador em Sala:**
- Vincula o colaborador a uma sala específica
- A função precisa ser do tipo Sala

**Alocação de Colaborador em Área Externa:**
- Vincula o colaborador à escola (sem sala específica)
- A função precisa ser do tipo Escola

**Alocação de Candidato:**
- Vincula o candidato a um evento, escola e sala
- Verifica se a sala tem espaço

### 9.2 Presença
- Marcada individualmente para cada colaborador
- Usada para controle de pagamento

### 9.3 Remover Alocação
- Remove o vínculo da pessoa
- Libera a vaga para outra pessoa
- Disponível para ADMIN, GERAL e LOCAL

---

## 10. Módulo de Candidatos

### 10.1 Dados do Candidato
| Campo | Descrição |
|---|---|
| Nome completo | Nome do candidato |
| CPF | CPF |
| E-mail | E-mail |
| Telefone | Telefone |
| Número de inscrição | Número da inscrição |
| Nome do pai | Nome do pai |
| Nome da mãe | Nome da mãe |
| Data de nascimento | Data de nascimento |

### 10.2 Importação em Lote
- Formato: planilha Excel (.xlsx)
- Você pode baixar um modelo pronto para preencher

### 10.3 Alocação de Candidatos
- Feita um por um pela tela
- O sistema verifica a capacidade da sala
- Se tiver e-mail, o candidato recebe a informação do local da prova

---

## 11. Módulo de Funções/Cargos

### 11.1 Dados da Função
| Campo | Descrição |
|---|---|
| Nome | Nome da função (ex: Aplicador) |
| Descrição | O que a pessoa vai fazer |
| Valor | Quanto vai receber |
| Local de atuação | Sala ou Escola |
| Situação | Ativo ou Inativo |

### 11.2 Locais de Atuação
- **Sala**: funções exercidas dentro de uma sala. Ex: "Aplicador", "Fiscal de Sala"
- **Escola**: funções exercidas na área externa. Ex: "Portaria", "Coordenação Externa"

---

## 12. Módulo de Relatórios

### 12.1 Relatório em PDF
Documento formatado contendo:
- Cabeçalho da escola (nome, tipo, CNPJ, telefone)
- Nome do evento
- Lista dos colaboradores alocados com funções e salas
- Data de impressão e usuário que gerou

### 12.2 Relatório em Planilha (Excel)
Arquivo com os dados organizados em colunas, ideal para:
- Controle financeiro
- Folha de pagamento
- Processamento de dados

---

## 13. Funcionalidades do Aplicativo Mobile

O aplicativo para celular do BGTech Flow oferece as seguintes funções:

### 13.1 Telas Principais
- **Entrar no sistema**: tela de login
- **Selecionar Evento**: escolha do evento
- **Painel Principal**: visão geral
- **Locais**: consulta de escolas e salas
- **Alocações**: consulta de profissionais alocados
- **Candidatos**: visualização de candidatos
- **Perfil**: editar dados pessoais e trocar senha
- **Confirmação de Convite**: aceitar ou recusar convites

### 13.2 Observação
O aplicativo é complementar ao sistema web. Ele é indicado para consultas e operações básicas em campo. Para fazer cadastros, alocações e relatórios completos, use o sistema pelo computador.

---

## 14. Glossário

| Termo | O que significa |
|---|---|
| **BGTech Flow** | Nome do sistema |
| **Consulpam** | Empresa que contrata e usa o sistema |
| **Evento** | Concurso, avaliação ou processo seletivo |
| **Local** | Escola onde o evento acontece |
| **Sala** | Sala de aula dentro da escola |
| **Andar / Piso** | Nível onde a sala fica (térreo, 1º andar) |
| **Colaborador** | Pessoa que trabalha no evento (aplicador, fiscal) |
| **Candidato** | Participante que vai fazer a prova |
| **Coordenador Geral (GERAL)** | Responsável por todo o evento |
| **Coordenador Local (LOCAL)** | Responsável por uma escola |
| **Função / Cargo** | Tipo de trabalho (com valor pago) |
| **Convite** | Mensagem para chamar alguém para participar |
| **Alocação** | Distribuição da pessoa para uma escola ou sala |
| **Edital** | Documento com as regras do evento |
| **Valor Base** | Quanto o evento pode gastar no total |
| **Equipe Necessária** | Quantas pessoas são precisas na escola |
| **Presença** | Confirmação de que a pessoa compareceu |

---

> **Documentação gerada em Junho de 2026**
> **Sistema BGTech Flow v1.0** | Desenvolvido por BGTech
