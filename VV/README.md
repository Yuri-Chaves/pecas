<h1 style="color: #004A8F;">Bot produtos VV</h1>
<h3 style="color: #4F4F4F;">Bloco de Código 1</h3>
<p>Importação da Bibliotecas</p>
<h3 style="color: #4F4F4F;">Bloco de Código 2</h3>
<p>Definição das variáveis</p>
<p><span style="color: #005FDF;">vvProdutos</span>: URL dos produtos VV</p>
<p><span style="color: #005FDF;">codigosVV</span>: Lista vazia utilizada posteriormente para armazenar os códigos VV</p>
<p><span style="color: #005FDF;">notFound</span>: DataFrame para Logs</p>
<p><span style="color: #005FDF;">cwd</span>: Current Working directory, diretório onde o programa está sendo executado</p>
<p><span style="color: #005FDF;">df_query</span>: DataFrame do arquivo com os produtos VV</p>
<h3 style="color: #4F4F4F;">Bloco de Código 3</h3>
<p>Definição da função <span style="color: #008639;font-weight: 900;">def <span style="color: #2F80ED;font-weight: 400;">camel_case(<span style="color: #0095DA;font-weight: 400;">String</span>)</span></span>,responsável por transformar as strings em camelCase</p>
<h3 style="color: #4F4F4F;">Bloco de Código 4</h3>
<p>Definição da função <span style="color: #008639;font-weight: 900;">def <span style="color: #2F80ED;font-weight: 400;">findVVCod(<span style="color: #0095DA;font-weight: 400;">String</span>)</span></span>,responsável por encontrar o código VV no nome do produto. Recebe como parâmetro uma string contendo o nome do produto e retorna uma lista de strings contendo os códigos VV encontrados</p>
<h3 style="color: #4F4F4F;">Bloco de Código 5</h3>
<p>Definição da função <span style="color: #008639;font-weight: 900;">def <span style="color: #2F80ED;font-weight: 400;">buscaInfo(<span style="color: #0095DA;font-weight: 400;">Navegador, String, String</span>)</span></span>,responsável por realizar a busca das informações dos produtos. Recebe como parâmetro o navegador, o código VV e o índice da peça(utiliza o código Cotripal como índice).</p>
<ul>
    <li>Verifica se o código possui "-", caso não possuir finaliza a busca e passa para o próximo código.</li>
    <li>Cria 2 variáveis temporárias para armazenar a chave e o valor de cada atributo.</li>
    <li>Acessa a página do produto adicionando o código VV ao final da variável <span style="color: #005FDF;">vvProdutos</span>.</li>
    <li>Verifica se o produto foi encontrado buscando pela classe HTML "<span style="color: #EB5757;">itensEquipamentos</span>", se não encontrar a classe finaliza a busca e passa para o próximo código VV.</li>
    <li>Se encontrou a classe HTML "<span style="color: #EB5757;">itensEquipamentos</span>", cria um dicionário Python com o código Cotripal e uma lista com as montadoras. cada item na lista contém o nome da montadora, o código OEM(código original da peça) e os equipamentos onde a peça é aplicável.</li>
    <li>Inicia a montagem do dicionário Python com as informações do produto. Com informações de ID(cód.Cotripal), Nome, Descrição, Atributos, linha, família, aplicação, material, tratamento, dureza, acabamento</li>
    <li>Inicia a montagem do dicionário Python que armazena o ID(cód. Cotripal) e uma lista contendo as imagens do produto</li>
    <li>Abre os arquivos Json e escreve os dicionários</li>
</ul>
<h3 style="color: #4F4F4F;">Bloco de Código 6</h3>
<ul>
    <li><p><span style="color: #005FDF;">chrome_options</span> Define as opções do navegador, o argumento <span style="color: #005FDF;">headless</span> permite que o bot seja executado em segundo plano.</p></li>
    <li><p><span style="color: #005FDF;">servico</span> Define o serviço do navegador, forçando a utilizar um driver instalado temporariamente. Assim o bot pode ser executado em qualquer máquina com o Chrome instalado.</p></li>
    <li><p><span style="color: #005FDF;">nav</span> Inicializa o navegador em que o Bot irá rodar. Utilizando as configurações passadas por <span style="color: #005FDF;">chrome_options</span> e <span style="color: #005FDF;">servico</span></p></li>
</ul>
<h3 style="color: #4F4F4F;">Bloco de Código 7</h3>
<ul>
    <li>Abre os arquivos Json e escreve "[" para indicar um array de itens</li>
    <li>Cria um laço de repetição para cada produto na lista de produtos</li>
    <li>Envia para a função <span style="color: #2F80ED;font-weight: 400;">findVVCod</span> o nome de cada produto</li>
    <li>Para cada código retornado da função, verifica se o tamanho do código é maior 6 e envia o código VV e o código Cotripal para a função <span style="color: #2F80ED;font-weight: 400;">buscaInfo</span></li>
    <li>Abre os arquivos Json e escreve "]" para indicar o encerramento do array de itens</li>
</ul>
<h3 style="color: #4F4F4F;">Bloco de Código 8</h3>
<p>Apresenta o DataFrame de Logs gerados</p>
<h3 style="color: #4F4F4F;">Bloco de Código 9</h3>
<p>Salva o DataFrame de Logs com o nome <span style="color: #008639;font-weight: 900;">notFound.xlsx</span></p>