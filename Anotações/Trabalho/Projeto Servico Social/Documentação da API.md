# **AtendimentoController**

**Base Route**: `api/v{version}/Atendimento`

---

#### GET `/api/v{version}/Atendimento/ObterQuestionario`

**Descrição**: Obtém o atendimento do tipo questionário com base no número de entrada.

**Parâmetros**:

|Nome|Tipo|Local|Obrigatório|Descrição|
|---|---|---|---|---|
|nuentrada|decimal|query|Sim|Número de entrada do atendimento|

**Resposta**:

- **200 OK**: Objeto contendo os dados do questionário associado ao atendimento.
    
- **404 Not Found**: Caso nenhum atendimento de questionário seja encontrado.
    

---

#### **GET** `/api/v{version}/Atendimento/ObterEvolucao`

**Descrição**: Obtém a evolução associada a um atendimento.

**Parâmetros**:

|Nome|Tipo|Local|Obrigatório|Descrição|
|---|---|---|---|---|
|nuentrada|decimal|query|Sim|Número de entrada do atendimento|

**Resposta**:

- **200 OK**: Objeto com a evolução do atendimento.
    
- **404 Not Found**: Caso nenhuma evolução seja encontrada.
    

---

#### **POST** `/api/v{version}/Atendimento/PostCriarAtendimento`

**Descrição**: Cria um novo atendimento com base no DTO de registro.

**Parâmetros (Body)**: `RegistroAtendimento`

**Exemplo de campos esperados no DTO** _(será detalhado ao analisar o DTO)_

**Resposta**:

- **200 OK**: Objeto de resposta com status e mensagem de sucesso.
    
- **404 Not Found**: Caso ocorra algum erro e o atendimento não seja criado.



---
 
# AutenticacaoController

**Base Route**: `api/v{version}/Autenticacao`

--- 

#### **POST** `/api/v{version}/Autenticacao/login-pmi`

**Descrição**: Realiza o login do usuário no sistema utilizando as credenciais da plataforma PMI (Atlas).

**Parâmetros (Body)**: `UsuarioLogin`

|Campo|Tipo|Obrigatório|Descrição|
|---|---|---|---|
|Matricula|string|Sim|Matrícula do usuário (username)|
|Senha|string|Sim|Senha do usuário|

**Resposta**:

- **200 OK**: Retorna o token de autenticação JWT e informações do usuário autenticado.
    
- **400 Bad Request**: Caso o modelo de login seja inválido.
    
- **401 Unauthorized**: Credenciais incorretas.

#### **POST** `/api/v1/Autenticacao/renovar-token-pmi`

**Descrição**: Revalida um `refresh_token` e retorna um novo `access_token`.

**Parâmetros (Body)**: `string` (token atual)

**DTO Enviado**: `RefreshAtlasDTO`

|Campo|Tipo|Descrição|
|---|---|---|
|client_id|string|ID do cliente do sistema|
|client_secret|string|Segredo privado do cliente|
|grant_type|string|"refresh_token"|
|refresh_token|string|Token de atualização atual|

**Resposta (200 OK)**: `AtlasLoginResponseSuccessDTO` (igual à resposta do login)

**Resposta (400 Bad Request)**: string com mensagem de erro

##### **GET** `/api/v1/Autenticacao/obter-permissoes`

**Descrição**: Obtém permissões do usuário autenticado a partir do `access_token` no header.

#### **GET** `/api/v1/Autenticacao/obter-roles/{policy}`

**Descrição**: Retorna as roles associadas a uma determinada policy de acesso.

**Parâmetro (path)**:

|Nome|Tipo|Obrigatório|Valores possíveis|
|---|---|---|---|
|policy|string|Sim|AcessoTotal, SomenteLeitura, PolicyMedEnf, etc|
#### **GET** `/api/v1/Autenticacao/conexao`

**Descrição**: Retorna dados da conexão ativa com o banco (servidor e nome do banco).

