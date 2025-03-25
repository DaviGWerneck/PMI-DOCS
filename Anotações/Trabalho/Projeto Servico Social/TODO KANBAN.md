---

kanban-plugin: board

---

## Backlog

- [ ] **Adicionar DTO para as rotas de relatório, e refatorar o código**
- [ ] **Grupo familiar debug**
- [ ] **Verificar segurança serviço por serviço**
- [ ] **Tela para cadastrar perguntas**
- [ ] **-nuatendor da ssdusuquestionario deve ser o referente ao atendimento do preenchimento do questionário**
- [ ] **-cdusuassi na sscatend deve ser o usucod da tabela usuario do banco guardian**
- [ ] **-cdusuinc na sscatend deve ser o usucod da tabela usuario do banco guardian**
- [ ] **-cdprofisslancamento na tabela ssdusuquestionario precisa ser do profissional que está logado - ver através da visão nomeprofissional**
- [ ] **Cdususist de TODAS as tabelas deve ser o usucod da tabela usuario do banco guardian**
- [ ] **-campo dtnascpessoa da tabela ssdentservicosocialgrfamiliar não está gravando no formato : "aaaammdd"**
- [ ] **-tela de bloqueados para visita não está permitindo pesquisar um código de sanitas de um usuário que já existe**
- [ ] Criar método de seleção de conexão de banco de dados.


## Doing

- [ ] **Inserir cdususist e cdativpro usando a tabela visão NomeProfissional. Quando não tiver cdativpro usar um fixo do serviço social**
- [ ] **-cdprofiss/cdativpro na sscatend precisa ser do profissional que está logado - ver através da visão nomeprofissional. Exceto para nossas matrículas, testes no treinamento fixar um cdprofiss**
- [ ] **-cdususist na sscatend deve ser o usucod da tabela usuario do banco guardian**
- [ ] **Mudar lógica de armazenamento de CPF, Validação (consumir API Invertexto se possível)**
- [ ] **Criar Rota para CEP**


## Review

- [ ] **Revisar código do Gael que usa muita plain query, se possível adaptar para uso do EF Core**


## Done

- [x] ~~**Rota para retornar desativados e finalizados da fila de atendimento**~~
- [x] ~~**Trazer Nuatend da evolução de conduta > - tabela sscentservicosocial -> ssdatinte -> ssdobs**~~
- [x] ~~**Ensinar Gael a fazer deploy no servidor, abrir chamado no SEATEC para matrícula**~~




%% kanban:settings
```
{"kanban-plugin":"board","list-collapse":[false,false,false,false]}
```
%%