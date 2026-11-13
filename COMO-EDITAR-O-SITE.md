# Como editar o site pelo painel

Os produtos e outras áreas do site são editados por um painel, sem mexer em código.
O painel é o **Pages CMS**: <https://app.pagescms.org>

O painel tem três telas no menu: **Produtos**, **Categorias (abas)** e **Pedido e WhatsApp**.
Elas salvam nos arquivos `data/produtos.json`, `data/categorias.json` e `data/pedido.json`.
O site lê esses arquivos e monta sozinho as abas, os cartões e a janela de pedido.
Depois de salvar, o site atualiza em cerca de 1 a 2 minutos.

## Primeiro acesso (feito uma vez pelo dono do repositório)

1. Entre em <https://app.pagescms.org> e clique em **Sign in with GitHub**.
2. Autorize o Pages CMS e instale o aplicativo dele na conta que tem o repositório `grafica-siao-v3`.
3. Escolha o repositório `grafica-siao-v3`. Vão aparecer **Produtos**, **Categorias (abas)** e **Pedido e WhatsApp** no menu.
4. Para outra pessoa editar sem conta no GitHub, convide pelo e-mail em **Settings → Collaborators** (ou equivalente no painel).

## Adicionar um produto

1. Abra **Produtos** e clique em **Add an entry** (adicionar).
2. Preencha:
   - **Nome do produto**: o nome que aparece no cartão.
   - **Categoria**: em qual aba ele aparece.
   - **Mostrar no site**: deixe marcado.
   - **Fotos**: envie de 1 a 6 fotos. A primeira é a principal. Prefira fotos em pé ou quadradas, com até uns 3 MB cada (foto maior dá o erro 413; reduza antes, por exemplo em squoosh.app).
   - **Descrição curta**: aparece na janela de pedido.
3. Clique em **Save** (salvar).

Pronto: o produto aparece no site com o botão "Montar pedido".
Sem tabela de preços, o pedido chega no WhatsApp como **orçamento** (o cliente informa a quantidade).

## Colocar preço em um produto

Em **Preços por quantidade**, adicione uma linha para cada quantidade:

| Quantidade | Preço total |
|---|---|
| 250 | 69 |
| 500 | 89 |
| 1000 | 129 |

O preço é o **valor total do pedido** naquela quantidade, não o preço por unidade.

### Opções (material, acabamento, tamanho…)

Em **Opções**, crie um grupo para cada escolha do cliente:

- **Nome da opção**: ex. "Material".
- **Como o cliente escolhe**:
  - *Escolher só um*: o cliente marca uma (ex. tipo de papel). A primeira já vem marcada, então deixe o acréscimo dela em 0.
  - *Pode escolher vários*: o cliente marca quantas quiser (ex. acabamentos).
- **Escolhas**: cada item com nome, acréscimo e tipo de acréscimo:
  - *Valor fixo (R$)*: soma esse valor ao pedido. Ex. cantos arredondados + R$ 25.
  - *Porcentagem do preço base (%)*: soma uma porcentagem do preço da quantidade escolhida. Ex. frente e verso + 30%.
  - *Por unidade (R$ cada)*: multiplica pela quantidade. Ex. cordão + R$ 4,50 cada.

**Conta do valor:** preço da quantidade + acréscimos das escolhas marcadas.

## Outras edições

- **Esconder um produto** sem apagar: desmarque **Mostrar no site**.
- **Mudar a ordem**: arraste os produtos na lista. A ordem do painel é a ordem no site.
- **Categorias (abas)** (tela própria no menu): muda o nome, o texto e a cor da faixa de cada aba.
  Para criar uma categoria nova, é preciso incluir o nome dela também na lista do campo "Categoria" (no arquivo `.pages.yml`) — peça a quem cuida do site.
- **Pedido e WhatsApp** (tela própria no menu): condições de prazo, entrega, pagamento e o aviso que aparecem na janela de pedido.
  - **WhatsApp que recebe os pedidos**: só números, com 55 e DDD.
  - **Os preços ainda são de exemplo**: desmarque quando os preços forem os reais. Enquanto marcado, a janela de pedido mostra o aviso "Preços de exemplo".

## Outras áreas do site

Além dos produtos, o menu do painel tem:

- **Quem somos (fotos)**: as fotos das duas molduras da seção Quem somos (a grande e a pequena). Cada moldura troca de foto sozinha. Com uma foto só, ela fica parada.
- **Portfólio**: cada item é uma foto da grade, com título, categoria (que vira o botão de filtro) e tamanho na grade: *Normal*, *Alta* (ocupa duas linhas) ou *Larga* (ocupa duas colunas).
- **Editora (livros)**:
  - **Livros publicados**: título, autor, descrição, fotos do livro e o **mockup**. O mockup é a imagem do livro em PNG com fundo transparente; ela aparece na estante. Enquanto não houver mockup, o site desenha uma capa provisória com o título.
  - **Fotos que saem do livro aberto**: as até 5 fotos que aparecem quando o visitante clica no livro grande.
- **Depoimentos**: nome, linha abaixo do nome, o texto e a foto ou logo (de preferência quadrada).

As mesmas regras de foto valem aqui: até uns 3 MB por foto.

## Se algo der errado

- Produto sem nome é ignorado. Tabela de preços com linha incompleta faz o produto voltar para "sob orçamento".
- O GitHub guarda cada alteração. Dá para voltar uma versão anterior pelo histórico dos arquivos da pasta `data` no repositório.