**Resposta (200 OK)**:

# **EnderecoController**

**Base Route**: `api/v{version}/Endereco`  
**Autenticação**: Requer autorização com a policy `"SERVICO SOCIAL"`

---

#### **POST** `/api/v{version}/Endereco/BuscarBairros`

**Descrição**: Retorna todos os bairros ativos de um município.

**Parâmetros**:

|Nome|Tipo|Local|Obrigatório|Descrição|
|---|---|---|---|---|
|cdMunicipio|decimal|query|Sim|Código do município|

**Resposta**:

- **200 OK**: Lista de bairros ativos.
    
- **404 Not Found**: Caso não existam bairros ou ocorra erro na consulta.
    

---

#### **POST** `/api/v{version}/Endereco/BuscarMunicipios`

**Descrição**: Retorna todos os municípios ativos de uma unidade federativa.

**Parâmetros**:

|Nome|Tipo|Local|Obrigatório|Descrição|
|---|---|---|---|---|
|uf|decimal|query|Sim|Código da unidade federativa (UF)|

**Resposta**:

- **200 OK**: Lista de municípios.
    
- **404 Not Found**: Caso não existam municípios ou erro na consulta.
    

---

#### **POST** `/api/v{version}/Endereco/BuscarLogradouros`

**Descrição**: Retorna os logradouros (ruas/avenidas) de um bairro.

**Parâmetros**:


| Nome     | Tipo    | Local | Obrigatório | Descrição        |
| -------- | ------- | ----- | ----------- | ---------------- |
| cdbairro | decimal | query | Sim         | Código do bairro |
**Resposta**:

- **200 OK**: Lista de logradouros.
    
- **404 Not Found**: Caso não existam logradouros ou erro na consulta.
    


#### **POST** `/api/v{version}/Endereco/BuscarUnidadesFederativas`

**Descrição**: Retorna as unidades federativas do Brasil. 

**Resposta**:

- **200 OK**: Lista de UFs.
    
- **404 Not Found**: Caso não existam UFs ou erro na consulta.


# **EvolucaoAtendimentoController**

**Base URL:** `/api/v1/EvolucaoAtendimento`  
**Autenticação:** Anônima (AllowAnonymous)  
**Versionamento:** `v1.0`

---

#### 📥 GET `/BuscarEvolucaoAtendimentoUsuario`

##### Descrição:

Retorna a evolução do atendimento a partir do número de atendimento.

##### Parâmetros (Query):

|Nome|Tipo|Obrigatório|Descrição|
|---|---|---|---|
|nuatend|decimal|Sim|Número do atendimento|

##### Respostas:

- ✅ `200 OK`: Evolução encontrada
    
- ❌ `404 Not Found`: Evolução não localizada
    

---

#### 📥 GET `/TrazerEvolucoesUsuario`

### Descrição:

Retorna todas as evoluções de um usuário com base na entrada.

### Parâmetros (Query):

|Nome|Tipo|Obrigatório|Descrição|
|---|---|---|---|
|nuentrada|decimal|Não|Número de entrada do atendimento|

##### Respostas:

- ✅ `200 OK`: Lista de evoluções
    
- ❌ `404 Not Found`: Nenhuma evolução encontrada
    

---

#### 📤 POST `/SalvarEvolucaoAtendimentoUsuario`

### Descrição:

Registra uma nova evolução de atendimento.

##### Corpo da Requisição: `AtendimentoDTO`

```
{
  "cdSetor": 1,
  "cdUsuario": 123,
  "cdProfiss": 5,
  "cdAtivPro": 10,
  "nuEntrada": 456,
  "cdLocal": 2,
  "cdSubLoc1": null,
  "cdSubLoc2": null,
  "cdSubLoc3": null,
  "dsObserv": "Texto livre",
  "cdUsuSist": 99,
  "dtInclusao": "2024-01-01",
  "hhInclusao": "14:00"
}

```

