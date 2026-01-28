# Infrações Disciplinares – IFPI

Sistema de modelagem para **gestão de infrações disciplinares** em uma instituição de ensino, desenvolvido com base em **Programação Orientada a Objetos** e **modelagem UML**, com foco no controle de ocorrências, penalidades e notificações.

---

## 1. Visão Geral

Este projeto apresenta um **modelo de classes** voltado para a gestão de infrações disciplinares no âmbito educacional. O sistema permite o **registro de ocorrências por professores**, o **acompanhamento por responsáveis**, a **aplicação de penalidades** e o **envio de notificações** aos envolvidos.

A modelagem utiliza conceitos fundamentais de **Orientação a Objetos**, como **herança (generalização)**, **associações** e **multiplicidades**, promovendo reutilização de código, organização e clareza no fluxo do sistema. A classe `Usuario` atua como superclasse, representando os diferentes perfis de acesso, enquanto classes especializadas implementam responsabilidades específicas.

---

## 2. Diagrama de Classes

O diagrama de classes representa visualmente as entidades do sistema, seus atributos, métodos e relacionamentos, evidenciando:

- A **generalização** entre `Usuario`, `Aluno`, `Professor` e `Responsavel`;
- As associações entre **Ocorrência**, **Penalidade** e **Notificação**;
- A estrutura acadêmica composta por **Curso**, **Turma** e **Disciplina**;
- As **multiplicidades**, que definem as regras de cardinalidade entre as classes.

O diagrama serve como base para o desenvolvimento do sistema e para a posterior implementação do banco de dados.

---

## 3. Catálogo de Classes

A seguir, apresenta-se a descrição das classes identificadas no diagrama, bem como suas responsabilidades e principais atributos.

| Classe | Descrição | Atributos Principais |
|------|---------|--------------------|
| Usuario | Superclasse que representa qualquer usuário do sistema e realiza autenticação. | id_usuario, nome, email, senha |
| Aluno | Subclasse de Usuario. Representa o estudante envolvido em ocorrências e penalidades. | matricula |
| Professor | Subclasse de Usuario. Responsável por registrar ocorrências disciplinares. | — |
| Responsavel | Subclasse de Usuario. Responsável por acompanhar as ocorrências do aluno. | — |
| Curso | Representa um curso oferecido pela instituição. | id_curso, nome |
| Turma | Representa uma turma vinculada a um curso e a uma disciplina. | id_turma, nome, id_disciplina |
| Disciplina | Representa uma disciplina acadêmica. | id_disciplina, nome, codigo |
| Ocorrencia | Representa uma infração disciplinar registrada no sistema. | id_ocorrencia, tipo, descricao, data, status |
| Penalidade | Representa a sanção aplicada a uma ocorrência. | id_penalidade, tipo, duracao_dias, data_aplicacao |
| Notificacao | Representa mensagens enviadas aos usuários do sistema. | id_notificacao, mensagem, canal, data_envio, status |

---

## 4. Dicionário de Dados

Esta seção descreve os atributos de cada classe, seus tipos de dados, finalidades e regras de negócio.

### 4.1 Usuario

| Atributo | Tipo | Descrição | Regras / Restrições |
|--------|----|---------|--------------------|
| id_usuario | Inteiro | Identificador único do usuário. | Chave primária |
| nome | String(100) | Nome completo do usuário. | Obrigatório |
| email | String(100) | Email para login e notificações. | Obrigatório, único |
| senha | String(255) | Senha de autenticação. | Obrigatório |

---

### 4.2 Aluno

| Atributo | Tipo | Descrição | Regras / Restrições |
|--------|----|---------|--------------------|
| matricula | String(50) | Matrícula institucional do aluno. | Obrigatório, único |

---

### 4.3 Professor

Classe especializada de `Usuario`, responsável pelo **registro de ocorrências disciplinares** no sistema. Não possui atributos próprios além dos herdados.

---

### 4.4 Responsavel

Classe especializada de `Usuario`, responsável por **acompanhar ocorrências** e receber notificações relacionadas ao aluno.

---

### 4.5 Curso

| Atributo | Tipo | Descrição | Regras / Restrições |
|--------|----|---------|--------------------|
| id_curso | Inteiro | Identificador do curso. | Chave primária |
| nome | String(100) | Nome do curso. | Obrigatório |

---

### 4.6 Turma

| Atributo | Tipo | Descrição | Regras / Restrições |
|--------|----|---------|--------------------|
| id_turma | Inteiro | Identificador da turma. | Chave primária |
| nome | String(50) | Nome ou código da turma. | Obrigatório |
| id_disciplina | Inteiro | Referência à disciplina. | Chave estrangeira |

---

### 4.7 Disciplina

| Atributo | Tipo | Descrição | Regras / Restrições |
|--------|----|---------|--------------------|
| id_disciplina | Inteiro | Identificador da disciplina. | Chave primária |
| nome | String(100) | Nome da disciplina. | Obrigatório |
| codigo | String(20) | Código institucional da disciplina. | Obrigatório, único |

---

### 4.8 Ocorrencia

| Atributo | Tipo | Descrição | Regras / Restrições |
|--------|----|---------|--------------------|
| id_ocorrencia | Inteiro | Identificador da ocorrência. | Chave primária |
| tipo | String(50) | Tipo da infração. | Obrigatório |
| descricao | String(255) | Descrição da ocorrência. | Obrigatório |
| data | Date | Data do registro. | Obrigatório |
| status | String(30) | Situação da ocorrência. | Obrigatório |

---

### 4.9 Penalidade

| Atributo | Tipo | Descrição | Regras / Restrições |
|--------|----|---------|--------------------|
| id_penalidade | Inteiro | Identificador da penalidade. | Chave primária |
| tipo | String(50) | Tipo de penalidade. | Obrigatório |
| duracao_dias | Inteiro | Duração da penalidade em dias. | Maior que zero |
| data_aplicacao | Date | Data de aplicação. | Obrigatório |

---

### 4.10 Notificacao

| Atributo | Tipo | Descrição | Regras / Restrições |
|--------|----|---------|--------------------|
| id_notificacao | Inteiro | Identificador da notificação. | Chave primária |
| mensagem | String(255) | Conteúdo da notificação. | Obrigatório |
| canal | String(50) | Meio de envio. | Obrigatório |
| data_envio | Date | Data do envio. | Obrigatório |
| status | String(30) | Situação da notificação. | Obrigatório |

---

## 5. Considerações Finais

Este modelo fornece uma base sólida para a implementação de um sistema de controle de infrações disciplinares, podendo ser facilmente expandido para incluir regras adicionais, integração com banco de dados relacional e desenvolvimento de interfaces de usuário.

---

**Curso:** Análise e Desenvolvimento de Sistemas  
**Instituição:** IFPI
