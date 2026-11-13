# Como adicionar e editar produtos

Os produtos do site são editados por um painel, sem mexer em código.
O painel é o **Pages CMS**: <https://app.pagescms.org>

Tudo o que é salvo no painel vai para o arquivo `data/produtos.json`.
O site lê esse arquivo e monta sozinho as abas, os cartões e a janela de pedido.
Depois de salvar, o site atualiza em cerca de 1 a 2 minutos.

## Primeiro acesso (feito uma vez pelo dono do repositório)

1. Entre em <https://app.pagescms.org> e clique em **Sign in with GitHub**.
2. Autorize o Pages CMS e instale o aplicativo dele na conta que tem o repositório `grafica-siao-v3`.
3. Escolha o repositório `grafica-siao-v3`. Vai aparecer **Produtos e preços** no menu.
4. Para outra pessoa editar sem conta no GitHub, convide pelo e-mail em **Settings → Collaborators** (ou equivalente no painel).

## Adicionar um produto

1. Abra **Produtos e preços** e, em **Produtos**, clique em **Add an entry** (adicionar).
2. Preencha:
   - **Nome do produto**: o nome que aparece no cartão.
   - **Categoria**: em qual aba ele aparece.
   - **Mostrar no site**: deixe marcado.
   - **Fotos**: envie de 1 a 6 fotos. A primeira é a principal. Prefira fotos em pé ou quadradas.
   - **Descrição curta**: aparece na janela de pedido.
3. Clique em **Save** (salvar).

Pronto: o produto aparece no site com o botão "Montar pedido".
Sem tabela de preços, o pedido chega no WhatsApp como **orçamento** (o cliente informa a quantidade).

## Colocar preço em um produto

Em **Tabela de quantidades e preços**, adicione uma linha para cada quantidade:

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
- **Categorias (abas)**: muda o nome, o texto e a cor da faixa de cada aba.
  Para criar uma categoria nova, é preciso incluir o nome dela também na lista do campo "Categoria" (no arquivo `.pages.yml`) — peça a quem cuida do site.
- **Condições**: prazo, entrega, pagamento e o aviso que aparecem na janela de pedido.
- **WhatsApp que recebe os pedidos**: só números, com 55 e DDD.
- **Os preços ainda são de exemplo**: desmarque quando os preços forem os reais. Enquanto marcado, a janela de pedido mostra o aviso "Preços de exemplo".

## Se algo der errado

- Produto sem nome é ignorado. Tabela de preços com linha incompleta faz o produto voltar para "sob orçamento".
- O GitHub guarda cada alteração. Dá para voltar uma versão anterior pelo histórico do arquivo `data/produtos.json` no repositório.