##### Respostas:

- ✅ `200 OK`: Evolução salva
    
- ❌ `404 Not Found`: Falha no registro

#### ✏️ PUT `/EditarEvolucaoAtendimento`

### Descrição:

Edita uma evolução de atendimento existente.

##### Corpo da Requisição: `EvolucaoAtendimentoDTO`

```
{
  "nuAtend": 456,
  "cdSetor": 1,
  "dsObserv": "Atualização",
  "idAtivo": "S",
  "nuComput": "PC01",
  "cdUsuSist": 99,
  "dtUltAlt": "2024-01-02",
  "hhUltAlt": "16:00",
  "cdUsuInc": 88,
  "dtInclusao": "2024-01-01",
  "hhInclusao": "14:00"
}

```

##### Respostas:

- ✅ `200 OK`: Evolução atualizada
    
- ❌ `404 Not Found`: Evolução não encontrada

#### ❌ DELETE `/DeletarEvolucaoAtendimento`

### Descrição:

Remove uma evolução de atendimento com base no atendimento e setor.

### Parâmetros (Query):

|Nome|Tipo|Obrigatório|Descrição|
|---|---|---|---|
|nuatend|decimal|Sim|Número do atendimento|
|cdsetor|decimal|Sim|Código do setor|

##### Respostas:

- ✅ `200 OK`: Evolução removida
    
- ❌ `404 Not Found`: Nenhuma evolução removida

# **FilaAtendimentoController**

**Base URL:** `/api/v1/FilaAtendimento`  
**Autenticação:** Anônima (`[AllowAnonymous]`)  
**Versionamento:** `v1.0`

---

#### 📥 GET `/BuscarFilaAtendimento`

### Descrição:

Retorna os usuários atualmente aguardando na fila de atendimento.

### Parâmetros: Nenhum

### Respostas:

- ✅ `200 OK`: Lista de usuários em fila
    
- ❌ `404 Not Found`: Nenhum usuário encontrado
    

---

#### 📥 GET `/BuscarFilaAtendimentoFinalizados`

### Descrição:

Retorna os usuários com atendimentos finalizados (encerrados da fila).

### Parâmetros: Nenhum

### Respostas:

- ✅ `200 OK`: Lista de atendimentos finalizados
    
- ❌ `404 Not Found`: Nenhum atendimento finalizado
    

---

#### 📤 POST `/PostUsuarioFilaAtendimento`

### Descrição:

Adiciona um novo usuário à fila de atendimento.

##### Corpo da Requisição: `AdicionarFilaAtendimentoDTO`

```
{
  "nuEntrada": 123,
  "cdUsuario": 456,
  "cdSetor": 1,
  "dsJustificativa": "Solicitação médica",
  "statusAtendimento": "E",
  "stPrioridade": "A",
  "cdProfCadastrou": 789,
  "nuComputador": "ACESSO WEB",
  "cdUsuSist": 999
}

```

### Respostas:

- ✅ `200 OK`: Usuário adicionado com sucesso
    
- ❌ `404 Not Found`: Falha ao adicionar

## ✏️ PUT `/UpdateFilaAtendimento`

### Descrição:

Atualiza os dados de um usuário que está na fila de atendimento.

### Corpo da Requisição: AtualizarFilaAtendimentoDTO

```
{
  "nuEntrada": 123,
  "cdUsuario": 456,
  "cdSetor": 2,
  "cdUsuSist": 999,
  "dsJustificativa": "Alteração de prioridade",
  "statusAtendimento": "F",
  "stPrioridade": "B"
}

```

### Respostas:

- ✅ `200 OK`: Registro atualizado
    
- ❌ `404 Not Found`: Falha ao atualizar

#### ❌ DELETE `/DeleteFilaAtendimento`

### Descrição:

Remove um usuário da fila de atendimento.

