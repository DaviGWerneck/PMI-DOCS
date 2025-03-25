1. ~~Rota para retornar desativados e finalizados da fila de atendimento~~
2. Revisar código do Gael que usa muita plain query, se possível adaptar para uso do EF Core
3. Adicionar DTO para as rotas de relatório, e refatorar o código
4. Verificar segurança serviço por serviço. 
5. Inserir cdususist e cdativpro usando a tabela visão NomeProfissional. Quando não tiver cdativpro usar um fixo do serviço social. 
6. Testes Unitários. 
7. ~~- Trazer Nuatend da evolução de conduta > - tabela sscentservicosocial -> ssdatinte -> ssdobs~~
8. Mudar logica de armazenamento de CPF, Validação (consumir api invertexto se pá )
9. Tela para cadastrar perguntas
10. ~~Ensinar Gael a fazer deploy no servidor, abrir chamado no SEATEC para matricula~~ 
11. Grupo familar debug 
12. Criar Rota para CEP
13. -nuatendor da ssdusuquestionario deve ser o referente ao atendimento do preenchimento do questionário;
14. -cdprofiss/cdativpro na sscatend precisa ser do profissional que está logado - ver através da visão nomeprofissional. Exceto para nossas matrículas, testes no treinamento fixar um cdprofiss.
15. -cdusuassi na sscatend deve ser o usucod da tabela usuario do banco guardian
16. -cdususist na sscatend deve ser o usucod da tabela usuario do banco guardian
17. -cdusuinc na sscatend deve ser o usucod da tabela usuario do banco guardian
18. -cdprofisslancamento na tabela ssdusuquestionario  precisa ser do profissional que está logado - ver através da visão nomeprofissional
19. ****Cdususist de TODAS as tabelas deve ser o usucod da tabela usuario do banco guardian 
20. -campo dtnascpessoa da tabela ssdentservicosocialgrfamiliar não está gravando no formato : "aaaammdd"
21. -tela de bloqueados para visita não está permitindo pesquisar um código de sanitas de um usuário que já existe.