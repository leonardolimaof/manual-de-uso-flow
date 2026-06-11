# 📘 Manual do Sistema BGTech Flow

<h4 align="center">Plataforma de Gerenciamento e Alocação para Eventos Educacionais</h4>

<p align="center">
  <img alt="Version" src="https://img.shields.io/badge/versão-1.0-blue" />
  <img alt="Status" src="https://img.shields.io/badge/status-finalizado-green" />
  <img alt="Empresa" src="https://img.shields.io/badge/empresa-Consulpam-orange" />
</p>

---

## 📑 Sumário

| # | Seção |
|---|-------|
| 1 | [Visão Geral do Sistema](#1--visão-geral-do-sistema) |
| 2 | [Hierarquia de Usuários e Permissões](#2--hierarquia-de-usuários-e-permissões) |
| 3 | [Fluxo Completo (Passo a Passo)](#3--fluxo-completo-do-sistema-passo-a-passo) |
| 4 | [Módulo de Autenticação](#4--módulo-de-autenticação) |
| 5 | [Módulo de Eventos](#5--módulo-de-eventos) |
| 6 | [Módulo de Locais (Escolas)](#6--módulo-de-locais-escolas) |
| 7 | [Módulo de Colaboradores](#7--módulo-de-colaboradores) |
| 8 | [Módulo de Convites](#8--módulo-de-convites) |
| 9 | [Módulo de Alocação](#9--módulo-de-alocação) |
| 10 | [Módulo de Candidatos](#10--módulo-de-candidatos) |
| 11 | [Módulo de Funções/Cargos](#11--módulo-de-funçõescargos) |
| 12 | [Módulo de Relatórios](#12--módulo-de-relatórios) |
| 13 | [Glossário](#13--glossário) |

---

## 1️⃣ — Visão Geral do Sistema

O **BGTech Flow** é um sistema desenvolvido para organizar e gerenciar eventos educacionais de grande porte, como concursos públicos, processos seletivos e avaliações aplicadas em escolas.

---

### 🎯 O que o sistema resolve

Organizar um evento que envolve várias escolas, centenas de profissionais (aplicadores, fiscais, coordenadores) e milhares de participantes é uma tarefa complicada. O BGTech Flow simplifica todo esse processo:

| O que faz | Descrição |
|-----------|-----------|
| 📋 **Cadastro e organização** | Gerencia eventos, escolas, salas, profissionais e participantes |
| 📧 **Envio de convites** | Envia convites com link para aceitar ou recusar |
| 👥 **Distribuição de profissionais** | Aloca colaboradores nas salas e escolas |
| 🏫 **Alocação de coordenadores** | Define coordenadores para cada local |
| 🎒 **Alocação de participantes** | Distribui candidatos nas salas respeitando a lotação |
| 📄 **Geração de relatórios** | Cria relatórios em PDF e planilha Excel |
| ✅ **Confirmação de presença** | Registra quem compareceu no dia do evento |
| 💰 **Controle de gastos** | Acompanha valor previsto versus valor realizado |

---

### 🏢 Para quem foi feito

O BGTech Flow foi desenvolvido para a **Consulpam**, empresa que realiza concursos públicos, processos seletivos e avaliações em parceria com prefeituras e escolas municipais.

---

## 2️⃣ — Hierarquia de Usuários e Permissões

> O sistema possui **dois níveis de hierarquia**: o primeiro define o que você pode fazer **dentro da plataforma**, o segundo define qual a sua **função dentro de um evento específico**.

---

### 👤 Papéis dentro da plataforma

| Papel | Acesso |
|:----:|--------|
| 🟢 **ADMIN** | **Acesso total.** Pode criar e editar eventos, cadastrar escolas, definir funções, alocar profissionais, gerar convites e ver dados financeiros. |
| 🔵 **FINANCEIRO** | **Visualização e relatórios.** Pode ver informações do evento e gerar relatórios em planilha. ❌ **Não pode** alocar ninguém nem gerenciar convites. |
| 🟡 **PARTICIPANTE** | **Acesso básico.** Pode ver seus eventos, seu perfil e suas informações. |

---

### 🎭 Papéis dentro de um evento

| Papel | Descrição | Pode alocar? | Pode convidar? |
|:-----:|-----------|:------------:|:--------------:|
| 🟣 **GERAL** | Coordenador Geral. Supervisiona todas as escolas e toda a equipe do evento. | ✅ Sim | ✅ Sim |
| 🟠 **LOCAL** | Coordenador de uma escola específica. Cuida da equipe da sua escola. | ✅ Sim (sua escola) | ✅ Sim (limitado) |
| ⚪ **COLABORADOR** | Profissional que trabalha no evento (aplicador, fiscal). ❌ **Não acessa o sistema** — apenas recebe convite por e-mail. | ❌ Não | ❌ Não |
| 🔴 **SCHOOL** | Representante da escola no evento. | ❌ Não | ❌ Não |

---

### 📋 O que cada um pode fazer

> ⚠️ **Importante**: O **COLABORADOR** (simples) **não acessa o sistema**. Ele apenas recebe o convite por e-mail e responde se aceita ou recusa. Por isso, não há permissões de sistema para ele.

| Funcionalidade | 🟢 ADMIN | 🔵 FINANCEIRO | 🟣 GERAL | 🟠 LOCAL |
|----------------|:--------:|:-------------:|:--------:|:--------:|
| Criar ou editar Eventos | ✅ | — | — | — |
| Cadastrar Escolas | ✅ | — | — | — |
| Cadastrar Funções/Cargos | ✅ | — | — | — |
| Cadastrar Colaboradores | ✅ | — | ✅ | ✅ |
| Gerar Convites | ✅ | — | ✅ | ✅ |
| Alocar Coordenadores | ✅ | — | ✅ | — |
| Alocar Colaboradores | ✅ | — | ✅ | ✅ |
| Alocar Candidatos | ✅ | — | — | — |
| Confirmar Presença | ✅ | — | ✅ | ✅ |
| Remover Alocação | ✅ | — | ✅ | ✅ |
| Ver Métricas do Evento | ✅ | ✅ | ✅ | ✅ |
| Gerar Relatório PDF | ✅ | — | ✅ | ✅ |
| Gerar Relatório Planilha | ✅ | ✅ | ✅ | ✅ |
| Anexar Edital | ✅ | — | — | — |
| Editar Próprio Perfil | ✅ | ✅ | ✅ | ✅ |

---

### 🔗 Regras para convidar pessoas

```
ADMIN ────► Qualquer pessoa (GERAL, LOCAL ou COLABORADOR)
GERAL ────► Apenas LOCAL e COLABORADOR
LOCAL ────► Apenas COLABORADOR
COLABORADOR ────► Não pode convidar ninguém
```

---

## 3️⃣ — Fluxo Completo do Sistema (Passo a Passo)

### 📌 Visão Geral

<details>
<summary>👆 Clique para ver o fluxo completo</summary>

```
┌─────────────────────────────────────────────────────────┐
│                   ANTES DO EVENTO                       │
├─────────────────────────────────────────────────────────┤
│                                                         │
│   1️⃣  ADMIN cadastra o Evento                          │
│       │                                                 │
│   2️⃣  ADMIN cadastra os Locais (Escolas) com Salas     │
│       │                                                 │
│   3️⃣  ADMIN cadastra as Funções/Cargos                 │
│       │                                                 │
│   4️⃣  ADMIN/GERAL/LOCAL cadastram Colaboradores        │
│       │                                                 │
│   5️⃣  ADMIN/GERAL/LOCAL enviam Convites                │
│       │                                                 │
│   6️⃣  Colaboradores recebem e-mail e respondem         │
│                                                         │
├─────────────────────────────────────────────────────────┤
│                 ALOCAÇÃO (DISTRIBUIÇÃO)                  │
├─────────────────────────────────────────────────────────┤
│                                                         │
│   7️⃣  ADMIN/GERAL alocam Coordenadores LOCAIS          │
│       │                                                 │
│   8️⃣  ADMIN/GERAL/LOCAL distribuem Colaboradores       │
│       │                                                 │
│   9️⃣  ADMIN aloca Candidatos (alunos) nas Salas        │
│                                                         │
├─────────────────────────────────────────────────────────┤
│                  DURANTE O EVENTO                        │
├─────────────────────────────────────────────────────────┤
│                                                         │
│   🔟  Presença dos Colaboradores é confirmada           │
│                                                         │
├─────────────────────────────────────────────────────────┤
│                  DEPOIS DO EVENTO                        │
├─────────────────────────────────────────────────────────┤
│                                                         │
│   1️⃣1️⃣  Geração de relatórios (PDF ou Planilha)        │
│                                                         │
│   1️⃣2️⃣  Desalocação de colaboradores (se necessário)   │
│                                                         │
└─────────────────────────────────────────────────────────┘
```

</details>

---

### 🪜 Passo a Passo Detalhado

---

#### 👋 PASSO 1 — Entrar no Sistema

| Quem faz | Qualquer usuário cadastrado |
|----------|-----------------------------|
| 🎯 **Objetivo** | Acessar a plataforma |

**Como fazer:**
1. Acesse o endereço do sistema BGTech Flow
2. Na tela de entrada, digite seu **e-mail** e **senha**
3. Clique em **"Entrar"**

**O que acontece:**
- ✅ O sistema confere se seus dados estão corretos
- ✅ Se for o **primeiro acesso**, o sistema vai pedir para você criar uma senha nova
- ✅ Você é direcionado para a tela de **Selecionar Evento**

> **Primeiro Acesso:**
> 1. Aparecerá uma janela de **primeiro acesso**
> 2. Digite a **senha atual** e a **nova senha**
> 3. A senha precisa ter no mínimo **6 caracteres**
> 4. Depois de confirmar, você segue para a tela principal

> **🔑 Esqueceu a senha?**
> 1. Na tela de entrada, clique em **"Esqueceu sua senha?"**
> 2. Informe seu **e-mail**
> 3. Você receberá um **código de 6 números** no e-mail
> 4. Digite o código na tela de verificação
> 5. Crie uma **nova senha**

---

#### 🎯 PASSO 2 — Selecionar um Evento

| Quem faz | Todos os usuários |
|----------|-------------------|
| 🎯 **Objetivo** | Escolher qual evento administrar |

**Como fazer:**
1. Depois de entrar, você será direcionado para a tela **"Selecionar Evento"**
2. Uma lista mostra todos os eventos que você pode acessar
3. **Clique** no evento desejado para trabalhar nele

**O que acontece:**
- O evento escolhido fica como **"evento ativo"**
- O destino após a escolha depende do seu papel:

  | Seu papel | Vai para |
  |:---------:|----------|
  | 🔵 **FINANCEIRO** | Página de **Colaboradores** |
  | 🟢 **ADMIN** / 🟣 **GERAL** / 🟠 **LOCAL** | **Painel Principal** do evento |

---

#### 📊 PASSO 3 — Painel Principal (Acompanhamento de Convites)

| Quem faz | ADMIN, GERAL, LOCAL |
|----------|---------------------|
| 🎯 **Objetivo** | Acompanhar os convites enviados |

**O que é:** O Painel Principal é a primeira tela depois que você seleciona um evento.

**📈 Indicadores:**

| Indicador | O que mostra |
|-----------|--------------|
| 📨 **Convites Enviados** | Total de convites gerados |
| ✅ **Convites Aceitos** | Quantos foram aceitos |
| ⏳ **Convites Pendentes** | Quantos ainda aguardam resposta |
| ❌ **Convites Recusados** | Quantos foram recusados |

**📋 Lista de Convites Enviados:**
Mostra todos os convites que você gerou, com:
- **Nome** do convidado
- **Função** (COLABORADOR, LOCAL, GERAL)
- **Situação** (Pendente, Aceito, Recusado)
- **Data de validade**
- Opção para **reenviar** o convite

> **Regra de visibilidade:**
> - 🟢 **ADMIN**: enxerga **todos** os convites do evento
> - 🟣 **GERAL** / 🟠 **LOCAL**: enxerga apenas os convites que **você mesmo enviou**

---

#### 🏗️ PASSO 4 — Cadastrar um Evento

| Quem faz | 🟢 Somente ADMIN |
|----------|:----------------:|
| 🎯 **Objetivo** | Criar um novo evento no sistema |

**Como fazer:**
1. No menu lateral, clique em **"Eventos"**
2. Clique no botão **"Adicionar Evento"**
3. Preencha o formulário:

   | Campo | Descrição |
   |-------|-----------|
   | 📛 **Nome do evento** | Obrigatório |
   | 📝 **Descrição** | Obrigatório |
   | 🏷️ **Tipo de evento** | Escolha entre os tipos cadastrados |
   | 📅 **Data de início** | Quando começa |
   | 📅 **Data de término** | Quando termina |
   | ⏰ **Horário de início** | Horário de abertura |
   | ⏰ **Horário de término** | Horário de encerramento |
   | 💰 **Valor base** | Quanto o evento pode gastar |
   | 🗺️ **Estados** | Quais estados fazem parte |
   | 🏙️ **Municípios** | Quais cidades participantes |

4. Opcional: anexe o **Edital** do evento (arquivo PDF)
5. Clique em **"Salvar"**

**✏️ Editar Evento:**
1. Na lista de eventos, clique no evento desejado
2. Na página de detalhes, clique em **"Editar"** para alterar os dados
3. É possível mudar os municípios vinculados

**🔗 Vincular ou Desvincular Escolas ao Evento:**
1. Na página de detalhes do evento, vá em **"Locais Cadastrados"**
2. Clique em **"Gerenciar Locais"**
3. Marque ou desmarque as escolas que deseja vincular ou remover
4. Confirme a operação

---

#### 🏫 PASSO 5 — Cadastrar um Local (Escola)

| Quem faz | 🟢 Somente ADMIN |
|----------|:----------------:|
| 🎯 **Objetivo** | Cadastrar uma escola que participará do evento |

**Como fazer:**
1. No menu lateral, clique em **"Locais"**
2. Clique em **"Adicionar Local"**
3. Preencha:

   | Campo | Descrição |
   |-------|-----------|
   | 📛 **Nome do local** | Obrigatório |
   | 🏷️ **Tipo de escola** | Municipal, Estadual, etc. |
   | 🔢 **CNPJ** | Opcional |
   | 📞 **Telefone** | Opcional |
   | 👤 **Nome do gestor** | Obrigatório |
   | 📧 **E-mail do gestor** | Obrigatório |
   | 👥 **Equipe necessária** | Quantas pessoas precisa |
   | 📍 **Endereço** | CEP (preenche automático), Rua, Número, Bairro, Cidade, Estado |

4. Opcional: adicione **Salas** clicando em **"Adicionar Sala"**:

   | Campo | Descrição |
   |-------|-----------|
   | 📛 **Nome** | Nome ou número da sala |
   | 👥 **Capacidade** | Quantas pessoas cabem |
   | 🔑 **Código** | Identificador da sala |
   | 🏢 **Andar** | Térreo, 1º andar, etc. |

5. Clique em **"Salvar"**

**🛠️ Gerenciar Salas:**
Na página de detalhes do local:
- A seção **"Salas Cadastradas"** lista todas as salas
- Você pode **adicionar**, **editar** ou **remover** salas

---

#### 🛠️ PASSO 6 — Cadastrar Funções/Cargos

| Quem faz | 🟢 Somente ADMIN |
|----------|:----------------:|
| 🎯 **Objetivo** | Definir os tipos de trabalho e seus valores |

> As funções (ou cargos) definem os tipos de trabalho que os profissionais vão exercer. Exemplos: "Aplicador", "Fiscal de Sala", "Portaria", "Coordenação".

**Como fazer:**
1. No menu lateral, clique em **"Funções"**
2. Clique em **"Adicionar Função"**
3. Preencha:

   | Campo | Descrição |
   |-------|-----------|
   | 📛 **Nome** | Ex: Aplicador |
   | 📝 **Descrição** | Ex: Aplica a prova na sala |
   | 💰 **Valor** | Quanto a pessoa vai receber |
   | 📍 **Local de atuação** | 🏠 **Sala** ou 🏫 **Escola** |
   | ✅ **Situação** | Ativo ou Inativo |

4. Clique em **"Salvar"**

> ⚠️ **Importante:** Na hora de alocar as pessoas, a função precisa ser compatível:
> - Alocação em **sala** → função com local de atuação **Sala**
> - Alocação em **área externa** → função com local de atuação **Escola**

---

#### 👥 PASSO 7 — Cadastrar Colaboradores

| Quem faz | 🟢 ADMIN, 🟣 GERAL, 🟠 LOCAL |
|----------|:---------------------------:|
| 🎯 **Objetivo** | Cadastrar as pessoas que vão trabalhar no evento |

> Colaboradores são as pessoas que vão trabalhar no evento (aplicadores, fiscais, etc.).

**Como fazer:**
1. No menu lateral, clique em **"Colaboradores"**
2. Clique em **"Adicionar Colaborador"**
3. Preencha:

   | Campo | Obrigatório? |
   |-------|:------------:|
   | 📛 **Nome completo** | ✅ Sim |
   | 🔢 **CPF** | ✅ Sim |
   | 📧 **E-mail** | ⚠️ Sim, se for coordenador (LOCAL ou GERAL) |
   | 📞 **Telefone** | ✅ Sim |
   | 📍 **Endereço** | ❌ Opcional |
   | 🏦 **Dados bancários** | ❌ Opcional (Banco, Agência, Conta, PIX) |

4. Clique em **"Salvar"**

**👁️ Visualizar Colaborador:**
1. Na lista, clique sobre um colaborador para ver os detalhes
2. A página exibe: nome, CPF, e-mail, telefone, endereço e dados bancários

---

#### 📨 PASSO 8 — Enviar Convites

| Quem faz | 🟢 ADMIN, 🟣 GERAL, 🟠 LOCAL |
|----------|:---------------------------:|
| 🎯 **Objetivo** | Convidar um colaborador para participar do evento |

**Quando fazer:** Depois que o colaborador já está cadastrado e o evento está ativo.

**Como fazer:**
1. No **Painel Principal**, clique em **"Convidar Colaborador"**
2. Ou na tela de **Colaboradores**, selecione alguém e clique em **"Convidar"**
3. Aparece uma janela com:

   | Seção | Informação |
   |-------|------------|
   | 📋 **Dados do evento** | Nome, tipo, data e horário (para conferência) |
   | 👤 **Dados do colaborador** | Nome, e-mail, CPF, telefone |
   | 🎭 **Função do colaborador** | Escolha uma: |

   | Opção | Descrição |
   |-------|-----------|
   | ⚪ **Colaborador Simples** | Função operacional |
   | 🟠 **Coordenador Local** | Coordenador de escola |
   | 🟣 **Coordenador Geral** | Coordenador geral |

4. Clique em **"Convidar"**

> ⚠️ **Regras importantes:**
> - Se a função for **GERAL** ou **LOCAL**, o **e-mail é obrigatório**
> - Para **COLABORADOR**, o e-mail é opcional
> - Uma pessoa só pode ser convidada **uma vez** para o mesmo evento
> - O convite **vence em 5 dias**

**O que acontece:**
- O convite fica com status **Pendente**
- Se a pessoa tem e-mail, ela recebe uma mensagem com o link para aceitar ou recusar

---

#### ✅ PASSO 9 — Aceitar ou Recusar um Convite

| Quem faz | Pessoa que recebeu o convite (externo) |
|----------|----------------------------------------|
| 🎯 **Objetivo** | Confirmar ou recusar participação no evento |

**Como fazer:**
1. Você recebe um **e-mail** com o link de confirmação
2. Clique no link. Você será direcionado para a página de confirmação
3. A tela mostra:
   - **"Confirmação de Convite"**
   - Mensagem: *"Você recebeu um convite para participar de um evento. Deseja confirmar sua participação?"*
   - Botões: **✅ "Confirmar"** ou **❌ "Recusar"**
4. Clique em **"Confirmar"** para aceitar ou **"Recusar"** para recusar

**O que acontece ao aceitar:**
- ✅ O convite muda para **Aceito**
- ✅ Você fica vinculado ao evento com a função escolhida
- ✅ Se for coordenador (GERAL ou LOCAL), o sistema cria automaticamente seu acesso à plataforma

**O que acontece ao recusar:**
- ❌ O convite muda para **Recusado**
- ❌ Você não participa do evento

> **⏰ Convite vencido:** Se o convite passou de 5 dias, ele aparece como **Vencido** e não pode mais ser respondido.

> **🔧 Gerenciamento manual (para ADMIN):** O ADMIN pode forçar a aceitação ou recusa de qualquer convite diretamente pelo Painel.

---

#### 👔 PASSO 10 — Alocar Coordenadores Locais

| Quem faz | 🟢 ADMIN, 🟣 GERAL |
|----------|:-----------------:|
| 🎯 **Objetivo** | Vincular coordenadores às escolas |

**Quando fazer:** Depois do evento configurado, escolas vinculadas e pessoas com função LOCAL já terem aceitado o convite.

**Como fazer:**
1. Vá para a página de detalhes do **Local**
2. Na seção **"Alocar Coordenador"**, clique em **"Alocar"**
3. Uma janela aparece com:
   - 📛 Nome do local
   - 👤 Lista de **Coordenadores** disponíveis
   - 💰 Campo de **Remuneração**
4. Selecione o coordenador e informe o valor
5. Clique em **"Salvar"**

**O que acontece:**
- ✅ O coordenador é vinculado à escola
- ✅ Ele aparece na lista **"Coordenadores Alocados"**
- ✅ Para remover, clique no ícone de lixeira 🗑️

> ⚠️ **Regras:**
> - Um coordenador só pode ser alocado **uma vez** por evento em cada escola
> - Apenas **ADMIN** e **GERAL** podem fazer isso
> - **LOCAL** não pode alocar coordenadores

---

#### 🪑 PASSO 11 — Alocar Colaboradores nas Salas

| Quem faz | 🟢 ADMIN, 🟣 GERAL, 🟠 LOCAL |
|----------|:---------------------------:|
| 🎯 **Objetivo** | Distribuir os colaboradores nas salas ou área externa |

**Quando fazer:** Depois que os colaboradores aceitaram o convite.

> **Há duas formas de alocação:**

**📌 Alocação em Sala:**
1. Vá para a página de detalhes do **Local**
2. Na seção **"Salas Cadastradas"**, localize a sala desejada
3. Clique em **"Alocar"**
4. Escolha:
   - 👤 **Colaborador** disponível
   - 🛠️ **Função** (apenas funções com local de atuação **Sala**)

**📌 Alocação em Área Externa (sem sala):**
1. Na seção **"Alocação na Área Externa"**, clique em **"Alocar"**
2. Escolha:
   - 👤 **Colaborador** disponível
   - 🛠️ **Função** (apenas funções com local de atuação **Escola**)

**O que acontece:**
- ✅ O colaborador é vinculado ao evento, escola e sala
- ✅ A função escolhida é registrada
- ✅ Ele aparece na lista **"Colaboradores Alocados"**

> ⚠️ **Regras:**
> - O número de colaboradores **não pode passar** do limite definido na escola
> - Funções de **Sala** só podem ser usadas em salas
> - Funções de **Escola** só podem ser usadas na área externa
> - 🔵 **FINANCEIRO** não vê as opções de alocação

---

#### 🎒 PASSO 12 — Alocar Candidatos (Participantes)

| Quem faz | 🟢 Somente ADMIN |
|----------|:----------------:|
| 🎯 **Objetivo** | Alocar os participantes nas salas de prova |

> Candidatos são os participantes que vão fazer a prova ou avaliação.

**Como fazer:**
1. No menu lateral, clique em **"Candidatos"**
2. Faça o **upload de uma planilha** (.xlsx) com os dados:

   | Dado | Exemplo |
   |------|---------|
   | Nome completo | Maria da Silva |
   | CPF | 123.456.789-00 |
   | E-mail | maria@email.com |
   | Telefone | (11) 99999-9999 |
   | Número de inscrição | 2024001 |

3. Após o upload, os candidatos aparecem na lista

**Alocar um candidato:**
1. Na lista, clique em **"Alocar"** ao lado do candidato
2. Escolha:
   - 📋 **Evento**
   - 🏫 **Local (Escola)**
   - 🚪 **Sala** (opcional)
3. O sistema verifica:
   - ✅ Se o candidato já não foi alocado antes
   - ✅ Se a sala tem espaço disponível
4. Clique em **"Confirmar"**

**O que acontece:**
- ✅ O candidato é vinculado ao evento, escola e sala
- ✅ Se tiver e-mail, ele recebe as informações da escola onde fará a prova

---

#### ✅ PASSO 13 — Confirmar Presença

| Quem faz | 🟢 ADMIN, 🟣 GERAL, 🟠 LOCAL |
|----------|:---------------------------:|
| 🎯 **Objetivo** | Registrar quais colaboradores compareceram |

**Quando fazer:** Durante o evento.

**Como fazer:**
1. Vá para a página de detalhes do **Local**
2. Na seção **"Colaboradores Alocados"**, localize o colaborador
3. Clique em **"Confirmar Presença"**

**O que acontece:**
- ✅ O status do colaborador muda para **"Presente"**
- ✅ Isso pode ser usado para **controle de pagamento**

---

#### 🗑️ PASSO 14 — Remover Alocação

| Quem faz | 🟢 ADMIN, 🟣 GERAL, 🟠 LOCAL |
|----------|:---------------------------:|
| 🎯 **Objetivo** | Desvincular um colaborador ou coordenador |

**Quando fazer:** Quando um colaborador ou coordenador precisa ser removido.

**👤 Para remover um Colaborador:**
1. Vá para a página de detalhes do **Local**
2. Na seção **"Colaboradores Alocados"**, localize a pessoa
3. Clique no ícone de **lixeira** 🗑️

**👔 Para remover um Coordenador:**
1. Na seção **"Coordenadores Alocados"**, localize o coordenador
2. Clique no ícone de **lixeira** 🗑️

**O que acontece:**
- ✅ A pessoa é desvinculada daquela função
- ✅ Ela fica disponível para ser alocada em outro lugar

---

#### 📄 PASSO 15 — Gerar Relatórios

| Quem faz | 🟢 ADMIN, 🟣 GERAL, 🟠 LOCAL (PDF) / 🔵 FINANCEIRO (Planilha) |
|----------|:------------------------------------------------------------:|
| 🎯 **Objetivo** | Gerar relatórios para acompanhamento ou prestação de contas |

**Quando fazer:** A qualquer momento, ou no final do evento.

**Como fazer:**
1. Vá para a página de detalhes do **Local**
2. Na seção **"Colaboradores Alocados"**, clique em **"Baixar Relatório"**

---

**📄 Relatório em PDF** *(para ADMIN, GERAL, LOCAL)*

| Item | Descrição |
|------|-----------|
| 🏫 **Cabeçalho** | Nome da escola, tipo, CNPJ e telefone |
| 📋 **Evento** | Nome do evento |
| 👥 **Colaboradores** | Lista dos alocados, funções e salas |
| 🖨️ **Rodapé** | Data de impressão e quem gerou |

**📊 Relatório em Planilha (.xlsx)** *(para FINANCEIRO)*

| Item | Descrição |
|------|-----------|
| 📋 **Dados** | Dados organizados em colunas |
| 💰 **Finalidade** | Controle financeiro e folha de pagamento |

---

#### 👤 PASSO 16 — Gerenciar seu Perfil

| Quem faz | 🟢 ADMIN, 🟣 GERAL, 🟠 LOCAL, 🔵 FINANCEIRO |
|----------|:------------------------------------------:|
| 🎯 **Objetivo** | Visualizar e editar seus dados pessoais |

**Como fazer:**
1. No menu lateral, clique em **"Perfil"**
2. Visualize suas informações:

   | Informação | Descrição |
   |------------|-----------|
   | 📛 **Nome** | Seu nome |
   | 📧 **E-mail** | Seu e-mail |
   | 🔢 **CPF** | Seu CPF |
   | 📞 **Telefone** | Seu telefone |
   | 🏠 **Endereço** | Seu endereço (se cadastrado) |
   | 🏦 **Dados bancários** | Banco, agência, conta (se cadastrado) |

3. Clique em **"Editar Perfil"** para alterar seus dados
4. Clique em **"Alterar Senha"** para mudar a senha

---

#### 📊 PASSO 17 — Visualizar Informações do Evento

| Quem faz | 🟢 ADMIN, 🟣 GERAL, 🟠 LOCAL, 🔵 FINANCEIRO |
|----------|:------------------------------------------:|
| 🎯 **Objetivo** | Acompanhar todas as informações do evento |

**Como fazer:**
1. Na lista de eventos, clique sobre um evento
2. A página de detalhes mostra:

---

**📋 Detalhes do Evento**

| Informação | Descrição |
|------------|-----------|
| 📛 **Nome** | Nome do evento |
| 📝 **Descrição** | Descrição do evento |
| 🏷️ **Tipo** | Tipo do evento |
| 💰 **Valor previsto** | Valor base do evento (🟢 visível apenas para ADMIN) |
| 💰 **Valor gasto** | Valor já utilizado (🟢 visível apenas para ADMIN) |
| 📅 **Período** | Data de início e término |
| ⏰ **Horário** | Horário de início e término |
| 🗺️ **Municípios** | Cidades participantes |
| 📄 **Edital** | PDF para visualizar ou baixar |

---

**🏫 Locais Cadastrados**

| Informação | Descrição |
|------------|-----------|
| 📋 **Lista** | Escolas vinculadas ao evento |
| 🏷️ **Tipo** | Tipo de cada escola |
| 🚪 **Salas** | Número de salas por escola |
| 👥 **Capacidade** | Capacidade total por escola |

---

**👥 Colaboradores do Evento**

| Informação | Descrição |
|------------|-----------|
| 📋 **Lista** | Todos os colaboradores vinculados ao evento |

---

**📊 Resumo de Locais**

| Indicador | Descrição |
|-----------|-----------|
| 🚪 **Total de Salas** | Soma de todas as salas |
| 👥 **Capacidade Total** | Soma da capacidade de todas as salas |
| 🏫 **Locais Participantes** | Quantidade de escolas |

**📊 Resumo de Colaboradores**

| Indicador | Descrição |
|-----------|-----------|
| 👥 **Colaboradores Necessários** | Total de profissionais precisos |
| ✅ **Colaboradores Disponíveis** | Quantos aceitaram o convite |
| 📌 **Colaboradores Alocados** | Quantos já foram distribuídos |

---

## 4️⃣ — Módulo de Autenticação

### 🔑 Entrar
- Informe seu **e-mail** e **senha** na tela inicial
- Se os dados estiverem corretos, você entra no sistema
- Se for o **primeiro acesso**, será solicitada a criação de uma nova senha

### 🚪 Sair
- Clique na opção de sair no menu lateral ou no seu perfil
- Você volta para a tela de entrada

### 🔒 Alterar Senha
1. Acesse seu **Perfil**
2. Clique em **"Alterar Senha"**
3. Digite a senha atual e a nova senha

### 🔄 Recuperar Senha

| Etapa | Ação |
|:----:|------|
| 1️⃣ | Solicite o código informando seu **e-mail** |
| 2️⃣ | Você recebe um **código de 6 números** |
| 3️⃣ | Digite o código na tela de verificação |
| 4️⃣ | Crie uma **nova senha** |

---

## 5️⃣ — Módulo de Eventos

### 📋 Dados de um Evento

| Campo | Descrição | Obrigatório |
|-------|-----------|:-----------:|
| 📛 **Nome** | Nome do evento | ✅ |
| 📝 **Descrição** | Descrição do evento | ✅ |
| 🏷️ **Tipo** | Concurso, Processo Seletivo, etc. | ✅ |
| 📅 **Data de início** | Quando começa | ✅ |
| 📅 **Data de término** | Quando termina | ✅ |
| ⏰ **Horário de início** | Horário de abertura | ✅ |
| ⏰ **Horário de término** | Horário de encerramento | ✅ |
| 💰 **Valor base** | Orçamento previsto | ✅ |
| 🗺️ **Localidades** | Estados e municípios participantes | ✅ |
| 📄 **Edital** | Arquivo PDF com as regras | ❌ |

### 🏷️ Tipos de Evento
Servem para categorizar os eventos. Exemplos: *"Concurso Público"*, *"Processo Seletivo"*, *"Avaliação Diagnóstica"*.

### 🗺️ Estados e Municípios
O evento pode abranger vários estados e municípios. A lista é carregada automaticamente com base nos dados oficiais.

---

## 6️⃣ — Módulo de Locais (Escolas)

### 📋 Dados de um Local

| Campo | Descrição | Obrigatório |
|-------|-----------|:-----------:|
| 📛 **Nome** | Nome da escola | ✅ |
| 🏷️ **Tipo** | Municipal, Estadual, etc. | ✅ |
| 🔢 **CNPJ** | CNPJ da escola | ❌ |
| 📞 **Telefone** | Telefone de contato | ❌ |
| 👤 **Nome do gestor** | Responsável pela escola | ✅ |
| 📧 **E-mail do gestor** | E-mail do responsável | ✅ |
| 👥 **Equipe necessária** | Quantos colaboradores precisa | ✅ |
| 📍 **Endereço** | Endereço completo | ✅ |
| 🚪 **Salas** | Lista de salas da escola | ❌ |

### 🚪 Dados de uma Sala

| Campo | Descrição | Obrigatório |
|-------|-----------|:-----------:|
| 📛 **Nome** | Nome ou número da sala | ✅ |
| 👥 **Capacidade** | Máximo de pessoas | ✅ |
| 🔑 **Código** | Identificador da sala | ✅ |
| 🏢 **Andar** | Andar onde fica | ✅ |

### 🏢 Andares
Gerenciados pelo ADMIN. Exemplos: *"Térreo"*, *"1º Andar"*, *"2º Andar"*.

---

## 7️⃣ — Módulo de Colaboradores

### 📋 Dados do Colaborador

| Campo | Descrição | Obrigatório |
|-------|-----------|:-----------:|
| 📛 **Nome completo** | Nome da pessoa | ✅ |
| 🔢 **CPF** | CPF | ✅ |
| 📧 **E-mail** | E-mail | ⚠️ Sim, se for coordenador |
| 📞 **Telefone** | Telefone de contato | ✅ |
| 📍 **Endereço** | Endereço completo | ❌ |
| 🏦 **Banco** | Código do banco | ❌ |
| 🏦 **Agência** | Agência bancária | ❌ |
| 🏦 **Conta** | Número da conta | ❌ |
| 💳 **Chave PIX** | Chave para pagamento | ❌ |

---

## 8️⃣ — Módulo de Convites

### 📌 Situações do Convite

| Situação | Ícone | O que significa |
|:--------:|:----:|-----------------|
| **Pendente** | ⏳ | Aguardando resposta da pessoa |
| **Aceito** | ✅ | A pessoa aceitou participar |
| **Recusado** | ❌ | A pessoa recusou |
| **Vencido** | ⏰ | O convite passou do prazo (5 dias) |

### 🔄 Como funciona o convite

```
1️⃣ ADMIN/GERAL/LOCAL envia convite
        │
        ▼
2️⃣ Pessoa recebe e-mail com link
        │
        ▼
3️⃣ Pessoa acessa o link
        │
        ├──► ✅ Aceita → Vinculada ao evento
        │
        └──► ❌ Recusa → Não participa
        │
4️⃣ Se não responder em 5 dias → ⏰ Convite vence
```

### 🔗 Quem pode convidar quem

```
ADMIN ──────────────────► Qualquer função
GERAL ──────────────────► LOCAL e COLABORADOR
LOCAL ──────────────────► Apenas COLABORADOR
COLABORADOR ────────────► Não pode convidar
```

---

## 9️⃣ — Módulo de Alocação

### 📌 Tipos de Alocação

| Tipo | Descrição | Quem faz |
|:----:|-----------|:--------:|
| 👔 **Coordenador** | Vincula um coordenador LOCAL a uma escola + remuneração | 🟢 ADMIN, 🟣 GERAL |
| 🪑 **Colaborador em Sala** | Vincula colaborador a uma sala específica | 🟢 ADMIN, 🟣 GERAL, 🟠 LOCAL |
| 🏫 **Colaborador na Área Externa** | Vincula colaborador à escola (sem sala) | 🟢 ADMIN, 🟣 GERAL, 🟠 LOCAL |
| 🎒 **Candidato** | Vincula candidato a evento, escola e sala | 🟢 ADMIN |

### ✅ Presença
- Marcada individualmente para cada colaborador
- Usada para **controle de pagamento**

### 🗑️ Remover Alocação
- Remove o vínculo da pessoa
- Libera a vaga para outra pessoa

---

## 🔟 — Módulo de Candidatos

### 📋 Dados do Candidato

| Campo | Descrição |
|-------|-----------|
| 📛 **Nome completo** | Nome do candidato |
| 🔢 **CPF** | CPF |
| 📧 **E-mail** | E-mail do candidato |
| 📞 **Telefone** | Telefone |
| 🔑 **Número de inscrição** | Número da inscrição |
| 👨 **Nome do pai** | Nome do pai |
| 👩 **Nome da mãe** | Nome da mãe |
| 🎂 **Data de nascimento** | Data de nascimento |

### 📥 Importação em Lote
- Formato: **planilha Excel** (.xlsx)
- Você pode baixar um **modelo pronto** para preencher

### 📌 Alocação de Candidatos
- Feita **um por um** pela tela
- O sistema verifica a **capacidade da sala**
- Se tiver e-mail, o candidato recebe a **informação do local da prova**

---

## 1️⃣1️⃣ — Módulo de Funções/Cargos

### 📋 Dados da Função

| Campo | Descrição |
|-------|-----------|
| 📛 **Nome** | Nome da função (ex: Aplicador) |
| 📝 **Descrição** | O que a pessoa vai fazer |
| 💰 **Valor** | Quanto vai receber |
| 📍 **Local de atuação** | 🏠 Sala ou 🏫 Escola |
| ✅ **Situação** | Ativo ou Inativo |

### 📍 Locais de Atuação

| Local | Descrição | Exemplos |
|:-----:|-----------|----------|
| 🏠 **Sala** | Funções dentro da sala de aula | Aplicador, Fiscal de Sala |
| 🏫 **Escola** | Funções na área externa | Portaria, Coordenação Externa |

---

## 1️⃣2️⃣ — Módulo de Relatórios

### 📄 Relatório em PDF
Documento formatado contendo:

| Item | Descrição |
|------|-----------|
| 🏫 **Cabeçalho** | Nome da escola, tipo, CNPJ, telefone |
| 📋 **Corpo** | Nome do evento + lista de colaboradores com funções e salas |
| 🖨️ **Rodapé** | Data de impressão e usuário que gerou |

### 📊 Relatório em Planilha (Excel)
Arquivo com dados organizados em colunas, ideal para:
- 💰 Controle financeiro
- 📋 Folha de pagamento
- 🔄 Processamento de dados

---

## 1️⃣3️⃣ — Glossário

| Termo | 🔤 Significado |
|-------|----------------|
| **BGTech Flow** | Nome do sistema |
| **Consulpam** | Empresa que utiliza o sistema |
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

<p align="center">
  <strong>Documentação gerada em Junho de 2026</strong><br>
  <em>Sistema BGTech Flow v1.0</em><br>
  Desenvolvido por <strong>BGTech</strong>
</p>