#### Corpo da Requisição (raw `decimal`):

| Campo     | Tipo    | Obrigatório | Descrição                        |
| --------- | ------- | ----------- | -------------------------------- |
| nuEntrada | decimal | Sim         | Número de entrada do atendimento |
### Respostas:

- ✅ `200 OK`: Registro removido com sucesso
    
- ❌ `404 Not Found`: Registro não encontrado ou falha ao remover

#### 🧩 Modelos (DTOs)

###### `AdicionarFilaAtendimentoDTO`

|Campo|Tipo|Obrigatório|Descrição|
|---|---|---|---|
|NuEntrada|decimal|Sim|Número da entrada|
|CdUsuario|decimal?|Não|Código do usuário|
|CdSetor|decimal?|Não|Código do setor|
|DsJustificativa|string?|Não|Texto de justificativa|
|StatusAtendimento|string?|Não|Status (padrão: `"E"`)|
|StPrioridade|string?|Não|Prioridade|
|CdProfCadastrou|decimal?|Não|Código do profissional que cadastrou|
|NuComputador|string?|Não|Computador (padrão: `"ACESSO WEB"`)|
|CdUsuSist|decimal?|Não|Usuário do sistema|

---

###### `AtualizarFilaAtendimentoDTO`

|Campo|Tipo|Obrigatório|Descrição|
|---|---|---|---|
|NuEntrada|decimal|Sim|Número da entrada|
|CdUsuario|decimal?|Não|Código do usuário|
|CdSetor|decimal?|Não|Código do setor|
|CdUsuSist|decimal?|Não|Usuário do sistema|
|DsJustificativa|string?|Não|Justificativa da mudança|
|StatusAtendimento|string?|Não|Novo status de atendimento|
|StPrioridade|string?|Não|Prioridade|

# **MainController (abstrato)**

**Funções principais**:

- `CustomResponse`: personaliza as respostas HTTP de acordo com o status e validações.
    
- `ValidarModelState`: valida o estado do modelo e retorna erros de forma padronizada.
    
- `AdicionarErro`, `LimparErros`, `ErrosAsString`: utilitários para lidar com mensagens de erro.
    

**Nota**: Nenhuma rota está diretamente vinculada a esse controller.

# **QuestionarioController**

**Base Route**: `api/v{version}/Questionario`  
**Autenticação**: [AllowAnonymous]

---

#### **GET** `/api/v{version}/Questionario/PegarPerguntasQuestionario`

**Descrição**: Retorna as perguntas de um questionário para o usuário.

**Parâmetros (query)**:

|Nome|Tipo|Obrigatório|Descrição|
|---|---|---|---|
|cdusuario|decimal|Não|Código do usuário|
|nuidade|decimal|Não|Número da unidade (entidade?)|

**Resposta**:

- **200 OK**: Lista de perguntas do questionário.
    
- **404 Not Found**: Caso não existam perguntas para os parâmetros.
    

---

#### **GET** `/api/v{version}/Questionario/TrazerQuestionarioRespondido`

**Descrição**: Retorna as respostas dadas por um usuário ao questionário.

**Parâmetros (query)**:

|Nome|Tipo|Obrigatório|Descrição|
|---|---|---|---|
|nuentrada|decimal|Não|Número de entrada do usuário|

**Resposta**:

- **200 OK**: Questionário respondido.
    
- **404 Not Found**: Caso não haja resposta registrada.
    

---

#### **PUT** `/api/v{version}/Questionario/EditarRespostaQuestionario`

**Descrição**: Edita uma resposta específica do questionário.

**Parâmetros (Body)**: `QuestionarioParams`

|Campo|Tipo|Descrição|
|---|---|---|
|nuentrada|decimal|Número de entrada do atendimento|
|cdpergunta|decimal|Código da pergunta|
|vlresposta|string|Valor da resposta|

**Resposta**:

