# Exercício de Sala 🏫  

## Evoluindo nosso dashboard

Para esse tutorial continuaremos a usar a base de dados do arquivo `base_final_s14_olist.csv` disponibilizada na pasta de [material](https://github.com/reprograma/on29-python-s16-dashboard/tree/main/material) 
___________________________

## Iniciando

Primeiro, faça uma nova publicação do dashboard desenvolvido na semana 15 por você *ou* faça uma cópia do dashboard disponibilizado pela Professora Mariana.
https://public.tableau.com/views/reprograma-s16-dashboards/Mapas?:language=pt-BR&:sid=&:redirect=auth&:display_count=n&:origin=viz_share_link

![](https://raw.githubusercontent.com/reprograma/on29-python-s16-dashboard/main/assets/exercicio-sala-1a-nova-publicacao-dashboard.png "Figura 1a")
![](https://raw.githubusercontent.com/reprograma/on29-python-s16-dashboard/main/exercicio-sala-1a-popup.png "Figura 1a - Popup")
*Figura 1a: Instruções de como fazer uma nova publicação de um dashboard seu. Com o seu dashboard aberto já em edição, clique no menu "Arquivo" e selecione "Publicar como", ou use o atalho Ctrl+Shift+S, aparecerá uma janela onde você deve digitar o nome a sua escolha e clicar "Publicar"*

![](https://raw.githubusercontent.com/reprograma/on29-python-s16-dashboard/main/assets/exercicio-sala-1b-fazer-copia-dashboard.png "Figura 1b")
*Figura 1b: Instruções de como fazer uma cópia de um dashboard. Clique no ícone "Fazer uma cópia" na visualização de dados modelo*

Assim seguiremos aprofundando nossa análise.
___________________________

## Combinando fontes de dados diferentes

Antes de começarmos, adicionaremos uma nova fonte de dados `estados_brasileiros.csv` disponibilizada na pasta de [material](https://github.com/reprograma/on29-python-s16-dashboard/tree/main/material)

![](https://raw.githubusercontent.com/reprograma/on29-python-s16-dashboard/main/assets/exercicio-sala-8-nova-fonte-de-dados.png "Figura 8")
*Figura 8: Instruções para adição de nova fonte de dados. Clique em "Fonte de dados" na parte inferior da tela, na parte superior direita clique no "+" ao lado de "Conexões".
Abrirá uma janela "Conectar a dados", clique em "Fazer upload usando o computador" e selecione o arquivo csv de estados.*

Aguarde carregar. Sob arquivos teremos **estados_brasileiros.csv** arraste-o para combinar*.
![](https://raw.githubusercontent.com/reprograma/on29-python-s16-dashboard/main/assets/exercicio-sala-9-arrastar-arquivo-de-dados.png "Figura 9")
*Figura 9: Instruções visuais de como arrastar o arquivo e para onde.*

Teremos uma visualização como abaixo, agora é hora de alterar o tipo de cada campo, pois só estado foi reconhecido como função geográfica.
![](https://raw.githubusercontent.com/reprograma/on29-python-s16-dashboard/main/assets/exercicio-sala-10-alterar-tipo-dado.png "Figura 10")
*Figura 10: Instruções para alteração de tipo de dados. Clique na seta acima de cada campo ao lado de "Abc", para **País** selecione "Função geográfica" e **País/Região**, para **Sigla** selecione "Função geográfica", "Criar de" e selecione o campo **Estado**, para **Estado** selecione "Função geográfica" e **Estado/Província**, e para **Região** selecione "Função geográfica", "Criar de" e selecione o campo **Estado***

Após isso, criaremos agora o relacionamento entre as tabelas arraste a nova tabela lógica para o lado da tabela original.
![](https://raw.githubusercontent.com/reprograma/on29-python-s16-dashboard/main/assets/exercicio-sala-11-criar-relacionamento-entre-bases.png "Figura 11")
*Figura 11: Instruções para criação de relacionamento entre fonte de dados. Clique em "Selecionar um campo" abaixo de cada fonte de dados. Selecione **Customer State** para a tabela original e **Sigla** para a nova tabela. O operador permanece como **=***

> 💡 Acabamos de combinar dados de diferentes tabelas. Podemos combinar várias fontes de dados e inclusive usar diversos campos para indicar o relacionamento entre elas. O paralelo disso em SQL seria o **JOIN**. Para mais detalhes: https://help.tableau.com/current/pro/desktop/pt-br/multiple_connections.htm
Mais do que termos os dados de região, queremos que o Tableau identifique os estados, pois ele não identifica as siglas diretamente. Para saber mais de dados de mapas: https://www.tableau.com/pt-br/mapdata.

> Vídeo curto de como criar uma mapa mostrando as regiões no Brasil

[![IMAGE ALT TEXT HERE](https://img.youtube.com/vi/8btsk1SSTMU/0.jpg)](https://www.youtube.com/watch?v=8btsk1SSTMU)
___________________________

## Parte 2 - Criando um gráfico de mapa com drill downs

### Planilhas

Criaremos três novas planilhas, nomeie-as como preferir (sugestão: País, Estado e Cidade).

#### Planilha País
1. Arraste o campo **País** na área da planilha onde se está "Solte o campo aqui"
2. No painel de *Marcas*, troque a opção de **Automático** para **Mapa**
3. Arraste o campo **Price**, que será agregado como soma, e também o campo **País** para **Rótulo** no painel de *Marcas*. Altere de *Contínuo* para *Discreto*. Em *Formatar número*, selecione **Moeda (padrão)**
![](https://raw.githubusercontent.com/reprograma/on29-python-s16-dashboard/main/assets/exercicio-sala-12-planilha-pais.png "Figura 12")

#### Planilha Estado
1. Arraste o campo **País** na área da planilha onde se está "Solte o campo aqui"
2. No painel de *Marcas*, troque a opção de **Automático** para **Mapa**
3. Arraste o campo **Estado** para **Detalhe** no painel de *Marcas*
4. Arraste o campo **Price**, que será agregado como soma, e também o campo **Sigla** para **Rótulo** no painel de *Marcas*. Altere de *Contínuo* para *Discreto*. Em *Formatar número*, selecione **Moeda (padrão)**
5. Opcional: Arraste o campo **Região** para **Cores** no painel de *Marcas*
![](https://raw.githubusercontent.com/reprograma/on29-python-s16-dashboard/main/assets/exercicio-sala-13-planilha-estado.png "Figura 13")

#### Planilha Cidade
1. Arraste o campo **País** na área da planilha onde se está "Solte o campo aqui"
2. Arraste o campo **Estado** para **Detalhe** no painel de *Marcas*
3. Arraste o campo **Customer City** para **Detalhe** no painel de *Marcas*
4. Arraste o campo **Price**, que será agregado como soma, para **Rótulo** no painel de *Marcas*. Altere de *Contínuo* para *Discreto*. Em *Formatar número*, selecione **Moeda (padrão)**
5. Opcional: Arraste o campo **Região** para **Cores** no painel de *Marcas*
![](https://raw.githubusercontent.com/reprograma/on29-python-s16-dashboard/main/assets/exercicio-sala-14-planilha-cidade.png "Figura 14")

Em qualquer uma das três planilhas arraste os campos: **Região**, **Sigla** e **Customer City** para a área de *Filtros*. Em cada um desses filtros clique com o botão direito e vá até a opção *Aplicar a planilhas* e selecione *Planilhas selecionadas...*. Selecione as outras duas planilhas e clique em Ok. Repita para os outros filtros.

> Coloque a Opção de *Mostrar filtro* e brinque com a visualização

### Criando Parâmetros
Parâmetros no Tableau são variáveis de planilha dinâmicas, que permitem controlar e adaptar as visualizações rapidamente. Permitem assumir valores constantes ou intervalos de valores (mínimo e máximo). Aceitam diversos tipos de dados: numéricos, texto, booleanos etc. Podem ser utilizados em diversas funções e cálculos.

Para criar um novo parâmetro:

1. Clique com o botão direito no campo **Estado** e selecione a opção Criar > Parâmetro.
Preencha como na imagem o **Parâmetro Estado**. *Aparecerá um novo painel chamado parâmetros no canto inferior esquerdo.
![](https://raw.githubusercontent.com/reprograma/on29-python-s16-dashboard/main/assets/exercicio-sala-15-parametro-estado.png "Figura 15")

 
2. Duplique o parâmetro recém-criado três vezes e renomeie (pela opção renomear, ou usando a tecla F2) para **Parâmetro Cidade**, **Parâmetro País** e **Parâmetro Estado Selecionado** (as opções são as mesmas para todos)

### Campos Calculados

Agora, iremos criar quatro campos calculados (Análise > Criar campo calculado...), que irão avaliar os valores recebidos pelor parâmetros, cada qual com a seguintes fórmulas:

#### Visibilidade País
`[Parâmetro Cidade]!=''
AND
[Parâmetro Estado]=''
AND
[Parâmetro País]=''`

#### Visibilidade Estado
`[Parâmetro Cidade]=''
AND
[Parâmetro Estado]=''
AND
[Parâmetro País]!=''`

#### Visibilidade Cidade
`[Parâmetro Cidade]=''
AND
[Parâmetro Estado]!=''
AND
[Parâmetro País]=''`

#### Filtro Estado
`[Estado]=[Parâmetro Estado Selecionado]`

## Dashboard
Criaremos nosso painel, ou dashboard, dê o nome que preferir. Arraste um **Contêiner vertical** para a área principal como na imagem abaixo.
![](https://raw.githubusercontent.com/reprograma/on29-python-s16-dashboard/main/assets/exercicio-sala-16-conteiner.png "Figura 16")

Dentro do contêiner, arraste as três planilhas: **País**, **Estado** e **Cidade**, uma abaixo da outra.

### Ações de Parâmetros
-o que sao ações-
1. No menu superior, selecione *Painel > Ações*. Clique em *Adicionar ação* no menu suspenso inferior e clique em **Alterar parâmetro**, conforme figura abaixo. Repetiremos esse processo quatro vezes para cada um dos casos abaixo.
![](https://raw.githubusercontent.com/reprograma/on29-python-s16-dashboard/main/assets/exercicio-sala-17-acao-parametro.png "Figura 17")

#### Alterar Parâmetro de País
![](https://raw.githubusercontent.com/reprograma/on29-python-s16-dashboard/main/assets/parametro-pais.png "Figura 18")

#### Alterar Parâmetro de Estado
![](https://raw.githubusercontent.com/reprograma/on29-python-s16-dashboard/main/assets/parametro-estado.png "Figura 19")

#### Alterar Parâmetro de Cidade
![](https://raw.githubusercontent.com/reprograma/on29-python-s16-dashboard/main/assets/parametro-cidade.png "Figura 20")

#### Alterar Estado Selecionado
![](https://raw.githubusercontent.com/reprograma/on29-python-s16-dashboard/main/assets/parametro-estado-selecionado.png "Figura 21")

Clique em OK para salvar.

### Exibição de campos de de parâmetros
Em qualquer um dos três mapas do dashboard, selecione a setinha de mais opções, como na imagem abaixo, e adicione os quatro parâmetros para serem exibidos como campo de texto na parte lateral
![](https://raw.githubusercontent.com/reprograma/on29-python-s16-dashboard/main/assets/exercicio-sala-22-adicionar-parametros.png "Figura 22")

### Exibição de Mapas dados aos parâmetros selecionados
⚠️ Antes de mais nada, clique em alguma cidade do mapa cidade e garanta que o parâmetro **Parâmetro Cidade** esteja preenchido, isso garante que as regras de exibição sempre serão satisfeitas. Caso isso não ocorra, preencha, por exemplo, o campo do país com **Brasil** selecione algum dos estados, e apague o parâmetro com Brasil.

Clique em cada um dos mapas e faça o seguinte processo, como ilustrado em cada imagem respectiva. No painel à esquerda clique em Layout, certifique-se do campo abaixo de item selecionado corresponde ao desejado, deixe marcado **Controlar a visibilidade usando valor** e selecione o campo correspondente ao item selecionado

### Mapa Cidade
O item selecionado deverá ser Cidade (ou o nome da planilha dado por você) e o campo corresponde a ser utilizado na visibilidade é **Visibilidade Cidade**
![](https://raw.githubusercontent.com/reprograma/on29-python-s16-dashboard/main/assets/exercicio-sala-23-visibilidade-cidade.png "Figura 23")

### Mapa Estado
O item selecionado deverá ser Estado (ou o nome da planilha dado por você) e o campo corresponde a ser utilizado na visibilidade é **Visibilidade Estado**
![](https://raw.githubusercontent.com/reprograma/on29-python-s16-dashboard/main/assets/exercicio-sala-24-visibilidade-estado.png "Figura 24")

### Mapa País
O item selecionado deverá ser País (ou o nome da planilha dado por você) e o campo corresponde a ser utilizado na visibilidade é **Visibilidade País**
![](https://raw.githubusercontent.com/reprograma/on29-python-s16-dashboard/main/assets/exercicio-sala-25-visibilidade-pais.png "Figura 25")


### Filtros na Planilha Cidade e Formatação de Título
Volte para planilha de Cidade e realize as seguintes ações

#### Filtro
Arraste o campo **Filtro Estado** para *Filtros* e deixe marcada apenas a opção **Verdadeiro**

⚠️ Caso não esteja aparecendo o valor Verdadeiro E Falso, certifique-se que o parâmetro **Parâmetro Estado Selecionado** esteja preenchido no seu dashboard e tente novamente.

#### Título
Selecione *Editar Título* e usando o menu de seleção **Inserir** adicione o campo de parâmetro de estado selecionado. O código ficaria algo como:

`<Nome da planilha> | <Parâmetros.Parâmetro Estado Selecionado>`

![](https://raw.githubusercontent.com/reprograma/on29-python-s16-dashboard/main/assets/exercicio-sala-26-parametro-titulo.png "Figura 26")

E clique em OK

Volte para o Dashboard e divirta-se.