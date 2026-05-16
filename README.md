# 🏅 SGO - Sistema de Gestão das Olimpíadas

Este é um repositório de Projeto de Software para um sistema web de gestão de olimpíadas, documentando funcionalidades como gerenciamento de competições, inscrições de atletas, alocação de locais para provas e controle de resultados.

Este documento descreve a documentação do projeto, incluindo histórias de usuário e modelagem do sistema via diagramas.

## Histórias de Usuário

---

### 📋 Cadastro de Modalidades

**US01** — *Como administrador das olimpíadas, quero poder cadastrar modalidades de esporte para serem disputadas em competições.*

**Critérios de Aceitação:**
O administrador informará o nome da modalidade e descrição, e ela será inserida na lista de modalidades.

---

### 🌍 Cadastro de Equipes

**US02** — *Como representante da equipe técnica do meu país, quero cadastrar o meu país nas olimpíadas.*

**Critérios de Aceitação:**
As equipes devem se cadastrar nas olimpíadas, informando sua nacionalidade. Só pode haver uma equipe cadastrada por país.

---

### 🏃 Cadastro de Atletas

**US03** — *Como atleta, quero poder me cadastrar no sistema para que possa me inscrever em competições.*

**Critérios de Aceitação:**
O atleta informará o seu nome, email, senha, nacionalidade e as modalidades que pratica. Após o cadastro, o atleta será inserido na lista de atletas do seu país para cada uma das suas modalidades.

---

### 🏟️ Cadastro de Competições

**US04** — *Como administrador das olimpíadas, quero poder cadastrar competições, informando o nome da modalidade, a data, horário e local da competição, para que os atletas se inscrevam.*

**Critérios de Aceitação:**
O administrador deve cadastrar a competição por um formulário com nome da modalidade, data, hora e local. Será criada uma lista de atletas vazia, que será preenchida à medida que os atletas se cadastrem na competição.

---

### 📍 Alocação de Locais

**US05** — *Como atleta, representante da equipe técnica ou espectador, quero ter certeza de que não haja duas competições agendadas para acontecer no mesmo horário e no mesmo local.*

**Critérios de Aceitação:**
Uma competição não pode ser cadastrada caso outra competição no mesmo local já tenha sido agendada para a mesma data e horário.

---

### 🏃 Inscrição e Controle de Atletas

**US06** — *Como atleta, quero poder me inscrever nas competições que quero participar.*

**Critérios de Aceitação:**
Atletas poderão se inscrever em competições específicas, selecionando a competição e clicando em "inscrever".

**US07** — *Como administrador, quero que os atletas atendam a todos os critérios da competição para que possam participar, na intenção de garantir que sejam justas.*

**Critérios de Aceitação:**
Atletas não poderão participar em competições caso não pratiquem a modalidade da competição ou a modalidade for dedicada à outra categoria de atleta.

---

### 🏅 Controle de Resultados

**US08** — *Como administrador das olimpíadas, quero poder registrar os resultados das competições, incluindo o atleta vencedor, o segundo e o terceiro colocado.*

**Critérios de Aceitação:**
Após o término da competição de acordo com o seu horário, o administrador poderá confirmar o término da competição e registrar os seus resultados, selecionando o primeiro, segundo e terceiro colocado na lista de atletas participantes.

---

**US09** — *Como atleta, quero receber medalhas com base na minha colocação na competição.*

**Critérios de Aceitação:**
Após o registro dos resultados, o primeiro colocado terá a sua quantidade de medalhas de ouro aumentada em 1, assim como o segundo e o terceiro colocado com a sua quantidade de medalhas de prata e bronze, respectivamente.

---

**US10** — *Como representante da equipe técnica, quero que as medalhas conquistadas por cada atleta contribuam com o total de medalhas da equipe, na intenção de criar um ranking entre os países participantes da olimpíada.*

**Critérios de Aceitação:**
Após o registro dos resultados, as medalhas conquistadas pelos atletas serão adicionadas ao total de medalhas de ouro, prata ou bronze da equipe, de acordo com a colocação dos seus atletas.

---

### 📊 Relatórios de Medalhas

**US11** — *Como administrador das olimpíadas, quero que sejam produzidos relatórios de medalhas, informando as medalhas conquistadas por cada país e uma classificação em ranking dos países.*

