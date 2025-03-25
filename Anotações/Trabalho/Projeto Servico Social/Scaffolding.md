# Scaffolding .NET

1. Sanitas_Treinamento


``` 
dotnet ef dbcontext scaffold "Data Source=SRV000066;Initial Catalog=Sanitas_Treinamento;Integrated Security=True;Connect Timeout=30;Encrypt=True;Trust Server Certificate=True;Application Intent=ReadWrite;Multi Subnet Failover=False" Microsoft.EntityFrameworkCore.SqlServer --table sscusuar --table sstsetor --table sscarea --table sscencam --table sscequipe --table sscfamil --table sscmarea --table sscprofi --table ssdentvisita --table ssdentvisitaauto --table sstatend --table sstatpro --table sstconse --table sstencam --table sstentps --table sstfluxo --table ssthospi --table sstlocenc --table sstlograd --table sstmunic --table ssttpaten --table ssttpequ --table sstunadm --table sstunfed --table ssdentcla --table sstclassifi --table ssdatinte --table sscentservicosocial --table ssdentservicosocialgrfamiliar --table ssdentservicosocialusuquestionario --table ssdusuquestionario --table sstpergunta --table sstgrupopergunta --table ssdperguntarespostaprevista --table ssdperguntarestricao --table ssdentservicosocialusunaoautorizado --table InformacoesUsuario --table sscatend --table sscleito --table sstlocal --table ssdobsate --table ssdatinte --table ssdentvisita --table ssdentvisitaauto --table ssdpaset --table sscinusu --table sstfaixa --table sstnive2 --table sstdiscrimi --table sstgrpar --table sstsemen --table ssttpfai --table sstbairro --table sstrespostaprevista --table sstnive1 --table sstsiste --table ssdperguntaresprevista --table sstpibge --table NomeProfissional --table sstcep --use-database-names --context-dir D:\SANITAS\servico-social-server\ServicoSocialServer\src\ServicoSocialServer.Data\Context --output-dir D:\SANITAS\servico-social-server\ServicoSocialServer\src\ServicoSocialServer.Data\Model --project D:\SANITAS\servico-social-server\ServicoSocialServer\src\ServicoSocialServer.Data\ServicoSocialServer.Data.csproj --force

```


2. Guardian

```
dotnet ef dbcontext scaffold "Data Source=SRV000066;Initial Catalog=Guardian;Integrated Security=True;Connect Timeout=30;Encrypt=True;Trust Server Certificate=True;Application Intent=ReadWrite;Multi Subnet Failover=False" Microsoft.EntityFrameworkCore.SqlServer --use-database-names --table ACESSOSANITASAPLGRUPO --table ACESSOSANITASAPLSETOR --table ACESSOSANITASAPLUSUARIO --table ADMINADMPAPEL --table ADMPAPEL --table APLCONEXAO --table APLGRPCNX --table APLGRUPO --table APLICACAO --table APLUSU --table ATRIBUSU --table AUDITORIA --table bkp_usuario --table COMATRIB --table COMREG --table CONEXAO --table conexao_teste --table CONEXAO2 --table DOMINIO --table dtproperties --table GRDADMAPL --table GRDADMIN --table GRDTIP --table GRPCNX --table GRPCNXATRIB --table GRUPO --table GRUPOCONEXAO --table GRUPOGRPCNX --table GRUPOPAPEL --table GRUPOUSU --table lab --table MSpeer_lsns --table MSpeer_originatorid_history --table MSreplication_objects --table MSreplication_subscriptions --table MSsubscription_agents --table PAPEL --table PREFERENCIA --table Results --table sysdiagrams --table TABELAGLOBAL --table TbSeguranca --table TesteREPLICA --table TesteREPLICACAO --table TesteREPLICACAO2 --table USUARIO --table UsuariosPorConexao --table USUCONEXAO --table usucris --table USUGRPCNX --table USUPAPEL --table wk_auditoria --table wk_cris_usuconexao --context-dir D:\SANITAS\servico-social-server\ServicoSocialServer\src\ServicoSocialServer.Data\Context --output-dir D:\SANITAS\servico-social-server\ServicoSocialServer\src\ServicoSocialServer.Data\Model --project D:\SANITAS\servico-social-server\ServicoSocialServer\src\ServicoSocialServer.Data\ServicoSocialServer.Data.csproj --force
```




---
