# Kanban - Tarefas de Desenvolvimento

## A Fazer

- [ ] **Revisar código do Gael que usa muita plain query, se possível adaptar para uso do EF Core**
- [ ] **Adicionar DTO para as rotas de relatório, e refatorar o código**
- [ ] **Verificar segurança serviço por serviço**
- [ ] **Tela para cadastrar perguntas**
- [ ] **Criar Rota para CEP**
- [ ] **-nuatendor da ssdusuquestionario deve ser o referente ao atendimento do preenchimento do questionário**
- [ ] **-cdprofiss/cdativpro na sscatend precisa ser do profissional que está logado - ver através da visão nomeprofissional. Exceto para nossas matrículas, testes no treinamento fixar um cdprofiss**
- [ ] **-cdusuassi na sscatend deve ser o usucod da tabela usuario do banco guardian**
- [ ] **-cdususist na sscatend deve ser o usucod da tabela usuario do banco guardian**
- [ ] **-cdusuinc na sscatend deve ser o usucod da tabela usuario do banco guardian**
- [ ] **-cdprofisslancamento na tabela ssdusuquestionario precisa ser do profissional que está logado - ver através da visão nomeprofissional**
- [ ] **Cdususist de TODAS as tabelas deve ser o usucod da tabela usuario do banco guardian**
- [ ] **-campo dtnascpessoa da tabela ssdentservicosocialgrfamiliar não está gravando no formato : "aaaammdd"**
- [ ] **-tela de bloqueados para visita não está permitindo pesquisar um código de sanitas de um usuário que já existe**

## Em Progresso

- [ ] **Inserir cdususist e cdativpro usando a tabela visão NomeProfissional. Quando não tiver cdativpro usar um fixo do serviço social**
- [ ] **Mudar lógica de armazenamento de CPF, Validação (consumir API Invertexto se possível)**
  
## Concluído

- [x] ~~**Rota para retornar desativados e finalizados da fila de atendimento**~~
- [x] ~~**Trazer Nuatend da evolução de conduta > - tabela sscentservicosocial -> ssdatinte -> ssdobs**~~
- [x] ~~**Ensinar Gael a fazer deploy no servidor, abrir chamado no SEATEC para matrícula**~~
- [x] **Grupo familiar debug**
