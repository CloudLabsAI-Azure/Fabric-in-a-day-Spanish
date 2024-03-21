
![](Media/4.1.png)
 
# Sumário 
- Introdução
- Fluxo de dados Gen2
    - Tarefa 1: Copiar consultas do Snowflake para o Fluxo de Dados
    - Tarefa 2: Criar conexão com o Snowflake
    - Tarefa 3: Configurar destino de dados para as consultas Supplier e PO
    - Tarefa 4: Renomear e publicar o fluxo de dados do Snowflake
    - Tarefa 5: Copiar consultas do Dataverse para o Dataflow
    - Tarefa 6: Criar conexão com o Dataverse
    - Tarefa 7: Criar destino de dados para a consulta Customer
    - Tarefa 8: Publicar e renomear o Fluxo de Dados do Dataverse
    - Tarefa 9: Copiar consultas do SharePoint para o Fluxo de Dados
    - Tarefa 10: Criar conexão do SharePoint
    - Tarefa 11: Configurar destino de dados para a consulta People
    - Tarefa 12: Publicar e renomear o Fluxo de Dados do SharePoint
- Referências


# Introdução 
Em nosso cenário, os Dados do Fornecedor estão no Snowflake, os Dados do Cliente no Dataverse e os Dados do Funcionário no SharePoint. Todas essas fontes de dados são atualizadas em momentos diferentes. Para minimizar o número de atualizações de dados de Fluxos de Dados, criaremos fluxos de dados individuais para cada uma dessas fontes de dados.

**Observação:** Várias fontes de dados são suportadas em um único Fluxo de Dados.
Ao final deste laboratório, você terá aprendido: 

- Como conectar ao Snowflake usando o Fluxo de dados Gen2 e ingerir dados no Lakehouse
- Como conectar ao SharePoint usando o Fluxo de dados Gen2 e ingerir dados no Lakehouse
- Como conectar ao Dataverse usando o Fluxo de dados Gen2 e ingerir dados no Lakehouse

# Fluxo de dados Gen2
## Tarefa 1: Copiar consultas do Snowflake para o Fluxo de Dados

1. Vamos voltar ao workspace do Fabric, **FAIAD_<nome de usuário>**, que você criou no Laboratório 2, Tarefa 8.
2. No menu superior, selecione **Novo -> Fluxo de dados Gen2**.

    ![](Media/4.2.png)
 
Você será direcionado para a **página do Fluxo de Dados**. Agora que estamos familiarizados com o Fluxo de Dados, vamos continuar e copiar as consultas do Power BI Desktop no Fluxo de Dados.

3. Se você ainda não tiver aberto, abra o arquivo **FAIAD.pbix** que está na pasta **Report** no **Desktop** do seu ambiente de laboratório. 
4. Na faixa de opções, selecione **Página Inicial -> Transformar dados**. A janela do Power Query é aberta. Como você observou no laboratório anterior, as consultas no painel esquerdo são organizadas por fonte de dados.
5. A janela do Power Query é aberta. No painel esquerdo, na pasta SnowflakeData, pressione **Ctrl+Select** ou Shift+Select para selecionar as seguintes consultas:

    a.	SupplierCategories

    b.	Suppliers

    c.	Supplier

    d.	PO

    e.	PO Line Items

6. **Clique com o botão direito do mouse** e selecione **Copiar**.

    ![](Media/4.3.png)
 
7. Volte para o **navegador**.
8. No **painel Dataflow**, selecione o **painel central** e pressione **Ctrl+V** (no momento, não é possível clicar com o botão direito do mouse em Colar).

   **Nota:** Se você estiver trabalhando no ambiente de laboratório, selecione as reticências no canto superior direito da tela. Use o controle deslizante para habilitar a **VM Native Clipboard**. Selecione OK na caixa de diálogo. Uma vez terminada a colagem da consulta, você pode desativar essa opção.

## Tarefa 2: Criar conexão com o Snowflake
Observe que as cinco consultas foram coladas e agora você tem o painel Consultas à esquerda. Como não temos uma conexão criada para o Snowflake, você verá uma mensagem de aviso solicitando que configure a conexão.