- **200 OK**: Resposta editada com sucesso.
    
- **404 Not Found**: Caso a edição falhe.
    

---

#### **POST** `/api/v{version}/Questionario/SalvarRegistroQuestionario`

**Descrição**: Salva todas as respostas de um questionário.

**Parâmetros (Body)**: `RegistroQuestionarioDTO`

**Resposta**:

- **200 OK**: Questionário salvo com sucesso.
    
- **404 Not Found**: Caso ocorra erro na gravação.

# **RelatorioController**

**Base Route**: `api/v{version}/Relatorio`  
**Autenticação**: [AllowAnonymous]  
**Formato de Resposta**: PDF (`application/pdf`)

---

#### **GET** `/api/v{version}/Relatorio/DeclaracaoInternacao`

**Descrição**: Gera um PDF com a declaração de internação do paciente.

**Parâmetros (query)**:

|Nome|Tipo|Obrigatório|Descrição|
|---|---|---|---|
|matricula|string|Sim|Matrícula do paciente|
|nuentrada|decimal|Não|Número de entrada do atendimento|

**Resposta**:

- **200 OK**: Arquivo PDF contendo a declaração de internação.
    
- **404 Not Found**: Caso ocorra falha na geração do relatório.
    

---

#### **GET** `/api/v{version}/Relatorio/AtestadoComparecimento`

**Descrição**: Gera um atestado de comparecimento em PDF.

**Parâmetros (query)**:

|Nome|Tipo|Obrigatório|Descrição|
|---|---|---|---|
|nuentrada|string|Sim|Número de entrada do paciente|
|matricula|string|Sim|Matrícula do paciente|
|nmacompanhante|string|Sim|Nome do acompanhante|
|data|string|Sim|Data do comparecimento|
|horas|string|Sim|Horário|

**Resposta**:

- **200 OK**: PDF com o atestado.
    
- **404 Not Found**: Caso ocorra falha.
    

---

#### **GET** `/api/v{version}/Relatorio/AuxilioFuneral`

**Descrição**: Gera um relatório de auxílio funeral.

**Parâmetros (query)**:

|Nome|Tipo|Obrigatório|Descrição|
|---|---|---|---|
|nuentrada|string|Sim|Número de entrada|
|matricula|string|Sim|Matrícula do falecido|
|nmfuneraria|string|Sim|Nome da funerária|
|data|string|Sim|Data do serviço funerário|

**Resposta**:

- **200 OK**: PDF com o relatório.
    
- **404 Not Found**: Caso ocorra falha.
    

---

#### **POST** `/api/v{version}/Relatorio/AtendimentoFuneral`

**Descrição**: Gera um relatório personalizado de atendimento funerário.

**Parâmetros (Body)**: `AtendimentoFuneralDTO`

**Resposta**:

- **200 OK**: PDF gerado.
    
- **404 Not Found**: Falha na geração.

# **SetorController**

**Base Route**: `api/v{version}/Setor`  
**Autenticação**: [AllowAnonymous]

---

#### **POST** `/api/v{version}/Setor/BuscarSetorPorMatricula`

**Descrição**: Retorna os setores aos quais a matrícula informada está vinculada.

**Parâmetros (Body)**:

|Nome|Tipo|Obrigatório|Descrição|
|---|---|---|---|
|matricula|string|Sim|Matrícula do usuário|

**Resposta**:

- **200 OK**: Lista de setores associados à matrícula.
    
- **404 Not Found**: Nenhum setor encontrado.
    

---

#### **POST** `/api/v{version}/Setor/BuscarLocaisPorSetor`

**Descrição**: Retorna os locais (ambientes) vinculados a um setor.

**Parâmetros (Body)**:

|Nome|Tipo|Obrigatório|Descrição|
|---|---|---|---|
|cdsetor|decimal|Sim|Código do setor|

**Resposta**:

- **200 OK**: Lista de locais do setor.
    
