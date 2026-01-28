# Infrações Disciplinares – IFPI

## 1. Visão Geral

Este projeto apresenta um **modelo de classes UML** desenvolvido para representar o processo de **gestão de ocorrências disciplinares em um ambiente educacional**. O sistema foi modelado com base nos princípios da **Programação Orientada a Objetos**, utilizando conceitos como **herança (generalização)**, **associações** e **cardinalidades**, garantindo uma estrutura clara, coesa e alinhada ao domínio do problema.

O fluxo principal do sistema envolve o **Professor registrando uma ocorrência**, o **Coordenador validando a ocorrência e aplicando penalidades**, e o **Aluno e seu Responsável acompanhando todo o processo por meio de notificações**. A estrutura acadêmica, composta por cursos, turmas e disciplinas, contextualiza as ocorrências dentro do ambiente escolar.

O modelo é adequado para fins acadêmicos e profissionais, podendo ser facilmente convertido para **modelo relacional**, **scripts SQL** ou implementações em linguagens orientadas a objetos.

---

## 2. Diagrama de Classes

O diagrama de classes representa visualmente as entidades do sistema, seus atributos, métodos e relacionamentos. A classe `Usuario` atua como superclasse, concentrando características comuns, enquanto as subclasses especializam os diferentes papéis desempenhados no sistema. As demais classes representam a estrutura acadêmica e o processo disciplinar.

---

## 3. Catálogo de Classes

A seguir, apresenta-se a descrição das classes do sistema, suas responsabilidades e principais atributos.

| Classe | Descrição | Atributos Principais |
|------|---------|--------------------|
| Usuario | Superclasse que representa qualquer usuário que interage com o sistema, centralizando autenticação e dados básicos. | id_usuario, nome, email, senha |
| Aluno | Subclasse de Usuario. Representa o estudante vinculado a uma turma e sujeito a ocorrências e penalidades. | matricula |
| Professor | Subclasse de Usuario. Responsável pelo registro de ocorrências disciplinares. | — |
| Coordenador | Subclasse de Usuario. Responsável por validar ocorrências e aplicar penalidades. | — |
| Responsavel | Subclasse de Usuario. Representa o responsável legal pelo aluno e acompanha o histórico disciplinar. | — |
| Curso | Representa um curso oferecido pela instituição de ensino. | id_curso, nome |
| Turma | Representa uma turma associada a um curso e a um ano letivo. | id_turma, nome, ano_letivo |
| Disciplina | Representa uma disciplina ministrada em uma turma. | id_disciplina, nome, codigo |
| Ocorrencia | Representa um registro disciplinar associado a um aluno em determinado contexto acadêmico. | id_ocorrencia, tipo, descricao, data, status |
| Penalidade | Representa a penalidade aplicada a uma ocorrência após validação. | id_penalidade, tipo, duracao_dias, data_aplicacao, status |
| Notificacao | Representa as notificações enviadas aos alunos e responsáveis. | id_notificacao, mensagem, canal, data_envio, status |

---

## 4. Dicionário de Dados

Esta seção detalha os atributos de cada classe, seus tipos de dados, descrições e regras de negócio.

### Classe: Usuario

| Atributo | Tipo | Descrição | Regras / Restrições |
|--------|----|---------|------------------|
| id_usuario | int | Identificador único do usuário no sistema. | Chave primária |
| nome | String | Nome completo do usuário. | Obrigatório |
| email | String | Email utilizado para autenticação e notificações. | Obrigatório, Único |
| senha | String | Senha de acesso ao sistema. | Obrigatório |

---

### Classe: Aluno

| Atributo | Tipo | Descrição | Regras / Restrições |
|--------|----|---------|------------------|
| matricula | String | Identificador acadêmico único do aluno. | Obrigatório, Único |

---

### Classe: Curso

| Atributo | Tipo | Descrição | Regras / Restrições |
|--------|----|---------|------------------|
| id_curso | int | Identificador único do curso. | Chave primária |
| nome | String | Nome do curso. | Obrigatório |

---

### Classe: Turma

| Atributo | Tipo | Descrição | Regras / Restrições |
|--------|----|---------|------------------|
| id_turma | int | Identificador único da turma. | Chave primária |
| nome | String | Nome ou código da turma. | Obrigatório |
| ano_letivo | int | Ano letivo da turma. | Obrigatório |

---

### Classe: Disciplina

| Atributo | Tipo | Descrição | Regras / Restrições |
|--------|----|---------|------------------|
| id_disciplina | int | Identificador único da disciplina. | Chave primária |
| nome | String | Nome da disciplina. | Obrigatório |
| codigo | String | Código interno da disciplina. | Obrigatório, Único |

---

### Classe: Ocorrencia

| Atributo | Tipo | Descrição | Regras / Restrições |
|--------|----|---------|------------------|
| id_ocorrencia | int | Identificador único da ocorrência. | Chave primária |
| tipo | String | Tipo da ocorrência registrada. | Obrigatório |
| descricao | String | Descrição detalhada da ocorrência. | Obrigatório |
| data | Date | Data do registro da ocorrência. | Obrigatório |
| status | String | Situação atual da ocorrência. | Obrigatório |

---

### Classe: Penalidade

| Atributo | Tipo | Descrição | Regras / Restrições |
|--------|----|---------|------------------|
| id_penalidade | int | Identificador único da penalidade. | Chave primária |
| tipo | String | Tipo da penalidade aplicada. | Obrigatório |
| duracao_dias | int | Duração da penalidade em dias. | Opcional |
| data_aplicacao | Date | Data da aplicação da penalidade. | Obrigatório |
| status | String | Situação atual da penalidade. | Obrigatório |

---

### Classe: Notificacao

| Atributo | Tipo | Descrição | Regras / Restrições |
|--------|----|---------|------------------|
| id_notificacao | int | Identificador único da notificação. | Chave primária |
| mensagem | String | Conteúdo da notificação enviada. | Obrigatório |
| canal | String | Meio de envio da notificação (email, sistema, etc.). | Obrigatório |
| data_envio | Date | Data de envio da notificação. | Obrigatório |
| status | String | Status da notificação. | Obrigatório |

---

## 5. Considerações Finais

O modelo de classes apresentado atende aos critérios de **organização, clareza, coerência conceitual e boas práticas de modelagem UML**, estando adequado para avaliações acadêmicas e para implementação em sistemas reais. A separação clara de responsabilidades entre as classes facilita a manutenção, evolução e integração do sistema com diferentes tecnologias.

---

**Curso:** Análise e Desenvolvimento de Sistemas  
**Instituição:** IFPI