1. Selecione **Configurar conexão**.

    ![](Media/4.4.png)
 
2. A caixa de diálogo Conectar-se à fonte de dados é aberta. Na lista suspensa **Conexão**, verifique se **Criar nova conexão** está selecionada.
3. O **Tipo de autenticação** deve ser **Snowflake**.
4. Insira o **Nome de usuário e a Senha do Snowflake** disponíveis na guia Variáveis de Ambiente (ao lado do Guia de Laboratório).
5. Selecione **Conectar**.

    ![](Media/4.5.png)
 
A conexão é estabelecida e você pode exibir os dados no painel de visualização. Fique à vontade para navegar pelas Etapas aplicadas das consultas. Basicamente, a consulta Suppliers tem os detalhes dos fornecedores e SupplierCategories, como o nome indica, tem categorias de fornecedores. Essas duas tabelas são unidas para criar a dimensão Supplier, com as colunas necessárias. Da mesma forma, temos a consulta PO Line Items mesclada com PO para criar o fato PO. Agora precisamos ingerir os dados de Supplier e PO no Lakehouse.

6. Conforme mencionado anteriormente, não estamos preparando nenhum desses dados. Portanto, **clique com o botão direito do mouse** na consulta **Supplier** no painel Consultas e selecione **Habilitar o preparo** para remover a marca de seleção.

    ![](Media/4.6.png)
 
7. Da mesma forma, clique com o botão direito do mouse na consulta **PO**. Selecione **Habilitar o preparo** para remover a marca de seleção.

**Observação:** Não precisamos desabilitar o preparo para as outras três consultas porque Habilitar Carregamento foi desabilitado no Power BI Desktop (de onde essas consultas foram copiadas).
## Tarefa 3: Configurar destino de dados para as consultas Supplier e PO
1. Selecione a consulta **Supplier**.
2. No canto inferior direito, selecione "**+**" ao lado de **Destino de dados**.
3. Selecione **Lakehouse** na caixa de diálogo.

    ![](Media/4.7.png)
 
4. A caixa de diálogo Conectar ao destino de dados é aberta. Na lista suspensa **Conexão**, selecione **Lakehouse (nenhum)**.
5. Selecione **Próximo**.

    ![](Media/4.8.png)
 
6. A caixa de diálogo Escolher alvo de destino é aberta. Verifique se o botão de opção **Nova tabela** está **selecionado**, pois estamos criando uma nova tabela.
7. Queremos criar a tabela no Lakehouse que criamos anteriormente. No painel esquerdo, navegue para **Lakehouse -> FAIAD_<nome de usuário>**. 
8. Selecione **lh_FAIAD**.
9. Deixe o nome da tabela como **Supplier**.
10. Selecione **Próximo**.

    ![](Media/4.9.png)
 
11. A caixa de diálogo Escolher configurações de destino é aberta. Sempre que o Fluxo de dados Gen2 for atualizado, gostaríamos de realizar um carregamento completo. Verifique se **Método de atualização** está definido como **Substituir**.
12.	Observe que há um aviso "Alguns nomes de colunas contêm caracteres sem suporte. Devemos corrigi-los para você?". O Lakehouse não aceita nomes de coluna com espaço. Selecione **Corrigir** para remover o aviso.
13.	O mapeamento de colunas pode ser usado para mapear colunas de fluxo de dados para colunas existentes. No nosso caso, é uma Nova Tabela. Portanto, podemos usar os valores padrão. Selecione **Salvar configurações**.

    ![](Media/4.10.png)
 
14.	Você será direcionado de volta à **janela** Power Query. No **canto inferior direito, Destino de dados** está definido como **Lakehouse**. Da mesma forma, **configure o Destino de dados para a consulta PO**. Uma vez feito isso, sua consulta PO deverá ter **Destino de dados** definido como **Lakehouse** conforme mostrado na captura de tela abaixo.

    ![](Media/4.11.png)
 