- **404 Not Found**: Nenhum local encontrado.

# **UsuarioController**

**Base Route**: `api/v{version}/Usuario`  
**Autenticação**: [AllowAnonymous]

---

#### **GET** `/api/v{version}/Usuario/BuscarFaixasIdentidadeGenero`

**Descrição**: Retorna as faixas de identidade de gênero disponíveis.

**Parâmetros**: Nenhum.

**Resposta**:

- **200 OK**: Lista de faixas de identidade de gênero.
    
- **404 Not Found**: Caso nenhuma faixa seja encontrada.
    

---

#### **POST** `/api/v{version}/Usuario/BuscarUsuarios`

**Descrição**: Busca usuários com base em critérios definidos.

**Parâmetros (Body)**: `UsuarioCriteriosBuscaDTO`

**Resposta**:

- **200 OK**: Lista de usuários que atendem aos critérios.
    
- **404 Not Found**: Nenhum usuário encontrado.
    

---

#### **PUT** `/api/v{version}/Usuario/UpdateUsuario`

**Descrição**: Atualiza informações de um usuário.

**Parâmetros (Body)**: `UsuarioAtualizacaoDTO`

**Resposta**:

- **200 OK**: Usuário atualizado com sucesso.
    
- **404 Not Found**: Falha na atualização.

# **VisitasController**

**Base Route**: `api/v{version}/Visitas`  
**Autenticação**: [AllowAnonymous]

---

#### **GET** `/api/v{version}/Visitas/BuscarGruposFamiliares`

**Descrição**: Retorna os grupos familiares ativos.

**Parâmetros**: Nenhum.

**Resposta**:

- **200 OK**: Lista de grupos familiares.
    
- **404 Not Found**: Nenhum grupo encontrado.
    

---

#### **POST** `/api/v{version}/Visitas/BuscarGrupoFamiliarUsuario`

**Descrição**: Retorna o grupo familiar associado a um número de entrada.

**Parâmetros (query)**:

|Nome|Tipo|Obrigatório|Descrição|
|---|---|---|---|
|nuentrada|decimal|Sim|Número de entrada do usuário|

**Resposta**:

- **200 OK**: Informações do grupo familiar.
    
- **404 Not Found**: Nenhum grupo encontrado.
    

---

#### **POST** `/api/v{version}/Visitas/BuscarVisitas`

**Descrição**: Retorna as visitas vinculadas a um número de entrada.

**Parâmetros (query)**:

|Nome|Tipo|Obrigatório|Descrição|
|---|---|---|---|
|nuentrada|decimal|Sim|Número de entrada do usuário|

**Resposta**:

- **200 OK**: Lista de visitas.
    
- **404 Not Found**: Nenhuma visita encontrada.
    

---

#### **POST** `/api/v{version}/Visitas/BuscarVisitasNaoAutorizadas`

**Descrição**: Retorna as visitas não autorizadas.

**Parâmetros (query)**:

|Nome|Tipo|Obrigatório|Descrição|
|---|---|---|---|
|nuentrada|decimal|Sim|Número de entrada do usuário|

**Resposta**:

- **200 OK**: Lista de visitas não autorizadas.
    
- **404 Not Found**: Nenhuma visita encontrada.
    

---

#### **POST** `/api/v{version}/Visitas/SalvarVisita`

**Descrição**: Salva um novo acompanhante (visita).

**Parâmetros (Body)**: `AcompanhanteDTO`

**Resposta**:

- **200 OK**: Visita registrada.
    
- **404 Not Found**: Falha ao registrar.
    

---

#### **POST** `/api/v{version}/Visitas/AdicionarFamiliar`

**Descrição**: Adiciona um novo membro ao grupo familiar.

**Parâmetros (Body)**: `GrupoFamiliarDTO`

**Resposta**:

- **200 OK**: Membro adicionado.
    
- **404 Not Found**: Falha na operação.