**Critérios de Aceitação:**
As equipes serão inseridas em uma página de classificação baseada na quantidade de medalhas, indicando o primeiro, segundo e terceiro país que obteve o melhor resultado nas olimpíadas.

---

## Diagrama de Casos de Uso

O diagrama de casos de uso descreve as interações entre os atores do sistema e as funcionalidades que cada um pode exercer. Os três atores principais — Administrador, Atleta e País — possuem perfis de acesso distintos, refletindo a separação de responsabilidades modelada nas classes `Admin`, `Atleta` e `Pais`. Um quarto ator, o Sistema (SGO), representa os processos automatizados que ocorrem sem interação humana direta, como o controle do tempo das competições via `GerenciadorTempo`.

![Diagrama de Casos de Uso](./docs/SGO%20-%20Diagrama%20de%20Casos%20de%20Uso.png)

### 🧍 Atores

- **Administrador**: Usuário privilegiado responsável pela gestão completa das olimpíadas. Corresponde à classe `Admin`, subclasse de `Usuario`. É o único ator capaz de cadastrar olimpíadas, competições, modalidades e registrar resultados.
- **Atleta**: Usuário que representa um esportista participante das olimpíadas. Corresponde à classe `Atleta`, subclasse de `UsuarioOlimpico`. Pode se inscrever em competições, consultar seu histórico e acompanhar suas medalhas.
- **País**: Usuário que representa a equipe técnica de um país participante. Corresponde à classe `Pais`, subclasse de `UsuarioOlimpico`. Gerencia os atletas vinculados ao seu país e acompanha o placar de medalhas da equipe.
- **Sistema (SGO)**: Ator secundário que representa os processos automatizados do sistema, como o controle de tempo das competições e o registro automático de prorrogações, executados pela classe `GerenciadorTempo` sem intervenção humana.

### 🗨️ Casos de Uso

- **UC01 — Cadastrar Olimpíada**: Permite ao Administrador criar uma nova edição das olimpíadas, informando o ano da olimpíada. Corresponde ao construtor de `Olimpiada` e ao método `cadastrarOlimpiada()` de `Admin`.
- **UC02 — Cadastrar Modalidade**: Permite ao Administrador registrar uma modalidade esportiva com nome, descrição, tipo, gênero (competição feminina, masculina ou mista), número de atletas e duração. Corresponde à criação de instâncias de `Modalidade`.
- **UC03 — Cadastrar Competição**: Permite ao Administrador criar uma competição vinculada a uma modalidade, data, horário e local. Inclui obrigatoriamente a verificação e reserva do local via `AlocadorLocal`, impedindo conflitos de horário e espaço (US05).
- **UC04 — Inscrever-se em Competição**: Permite ao Atleta se inscrever em uma competição disponível. O sistema valida se o atleta pratica a modalidade da competição e se atende aos critérios de categoria (US06, US07), correspondendo ao método `inscreverCompetição()` de `Atleta`.
- **UC05 — Cancelar Inscrição**: Permite ao Atleta cancelar sua participação em uma competição na qual estava inscrito, correspondendo ao método `cancelarInscricao()` de `Atleta`.
- **UC06 — Registrar Resultado da Competição**: Permite ao Administrador finalizar uma competição e registrar os três primeiros colocados. Aciona automaticamente a distribuição de medalhas para os atletas (US08, US09) e atualiza o placar do país (US10), via `Resultado` e `MarcadorMedalhas`.
- **UC07 — Consultar Placar de Medalhas**: Permite ao Administrador e ao País visualizar o ranking de medalhas por equipe, correspondendo ao método `placarAtual()` de `Olimpiada` (US11).
- **UC08 — Gerenciar Tempo da Competição**: Agrupa as operações de controle de tempo executadas pelo Administrador e pelo Sistema: pausar, retomar e prorrogar uma competição em andamento, correspondendo aos métodos `pausar()`, `retomar()` e `prorrogar()` de `Competicao` e `GerenciadorTempo`.

---

## Diagrama de Classes

O diagrama de classes modela os dados do sistema dividindo-os em módulos, cada um com seus atributos e métodos. Este é o diagrama de classes que representa o sistema projetado:

![Diagrama de Classes](./docs/SGO%20-%20Diagrama%20de%20Classes.png)

### Classes