## Tarefa 4: Renomear e publicar o fluxo de dados do Snowflake
1. Na parte superior da tela, selecione a **seta ao lado do Dataflow 1** para renomear.
2. Na caixa de diálogo, altere o nome para **df_Supplier_Snowflake**.
3. Clique em **Enter** para salvar a alteração do nome.

    ![](Media/4.12.png)
 
4. No canto inferior direito, selecione **Publicar**.

    ![](Media/4.13.png)
 
Você será direcionado de volta à **tela Data Factory**. Pode levar alguns instantes para que Fluxo de Dados ser publicado.

**Observação:** Às vezes, o nome do Fluxo de Dados não é atualizado. Neste caso, siga as etapas abaixo. Se o Fluxo de Dados for renomeado, você poderá passar para a próxima tarefa.

5.	Assim que a publicação do Dataflow 1 terminar, vamos renomeá-lo. Clique nas **reticências (…)** ao lado de Dataflow 1. Selecione **Propriedades**.

    ![](Media/4.14.png)
 
6. A caixa de diálogo Propriedades do fluxo de dados é aberta. Altere o nome para **df_Supplier_Snowflake**.
7. Na caixa de texto **Descrição**, adicione **Dataflow to ingest Supplier data from Snowflake to Lakehouse**.
8. Selecione **Salvar**.

    ![](Media/4.15.png)
 
Você será direcionado de volta à **tela Data Factory**. Agora vamos criar um fluxo de dados para mostrar dados do Dataverse.

## Tarefa 5: Copiar consultas do Dataverse para o Dataflow
1. No menu superior, selecione **Novo -> Fluxo de dados Gen2**.

    ![](Media/4.16.png)
 
Você será direcionado para a **página do Fluxo de Dados**. Agora que estamos familiarizados com o Fluxo de Dados, vamos continuar e copiar as consultas do Power BI Desktop no Fluxo de Dados.

2. Se você ainda não tiver aberto, abra o arquivo **FAIAD.pbix** que está na pasta **Report** no **Desktop** do seu ambiente de laboratório. 
3. Na faixa de opções, selecione **Página Inicial -> Transformar dados**. A janela do Power Query é aberta. Como você observou no laboratório anterior, as consultas no painel esquerdo são organizadas por fonte de dados.
4. A janela do Power Query é aberta. No painel esquerdo, na pasta DataverseData, pressione **Ctrl+Select** para selecionar as seguintes consultas:

    a.	BabyBoomer
    
    b.	GenX
    
    c.	GenY
    
    d.	GenZ
    
    e.	Customer

5. **Clique com o botão direito do mouse** e selecione **Copiar**.

    ![](Media/4.17.png)
 
6. Volte para a **página Dataflow** no navegador.
7. No **painel Dataflow**, pressione **Ctrl+V** (no momento, não é possível clicar com o botão direito do mouse em Colar).

   **Nota:** Se você estiver trabalhando no ambiente de laboratório, selecione as reticências no canto superior direito da tela. Use o controle deslizante para habilitar a **VM Native Clipboard**. Selecione OK na caixa de diálogo. Uma vez terminada a colagem da consulta, você pode desativar essa opção.

## Tarefa 6: Criar conexão com o Dataverse
Observe que as cinco consultas foram coladas e agora você tem o painel Consultas à esquerda. Como não temos uma conexão criada para o Dataverse, você verá uma mensagem de aviso solicitando que configure a conexão.

1. Selecione **Configurar conexão**.

    ![](Media/4.18.png)
 
2. A caixa de diálogo Conectar-se à fonte de dados é aberta. Na **lista suspensa Conexão**, verifique se **Criar nova conexão** está **selecionada**.
3. O **Tipo de autenticação** deve ser **Conta organizacional**.
4. Selecione **Conectar**.

    ![](Media/4.19.png)
 
