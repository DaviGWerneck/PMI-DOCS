
# Deploy API

- Publish .NET comando> 

```
dotnet publish -c Release -o ./publish
```

1. Verificar o funcionamento do appsettings.json e se os locais estão corretos para o atlas, CORS e outras coisas. 
2. Configurar `ASPNETCORE_ENVIRONMENT` no IIS

- `Development` para homologação.
- `Production` para produção.
- `Staging` para deploy em homologação (atual)

## Web.Config API

```
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <location path="." inheritInChildApplications="false">
    <system.webServer>
      <handlers>
        <add name="aspNetCore" path="*" verb="*" modules="AspNetCoreModuleV2" resourceType="Unspecified" />
      </handlers>
      <aspNetCore processPath=".\ServicoSocialServer.Api.exe" stdoutLogEnabled="true" stdoutLogFile=".\logs\stdout" hostingModel="inprocess">
      <environmentVariables>
      <environmentVariable name="ASPNETCORE_ENVIRONMENT" value="Staging" />
      </environmentVariables>
      </aspNetCore>
    </system.webServer>
  </location>
</configuration>
<!--ProjectGuid: a14fd8d6-cc46-44a4-a90e-c9f212b82a1c-->
```


- https://hmg-api.saude.ipatinga.mg.gov.br/servicosocial/swagger/index.html
  
- https://hmg-api.saude.ipatinga.mg.gov.br/servicosocial/api/v1/


## Tutorial Deploy IIS

### Deploy API


1. Baixar o codigo da branch develop e colocar na branch release manualmente ou usando git merge 

2. Publicar a API > 
   
   ![[Pasted image 20250324115225.png]]
3. ![[Pasted image 20250324115301.png]]
4. Caminho > servico-social-server/publish
5. ![[Pasted image 20250324115545.png]]
6. ![[Pasted image 20250324115632.png]]
7. ![[Pasted image 20250324115651.png]]
8. ![[Pasted image 20250324115800.png]] 
9. Alterar o WebConfig para o texto abaixo > 

```
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <location path="." inheritInChildApplications="false">
    <system.webServer>
      <handlers>
        <add name="aspNetCore" path="*" verb="*" modules="AspNetCoreModuleV2" resourceType="Unspecified" />
      </handlers>
      <aspNetCore processPath=".\ServicoSocialServer.Api.exe" stdoutLogEnabled="true" stdoutLogFile=".\logs\stdout" hostingModel="inprocess">
      <environmentVariables>
      <environmentVariable name="ASPNETCORE_ENVIRONMENT" value="Staging" />
      </environmentVariables>
      </aspNetCore>
    </system.webServer>
  </location>
</configuration>
<!--ProjectGuid: a14fd8d6-cc46-44a4-a90e-c9f212b82a1c-->
```

10. Navegar para o Servidor srv000082
![[Pasted image 20250324120123.png]]
11. \\SRV000082\Sites$\homologacao\hmg-api.saude.ipatinga.local\servicosocial
12. Deletar todos os arquivos da pasta servicosocial, e colar os arquivos da pasta publish (os arquivos recem publicados da API, com o WebConfig modificado)
13. Caso ocorra o erro 500 alguma coisa que eu nn lembro, peça ao Cadu do SEATEC pra reiniciar o IIS. 


---


# Deploy Frontend


1. Merge Develop Into Release (atualizar o codigo da branch Release), alterando o arquivo axios.service.ts para consumir a rota de homologação %3E 
   
```
constructor() {

    this.axiosInstance = axios.create({

      baseURL: 'https://hmg-api.saude.ipatinga.mg.gov.br/servicosocial/api/v1/',  

      timeout: 100000,

    });

  }
```

2. Rodar no terminal o comando > 

```
ng build --configuration production  
```

3. Pegar os arquivos gerados na pasta dist/browser e copiar
4. Ir até \\SRV000082\Sites$\homologacao\hmg-servicosocial.ipatinga.local, apagar todos os arquivos e colar os arquivos copiados da pasta dist/browser. 
5. Verificar o funcionamento do site, caso esteja off peça ao Cadu do SEATEC para reiniciar.>)
  

