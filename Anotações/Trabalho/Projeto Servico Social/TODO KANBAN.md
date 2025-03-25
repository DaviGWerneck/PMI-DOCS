---

kanban-plugin: board

---

## Backlog

- [ ] **Adicionar DTO para as rotas de relatório, e refatorar o código**
- [ ] **Grupo familiar debug**
- [ ] **Verificar segurança serviço por serviço**
- [ ] **Tela para cadastrar perguntas**
- [ ] **-campo dtnascpessoa da tabela ssdentservicosocialgrfamiliar não está gravando no formato : "aaaammdd"**
- [ ] **-tela de bloqueados para visita não está permitindo pesquisar um código de sanitas de um usuário que já existe**
- [ ] **Revisar código do Gael que usa muita plain query, se possível adaptar para uso do EF Core**
- [ ] [[Método de seleção de conexão de banco de dados]]
- [ ] **Apagar as perguntas desnecessárias do questionário**
- [ ] **Dinamica de perguntas chaves e perguntas dependentes no questionário**
- [ ] **Melhorar a visualização da FilaAtendimentos no Mobile**
- [ ] **Ficha SiNAN Versão Web**


## Doing

- [ ] **Criar Rota para CEP**


## Review



## Done

- [x] ~~**Rota para retornar desativados e finalizados da fila de atendimento**~~
- [ ] **-nuatendor da ssdusuquestionario deve ser o referente ao atendimento do preenchimento do questionário**
- [ ] **-cdusuassi na sscatend deve ser o usucod da tabela usuario do banco guardian**
- [ ] **Inserir cdususist e cdativpro usando a tabela visão NomeProfissional. Quando não tiver cdativpro usar um fixo do serviço social**
- [ ] **-cdususist na sscatend deve ser o usucod da tabela usuario do banco guardian**
- [ ] **Mudar lógica de armazenamento de CPF, Validação (consumir API Invertexto se possível)**
- [ ] **-cdprofiss/cdativpro na sscatend precisa ser do profissional que está logado - ver através da visão nomeprofissional. Exceto para nossas matrículas, testes no treinamento fixar um cdprofiss**
- [ ] **-cdprofisslancamento na tabela ssdusuquestionario precisa ser do profissional que está logado - ver através da visão nomeprofissional**
- [ ] **Cdususist de TODAS as tabelas deve ser o usucod da tabela usuario do banco guardian**
- [ ] **-cdusuinc na sscatend deve ser o usucod da tabela usuario do banco guardian**
- [x] ~~**Trazer Nuatend da evolução de conduta > - tabela sscentservicosocial -> ssdatinte -> ssdobs**~~
- [x] ~~**Ensinar Gael a fazer deploy no servidor, abrir chamado no SEATEC para matrícula**~~




%% kanban:settings
```
{"kanban-plugin":"board","list-collapse":[false,false,false,false]}
```
%%