## Tarefa 7: Criar destino de dados para a consulta Customer
A conexão é estabelecida e você pode exibir os dados no painel de visualização. Fique à vontade para navegar pelas Etapas aplicadas das consultas. Os dados do cliente estão disponíveis por Categoria: BabyBoomer, GenX, GenY e GenZ. Essas quatro consultas são acrescentadas para criar a consulta Customer. Agora precisamos ingerir os dados de Customer no Lakehouse.

1. Conforme mencionado anteriormente, não estamos preparando nenhum desses dados. Portanto, **clique com o botão direito do mouse** na consulta **Customer** no painel Consultas e selecione **Habilitar o preparo** para remover a marca de seleção.

    ![](Media/4.20.png)
 
2. Selecione a consulta **Customer**.
3. No canto inferior direito, selecione "**+**" ao lado de **Destino de dados**.
4. Selecione **Lakehouse** na caixa de diálogo.

    ![](Media/4.21.png)
 
5. A caixa de diálogo Conectar ao destino de dados é aberta. Na lista suspensa **Conexão**, selecione **Lakehouse (nenhum)**.
6. Selecione **Próximo**.

    ![](Media/4.22.png)
 
7. A caixa de diálogo Escolher alvo de destino é aberta. Verifique se o botão de opção **Nova tabela** está selecionado, pois estamos criando uma nova tabela.
8.	Queremos criar a tabela no Lakehouse que criamos anteriormente. No painel esquerdo, navegue para **Lakehouse -> FAIAD_<nome de usuário>**. 
9. Selecione **lh_FAIAD**.
10.	Deixe o nome da tabela como **Customer**.
11.	Selecione **Próximo**.

    ![](Media/4.23.png)
 
12.	A caixa de diálogo Escolher configurações de destino é aberta. Sempre que o Fluxo de dados Gen2 for atualizado, gostaríamos de realizar um carregamento completo. Verifique se **Método de atualização** está definido como **Substituir**.
13.	Observe que há um aviso "Alguns nomes de colunas contêm caracteres sem suporte. Devemos corrigi-los para você?". O Lakehouse não aceita nomes de coluna com espaço. Selecione **Corrigir** para remover o aviso.
14.	O mapeamento de colunas pode ser usado para mapear colunas de fluxo de dados para colunas existentes. No nosso caso, é uma Nova Tabela. Portanto, podemos usar os valores padrão. Selecione **Salvar configurações**.

    ![](Media/4.24.png)
 

## Tarefa 8: Publicar e renomear o Fluxo de Dados do Dataverse
1. Você será direcionado de volta à **janela Power Query**. No **canto inferior direito, Destino de dados** está definido como **Lakehouse**.
2. No canto inferior direito, selecione **Publicar**.

    ![](Media/4.25.png)
 
**Observação:** Você será direcionado de volta à **tela Data Factory**. Pode levar alguns instantes para que Fluxo de Dados ser publicado. 

3. Estamos trabalhando com o Dataflow 1. Vamos renomeá-lo antes de continuar. Clique nas **reticências (…)** ao lado de Dataflow 1. Selecione **Propriedades**.

    ![](Media/4.26.png)
 
4. A caixa de diálogo Propriedades do fluxo de dados é aberta. Altere o **Nome** para **df_Customer_Dataverse**.
5. Na caixa de texto **Descrição**, adicione **Dataflow to ingest Supplier data from Snowflake to Lakehouse**.
6. Selecione **Salvar**.

    ![](Media/4.27.png)
 
Você será direcionado de volta à **tela Data Factory**. Agora vamos criar um fluxo de dados para mostrar dados do SharePoint.

## Tarefa 9: Copiar consultas do SharePoint para o Fluxo de Dados
1. No menu superior, selecione **Novo -> Fluxo de dados Gen2**.

    ![](Media/4.28.png)
 
Você será direcionado à **página do Fluxo de Dados**. Agora que estamos familiarizados com o Fluxo de Dados, vamos continuar e copiar as consultas do Power BI Desktop no Fluxo de Dados.