- `Usuario`: É uma classe abstrata que existe para abstrair a lógica compartilhada por todos os tipos de usuário no sistema, como os dados de email e senha para efetuar o cadastro e login.
- `Admin`: Representa o usuário administrador único, que gerencia as olimpíadas. É uma subclasse de `Usuario`.
- `UsuarioOlimpico`: Uma outra classe abstrata que herda de `Usuario`. Representa um usuário que possui lógica diretamente relacionada às competições da olimpíada, tais como controle de medalhas via composição com `MarcadorMedalhas`.
- `Atleta`: Subclasse de `UsuarioOlimpico` que representa um atleta que participa de competições representando um país. Armazena as modalidades praticadas e o histórico de competições.
- `Pais`: Outra subclasse de `UsuarioOlimpico` que representa a equipe de um país nas olimpíadas. Só pode existir uma equipe para cada país.
- `Olimpiada`: Agrega as competições e os países participantes de uma edição dos jogos. Expõe o placar consolidado de medalhas por país.
- `Competicao`: Entidade central do domínio. Reúne a modalidade, o local alocado, os atletas inscritos, o gerenciador de tempo e o resultado final.
- `Modalidade`: Record imutável que descreve as regras de uma prova: tipo olímpico, gênero, número de atletas, duração e possibilidade de prorrogação.
- `Local`: Representa o espaço físico onde uma competição ocorre. Controla sua disponibilidade por data e horário para evitar conflitos de alocação.
- `AlocadorLocal`: Responsável por verificar a disponibilidade de um local e efetuar sua reserva para uma competição, desacoplando essa lógica de `Competicao`.
- `GerenciadorTempo`: Controla o ciclo de tempo de uma competição: tempo decorrido, estado de pausa e prorrogações. Opera de forma autônoma após ser iniciado.
- `Resultado`: Value object imutável que registra o placar final de uma competição, com o mapeamento de atletas para suas colocações.
- `MarcadorMedalhas`: Componente compartilhado por composição entre `Atleta` e `Pais`. Centraliza a contagem de medalhas de ouro, prata e bronze, evitando duplicação de lógica entre as duas classes.
- `EMedalha`: Enum que define os tipos de medalha possíveis: `OURO`, `PRATA` e `BRONZE`.
- `ETipoOlimpiada`: Enum que define o tipo da modalidade em relação ao clima/estação: `VERÃO` ou `INVERNO`. Permite que olimpíadas não sejam limitadas pelo tipo como seria caso esse atributo fosse parte da classe Olimpiada. Uma olimpíada de verão pode ter algumas modalidades de inverno, e vice-versa.

---

## Diagrama de Pacotes

O diagrama de pacotes organiza as classes do sistema em camadas com responsabilidades bem definidas, seguindo o princípio de que dependências devem sempre apontar de camadas externas para camadas internas — nunca ao contrário. Essa estrutura reduz o acoplamento entre módulos e facilita a substituição de implementações sem impacto nas regras de negócio.

![Diagrama de Pacotes](./docs/SGO%20-%20Diagrama%20de%20Pacotes.png)

### Pacotes

- **`Apresentação/Acesso`**: Camada de acesso ao sistema. Contém os pontos de entrada para cada perfil de usuário: `Admin` em `.admin`, `UsuarioOlimpico` em `.atleta` e a lógica de autenticação em `.auth`. Cada sub-pacote é isolado para que alterações no fluxo de um perfil não afetem os demais.
- **`Aplicação/Serviços`**: Camada de serviços de aplicação. Orquestra o domínio sem conter regras de negócio próprias. Reúne os serviços identificados no sistema: `Olimpiada`, `Competiacao`, `Modalidade`, `Local`, `AlocadorLocal`, `Inscricao` e o serviço de controle de tempo. Esta camada pode chamar `Domínio/Entidades`, mas nunca o inverso.
- **`Domínio/Entidades`**: Camada de domínio puro. Subdividida em dois grupos: as entidades e agregados (`olimpiada`, `competicao`, `atleta`, `pais`, `local`), que encapsulam as regras de negócio do sistema; e os contratos que definem o vocabulário comum usado por múltiplos módulos sem criar dependências cruzadas entre eles.
- **`DTO`**: Camada que contém DTOs divididos em `DTO.request` e `DTO.response`, para desacoplar a lógica de domínio da implementação das entidades no BD, e aumentar a segurança ao restringir as informações acessadas pelas camadas mais altas.
- **`Infraestrutura`**: Camada de infraestrutura. Contém os detalhes técnicos que podem mudar sem afetar nenhuma regra de negócio: como `.persistence` para acesso ao banco de dados.

