# 🏅 SGO - Sistema de Gestão das Olimípíadas

Este é um reposítorio de Projeto de Software para um sistema web de gestão de olimpíadas, documentando  funcionalidades como gerenciamento de competições, inscrições de atletas. alocação de locais para provas e controle de resultados.

Este documento descreve a documentação do projeto, incluindo histórias de usuário e modelagem do sistema via diagramas.

## Histórias de Usuário

---

### 📋 Cadastro de Modalidades

**US01** — *Como instituição gestora das olimpíadas, quero poder cadastrar modalidades de esporte para serem disputadas em competições.*

**Critérios de Aceitação:**
A instituição informará o nome da modalidade e descrição, e ela será inserida na lista de modalidades.

---

### 🌍 Cadastro de Equipes

**US02** — *Como representante da equipe técnica do meu país, quero cadastrar o meu país nas olimpíadas.*

**Critérios de Aceitação:**
As equipes devem se cadastrar nas olimpíadas, informando sua nacionalidade. Só pode haver uma equipe cadastrada por país.

---

### 🏃 Cadastro de Atletas

**US03** — *Como atleta, quero poder me cadastrar no sistema para que possa me inscrever em competições.*

**Critérios de Aceitação:**
O atleta informará o seu nome, email, senha, nacionalidade e as modalidades que joga. Após o cadastro, o atleta será inserido na lista de atletas do seu país para cada uma das suas modalidades.

---

### 🏟️ Cadastro de Competições

**US04** — *Como instituição gestora das olimpíadas, quero poder cadastrar competições, informando o nome da modalidade, a data, horário e local da competição, para que os atletas se inscrevam.*

**Critérios de Aceitação:**
A instituição deve cadastrar a competição por um formulário com nome da modalidade, data, hora e local. Será criada uma lista de atletas vazia, que será preenchida à medida que os atletas se cadastrem na competição.

---

### 📍 Alocação de Locais

**US05** — *Como atleta, representante da equipe técnica ou espectador, quero ter certeza de que não haja duas competições agendadas para acontecer no mesmo horário e no mesmo local.*

**Critérios de Aceitação:**
Uma competição não pode ser cadastrada caso outra competição no mesmo local já tenha sido agendada para a mesma data e horário.

---

### 🏅 Controle de Resultados

**US06** — *Como instituição gestora das olimpíadas, quero poder registrar os resultados das competições, incluindo o atleta vencedor, o segundo e o terceiro colocado.*

**Critérios de Aceitação:**
Após o término da competição de acordo com o seu horário, a instituição poderá confirmar o término da competição e registrar os seus resultados, selecionando o primeiro, segundo e terceiro colocado na lista de atletas participantes.

---

**US07** — *Como atleta, quero receber medalhas com base na minha colocação na competição.*

**Critérios de Aceitação:**
Após o registro dos resultados, o primeiro colocado terá a sua quantidade de medalhas de ouro aumentada em 1, assim como o segundo e o terceiro colocado com a sua quantidade de medalhas de prata e bronze, respectivamente.

---

**US08** — *Como representante da equipe técnica, quero que as medalhas conquistadas por cada atleta contribuam com o total de medalhas da equipe, na intenção de criar um ranking entre os países participantes da olimpíada.*

**Critérios de Aceitação:**
Após o registro dos resultados, as medalhas conquistadas pelos atletas serão adicionadas ao total de medalhas de ouro, prata ou bronze da equipe, de acordo com a colocação dos seus atletas.

---

### 📊 Relatórios de Medalhas

**US09** — *Como instituição gestora das olimpíadas, quero que sejam produzidos relatórios de medalhas, informando as medalhas conquistadas por cada país e uma classificação em ranking dos países.*

**Critérios de Aceitação:**
As equipes serão inseridas em uma página de classificação baseada na quantidade de medalhas, indicando o primeiro, segundo e terceiro país que obteve o melhor resultado nas olimpíadas.

---