2. Se você ainda não tiver aberto, abra o arquivo **FAIAD.pbix** que está na pasta **Report** no **Desktop** do seu ambiente de laboratório. 
8. Na faixa de opções, selecione **Página Inicial -> Transformar dados**. A janela do Power Query é aberta. Como você observou no laboratório anterior, as consultas no painel esquerdo são organizadas por fonte de dados.
9. A janela do Power Query é aberta. No painel esquerdo, na pasta SharepointData, **selecione** a consulta **People**.
10. **Clique com o botão direito do mouse** e selecione **Copiar**.

    ![](Media/4.29.png)
 
11.	Volte para a tela **Fluxo de Dados** no navegador.
12.	No **painel Fluxo de Dados**, pressione **Ctrl+V** (no momento, não é possível clicar com o botão direito do mouse em Colar).

    **Nota:** Se você estiver trabalhando no ambiente de laboratório, selecione as reticências no canto superior direito da tela. Use o controle deslizante para habilitar a **VM Native Clipboard**. Selecione OK na caixa de diálogo. Uma vez terminada a colagem da consulta, você pode desativar essa opção.

Observe se a consulta foi colada e se está disponível no painel esquerdo. Como não temos uma conexão criada para o SharePoint, você verá uma mensagem de aviso solicitando que configure a conexão.

## Tarefa 10: Criar conexão do SharePoint
1. Selecione **Configurar conexão**.

    ![](Media/4.30.png)
 
2. A caixa de diálogo Conectar-se à fonte de dados é aberta. Na lista suspensa **Conexão**, verifique se **Criar nova conexão** está selecionada.
3. O **Tipo de autenticação** deve ser **Conta organizacional**.
4. Selecione **Conectar**.

    ![](Media/4.31.png)
 

## Tarefa 11: Configurar destino de dados para a consulta People
A conexão é estabelecida e você pode exibir os dados no painel de visualização. Fique à vontade para navegar pelas Etapas aplicadas das consultas. Agora precisamos ingerir os dados de People no Lakehouse.
1. Conforme mencionado anteriormente, não estamos preparando nenhum desses dados. Portanto, **clique com o botão direito do mouse** na consulta **People** no painel Consultas e selecione **Habilitar o preparo** para remover a marca de seleção.

    ![](Media/4.32.png)
 
2. Selecione a consulta **People**.
3. No canto inferior direito, selecione "**+**" ao lado de **Destino de dados**.
4. Selecione **Lakehouse** na caixa de diálogo.

    ![](Media/4.33.png)
 
5. A caixa de diálogo Conectar ao destino de dados é aberta. Na lista suspensa **Conexão**, selecione **Lakehouse (nenhum)**.
6. Selecione **Próximo**.

    ![](Media/4.34.png)
 
7. A caixa de diálogo Escolher alvo de destino é aberta. Verifique se o botão de opção **Nova tabela** está selecionado, pois estamos criando uma nova tabela.
8. Queremos criar a tabela no Lakehouse que criamos anteriormente. No painel esquerdo, navegue para **Lakehouse -> FAIAD_<nome de usuário>**. 
9. Selecione **lh_FAIAD**.
10. Deixe o nome da tabela como **People**.
11. Selecione **Próximo**.

    ![](Media/4.35.png)
 
12. A caixa de diálogo Escolher configurações de destino é aberta. Sempre que o Fluxo de dados Gen2 for atualizado, gostaríamos de realizar um carregamento completo. Verifique se **Método de atualização** está definido como **Substituir**.
13.	Observe que há um aviso "Alguns nomes de colunas contêm caracteres sem suporte. Devemos corrigi-los para você?". O Lakehouse não aceita nomes de coluna com espaço. Selecione **Corrigir** para remover o aviso.
14.	O mapeamento de colunas pode ser usado para mapear colunas de fluxo de dados para colunas existentes. No nosso caso, é uma Nova Tabela. Portanto, podemos usar os valores padrão. Selecione **Salvar configurações**.

    ![](Media/4.36.png)
 
## Tarefa 12: Publicar e renomear o Fluxo de Dados do SharePoint
1. Você será direcionado de volta à **janela Power Query**. No **canto inferior direito**, Destino de dados está definido como **Lakehouse**.
2. No canto inferior direito, selecione **Publicar**.

    ![](Media/4.37.png)
 