---

## Diagrama de Componentes e Implantação

O diagrama de componentes e implantação descreve como os módulos do sistema se organizam em unidades deployáveis e como essas unidades se comunicam em ambiente de produção. A arquitetura adota um modelo de microsserviços com API Gateway, onde cada serviço de domínio é implantado de forma independente em seu próprio container, orquestrado por Kubernetes, e exposto ao mundo externo por meio de uma camada de gateway dedicada por perfil de usuário.

![Diagrama de Componentes e Implantação](./docs/SGO%20-%20Diagrama%20de%20Componentes%20e%20Implantação.png)

### 🛠️ Tecnologias Escolhidas

#### Dispositivo do Usuário — Navegador — Front-End

- **Linguagem/Superset:** TypeScript ES6+
- **Framework Front-End:** Angular

O Angular foi escolhido por oferecer uma estrutura opinada e consistente com a arquitetura do restante do sistema. O sistema possui três perfis de usuário com fluxos e permissões radicalmente distintos (Administrador, Atleta e País), o que se encaixa com naturalidade no sistema de módulos com lazy loading do Angular — cada perfil é carregado sob demanda como um módulo isolado. Os interceptors HTTP nativos do framework simplificam a integração com a camada de autenticação dos gateways, adicionando o token JWT a todas as requisições de forma transparente. Por ser um sistema interno sem requisitos de SEO, as vantagens de Server-Side Rendering de frameworks alternativos não se aplicam.

#### Servidor da Aplicação — API REST Layer

- **Linguagem:** Go
- **Framework REST:** Gin

A API REST Layer atua como ponto de entrada único do sistema, responsável exclusivamente por rotear requisições do navegador para o gateway correto com base no perfil do usuário. Por ser uma camada de roteamento sem lógica de domínio, ela se beneficia diretamente das características de Go: alta performance em operações de I/O, baixo consumo de memória e tempo de inicialização reduzido. O framework Gin oferece roteamento eficiente e suporte a proxy reverso com poucas linhas de código. A escolha de Go aqui também garante consistência operacional com os servidores de gateway, unificando o runtime de toda a camada de infraestrutura de rede em uma única linguagem.

#### Servidores de Gateway — API Gateway

- **Linguagem:** Go

Os três gateways (Auth. Admin, Auth. Atleta e Auth. País) são responsáveis por autenticação, autorização e roteamento das requisições para os microsserviços correspondentes. Esse tipo de trabalho — validação de tokens JWT, aplicação de rate limiting e repasse de requisições HTTP — é intensivo em I/O e se beneficia diretamente do modelo de concorrência de Go com goroutines. O uso de Go também mantém a consistência com a API REST Layer, permitindo que toda a camada de entrada do sistema compartilhe o mesmo runtime, pipeline de build e imagens de container, reduzindo o overhead operacional do time.

#### Cluster de Microsserviços

- **Orquestração de containers:** Kubernetes
- **Containerização:** Docker

O cluster de microsserviços seria orquestrado por Kubernetes, representado no diagrama de implantação como o nó de cluster externo. Cada microsserviço individual roda em seu próprio container Docker, representado como um nó interno do tipo `<<Docker Container>>`. Essa separação reflete a realidade de produção: o Kubernetes gerencia escalabilidade, reinicialização automática e distribuição de carga entre os containers, enquanto o Docker garante o isolamento e a portabilidade de cada unidade de implantação.

##### Microsserviços

- **Linguagem:** Java com Spring Boot

Os microsserviços de domínio — `olimpiadas`, `competicoes`, `modalidades`, `locais`, `resultados`, `medalhas`, `inscricoes` e `gerenciamento de atletas` — seriam implementados em Java com Spring Boot. Esses serviços encapsulam lógica de negócio complexa (regras de inscrição, validação de elegibilidade, controle de resultados), para a qual o ecossistema Java oferece vantagens concretas: injeção de dependência com Spring, validação declarativa com Bean Validation, mapeamento de entidades com JPA e testes de integração robustos com Spring Boot Test e Testcontainers. Cada microsserviço possui seu próprio banco de dados SQL Server, seguindo o padrão _database per service_, o que garante isolamento de dados e permite que cada serviço evolua seu schema de forma independente.