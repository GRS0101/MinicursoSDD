# Gerador 1:1 — Personal Organizer

Sequência de comandos para reproduzir o projeto exatamente como está.

## 1. Constitution

```
/speckit.constitution
Usar Behavior-Driven Development; usar princípios S.O.L.I.D; usar Clean Architecture, dividindo em camadas, usando ports e adapters; usar Domain-Driven Design; usar Dependency Injection; usar Inversion of Control; usar Repository Pattern; sempre testar o código após cada alteração, refatoração, ou novo código; antes de criar testes de integração, sempre criar testes unitários com 100% de cobertura de testes; criar testes de funcionalidade sob a ótica do usuário, interagindo com a tela, operando as funcionalidades conforme um usuário, no caminho feliz, e em cada condição alternativa, como em mensagens de erro, alertas e exceptions; sempre entrevistar o usuário para entender suas necessidades e expectativas; sempre que for perguntar ao usuário faça somente uma pergunta de cada vez, sobre somente um assunto de cada vez; sempre registre suas perguntas e as respostas do usuário em um arquivo de decisões de projeto em docs/decisions.md; sempre escrever um plano passo-a-passo com checklist antes de implementar ou dar manutenção em qualquer funcionalidade; identificar a oportunidade de criação de agentes especializados; linguagem Python 3.12+ com tipagem estrita via mypy; GUI PySide6; banco SQLite modo WAL sem ORM; testes pytest + pytest-qt + pytest-cov com 100% de cobertura no core; linter e formatador ruff; empacotamento PyInstaller para executável único .exe; Clean Architecture com camadas core/domain core/application infrastructure ui; Repository Pattern com ABCs; MVP na camada de UI; injeção de dependência manual via construtores; dark mode exclusivo; interface em português; Windows desktop;
```

## 2. Spec

```
/speckit.specify
Preciso de um programa que sirva para organizar a vida do usuário; ele deve ter funcionalidades de um bloco de notas; calendário, horário; deve ser possível utiliza-lo como agenda para atribuir tarefas, eventos, etc à datas específicas; também deve ser possível definir prioridades pra tarefas para que hajam lembretes delas, de acordo com a prioridade de execução;
```

## 3. Clarify (responder às perguntas)

```
Q1: "How should users preserve and recover their data in case of file corruption or device loss?"
→ Auto-backup with versioning — automatic periodic snapshots stored locally with ability to roll back to previous versions.

Q2: "Should notes support text formatting or be plain text only?"
→ Rich text — bold, italic, bullet lists, headings via a formatting toolbar.

Q3: "Should search cover only titles or full content of notes, tasks, and events?"
→ Full content search — search matches titles and body content of notes, tasks, and events.

Q4: "Should deletion be permanent or allow recovery?"
→ Soft delete with trash/recycle bin — deleted items go to trash, users can restore or permanently empty it.

Q5: "Should categories be shared across all entity types or separate per type?"
→ Unified categories — a single category system shared by notes, tasks, and events.
```

## 4. Plan

```
/speckit.plan
```

## 5. Tasks

```
/speckit.tasks
```

## 6. Implement

```
/speckit.implement
```