**Observação:** Você será direcionado de volta à tela Data Factory. Pode levar alguns instantes para que Fluxo de Dados ser publicado. 

3. Estamos trabalhando com o Dataflow 1. Vamos renomeá-lo antes de continuar. Clique nas **reticências (…)** ao lado de Dataflow 1. Selecione **Propriedades**.

    ![](Media/4.38.png)
 
4. A caixa de diálogo Propriedades do fluxo de dados é aberta. Altere o **nome** para **df_People_SharePoint**.
5. Na caixa de texto **Descrição**, adicione **Dataflow to ingest People data from SharePoint to Lakehouse**.
6. Selecione **Salvar**.

    ![](Media/4.39.png)
 
Você será direcionado de volta à **tela Data Factory**. Agora ingerimos todos os dados no Lakehouse. No próximo laboratório, agendaremos a atualização do Fluxo de Dados.

# Referências
O Fabric Analyst in a Day (FAIAD) apresenta algumas das principais funções disponíveis no Microsoft Fabric. No menu do serviço, a seção Ajuda (?) tem links para ótimos recursos.

![](Media/4.40.png)
 
Veja aqui mais alguns recursos que ajudarão você com as próximas etapas do Microsoft Fabric.
- Veja a postagem do blog para ler o [anúncio completo de GA do Microsoft Fabric](https://aka.ms/Fabric-Hero-Blog-Ignite23)
- Explore o Fabric por meio do [Tour Guiado](https://aka.ms/Fabric-GuidedTour)
- Inscreva-se para a [avaliação gratuita do Microsoft Fabric](https://aka.ms/try-fabric)
- Visite o [site do Microsoft Fabric](https://aka.ms/microsoft-fabric)
- Aprenda novas habilidades explorando os [módulos de Aprendizagem do Fabric](https://aka.ms/learn-fabric)
- Explore a [documentação técnica do Fabric](https://aka.ms/fabric-docs)
- Leia o livro [eletrônico gratuito sobre como começar a usar o Fabric](https://aka.ms/fabric-get-started-ebook)
- Participe da [comunidade do Fabric](https://aka.ms/fabric-community) para postar suas perguntas, compartilhar seus comentários e aprender com outras pessoas

Leia os blogs de comunicados de experiências do Fabric em mais detalhes:

- [Experiência do Data Factory no blog do Fabric](https://aka.ms/Fabric-Data-Factory-Blog) 
- [Experiência do Synapse Data Engineering no blog do Fabric](https://aka.ms/Fabric-DE-Blog) 
- [Experiência do Synapse Data Science no blog do Fabric](https://aka.ms/Fabric-DS-Blog) 
- [Experiência do Synapse Data Warehousing no blog do Fabric](https://aka.ms/Fabric-DW-Blog) 
- [Experiência do Synapse Real-Time Analytics no blog do Fabric](https://aka.ms/Fabric-RTA-Blog)
- [Blog de comunicado do Power BI](https://aka.ms/Fabric-PBI-Blog)
- [Experiência do Data Activator no blog do Fabric](https://aka.ms/Fabric-DA-Blog) 
- [Administração e governança no blog do Fabric](https://aka.ms/Fabric-Admin-Gov-Blog)
- [OneLake no blog do Fabric](https://aka.ms/Fabric-OneLake-Blog)
- [Blog de integração do Dataverse e Microsoft Fabric](https://aka.ms/Dataverse-Fabric-Blog)

© 2023 Microsoft Corporation. Todos os direitos reservados.

Ao usar esta demonstração/este laboratório, você concorda com os seguintes termos:

A tecnologia/funcionalidade descrita nesta demonstração/neste laboratório é fornecida pela Microsoft Corporation para obter seus comentários e oferecer uma experiência de aprendizado. Você pode usar a demonstração/o laboratório somente para avaliar tais funcionalidades e recursos de tecnologia e fornecer comentários à Microsoft. Você não pode usá-los para nenhuma outra finalidade. Você não pode modificar, copiar, distribuir, transmitir, exibir, executar, reproduzir, publicar, licenciar, criar obras derivadas, transferir nem vender esta demonstração/este laboratório ou qualquer parte deles.

A CÓPIA OU A REPRODUÇÃO DA DEMONSTRAÇÃO/DO LABORATÓRIO (OU DE QUALQUER PARTE DELES) EM QUALQUER OUTRO SERVIDOR OU LOCAL PARA REPRODUÇÃO OU REDISTRIBUIÇÃO ADICIONAL É EXPRESSAMENTE PROIBIDA.

ESTA DEMONSTRAÇÃO/ESTE LABORATÓRIO FORNECE DETERMINADOS RECURSOS E FUNCIONALIDADES DE PRODUTO/TECNOLOGIA DE SOFTWARE, INCLUINDO NOVOS RECURSOS E CONCEITOS POTENCIAIS, EM UM AMBIENTE SIMULADO SEM CONFIGURAÇÃO NEM INSTALAÇÃO COMPLEXA PARA A FINALIDADE DESCRITA ACIMA. A TECNOLOGIA/OS CONCEITOS REPRESENTADOS NESTA DEMONSTRAÇÃO/NESTE LABORATÓRIO PODEM NÃO REPRESENTAR A FUNCIONALIDADE COMPLETA DOS RECURSOS E PODEM NÃO FUNCIONAR DA MESMA MANEIRA QUE UMA VERSÃO FINAL. ALÉM DISSO, PODEMOS NÃO LANÇAR UMA VERSÃO FINAL DE TAIS RECURSOS OU CONCEITOS. SUA EXPERIÊNCIA COM O USO DE TAIS RECURSOS E FUNCIONALIDADES EM UM AMBIENTE FÍSICO TAMBÉM PODE SER DIFERENTE.

**COMENTÁRIOS.** Caso você forneça comentários sobre os recursos de tecnologia, as funcionalidades e/ou os conceitos descritos nesta demonstração/neste laboratório à Microsoft, você concederá à Microsoft, sem encargos, o direito de usar, compartilhar e comercializar seus comentários de qualquer forma e para qualquer finalidade. Você também concede a terceiros, sem encargos, quaisquer direitos de patente necessários para que seus produtos, suas tecnologias e seus serviços usem ou interajam com partes específicas de um software ou um serviço da Microsoft que inclua os comentários. Você não fornecerá comentários que estejam sujeitos a uma licença que exija que a Microsoft licencie seu software ou sua documentação para terceiros em virtude da inclusão de seus comentários neles. Esses direitos continuarão em vigor após o término do contrato.

POR MEIO DESTE, A MICROSOFT CORPORATION SE ISENTA DE TODAS AS GARANTIAS E CONDIÇÕES REFERENTES À DEMONSTRAÇÃO/AO LABORATÓRIO, INCLUINDO TODAS AS GARANTIAS E CONDIÇÕES DE COMERCIALIZAÇÃO, SEJAM ELAS EXPRESSAS, IMPLÍCITAS OU ESTATUTÁRIAS, E DE ADEQUAÇÃO A UMA FINALIDADE ESPECÍFICA, TÍTULO E NÃO VIOLAÇÃO. A MICROSOFT NÃO DECLARA NEM GARANTE A PRECISÃO DOS RESULTADOS DERIVADOS DO USO DA DEMONSTRAÇÃO/DO LABORATÓRIO NEM A ADEQUAÇÃO DAS INFORMAÇÕES CONTIDAS NA DEMONSTRAÇÃO/NO LABORATÓRIO A QUALQUER FINALIDADE.

**AVISO DE ISENÇÃO DE RESPONSABILIDADE**

Esta demonstração/este laboratório contém apenas uma parte dos novos recursos e aprimoramentos do Microsoft Power BI. Alguns dos recursos podem ser alterados em versões futuras do produto. Nesta demonstração/neste laboratório, você aprenderá sobre alguns dos novos recursos, mas não todos.
