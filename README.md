# Fasical Cafe

PDV (ponto de venda) completo para a cafeteria **Fasical Cafe**, em **um único arquivo HTML**, sem instalação, sem internet e sem servidor. Todos os dados ficam no navegador (`localStorage`).

## Como abrir

1. Dê um duplo clique em `index.html`.
2. Pronto. O app abre no navegador com cardápio de exemplo já cadastrado.

> Funciona melhor no Chrome, Edge ou Firefox atualizados. Para usar no celular/tablet, sirva a pasta por um servidor local ou hospede o arquivo em qualquer host estático (o `localStorage` é por navegador e por endereço, então os dados não são compartilhados entre dispositivos).

## O que tem

**PDV / Cardápio**
- 17 produtos de exemplo em 5 categorias (Cafés, Bebidas, Doces, Salgados, Combos).
- Busca por nome e filtro por categoria.
- Adicionar, aumentar, diminuir e remover itens; observação por item.
- Cadastro de produtos com foto (upload ou arrastar a imagem); a foto aparece no cardápio e é otimizada automaticamente. Sem foto, o produto usa o ícone escolhido.
- Tipos de pedido: balcão, mesa (com nome configurável) ou delivery (cliente, telefone, endereço e taxa de entrega).
- Desconto em valor ou porcentagem.
- Comandas em aberto salvas automaticamente, com troca entre comandas e código sequencial (`#001`, `#002`...).
- Impressão da comanda com preço unitário, subtotal, desconto (valor ou %) e total.
- Comanda e comprovante podem ser impressos com a logo da cafeteria (ligado por padrão em **Configurações**).
- Layout responsivo: no celular, o pedido abre como painel inferior.

**Pagamento**
- Dinheiro, Pix, débito, crédito e vale.
- Pagamento dividido entre várias formas.
- Campo de valor recebido, botões rápidos (R$ 20 / 50 / 100 / valor exato) e cálculo de troco em tempo real.
- Só conclui quando o total estiver quitado.
- Comprovante na tela e impressão em bobina de 76–80 mm.

**Caixa**
- Abertura com fundo de troco.
- Suprimento (entrada) e sangria (retirada) com observação.
- Vendas da sessão por forma de pagamento.
- Dinheiro esperado em caixa = fundo + dinheiro recebido + suprimentos − sangrias.
- Fechamento com valor contado, diferença e histórico de fechamentos.

**Produtos e configurações**
- Criar, editar, ativar/desativar e excluir produtos e categorias.
- Cada produto e categoria tem um ícone de linha próprio, escolhido em uma grade visual no cadastro. São 19 opções (cafés, bebidas, doces, salgados e combos); o ícone aparece no cardápio, nos filtros e nas listas quando não há foto.
- Nome da loja, telefone, endereço e operador.
- Aba **Mesas** para renomear, adicionar e remover mesas (até 40). Os nomes aparecem no seletor do pedido, nas comandas, nos comprovantes e nos relatórios; renomear uma mesa atualiza as comandas abertas nela.
- Backup dos dados em JSON e restauração por arquivo.
- Restaurar apenas o cardápio de exemplo ou apagar todos os dados.

**Relatórios**
- Vendas do dia, faturamento, ticket médio, itens vendidos e formas de pagamento.
- Filtro por data e exportação em CSV.
- Edição do histórico de vendas: em **Relatórios**, clique no ícone de lápis ao lado da comanda para corrigir cliente, tipo/mesa, itens, quantidades, desconto, taxa de entrega e pagamentos; os totais são recalculados e o caixa é atualizado.
- Exclusão de vendas do histórico: no mesmo local, clique no ícone de lixeira para remover uma venda (com confirmação); o caixa e os relatórios são atualizados.
- Impressão do relatório do dia em A4, com resumo financeiro, formas de pagamento, mais vendidos e lista completa de vendas.

## Impressão

Use o botão de impressão no comprovante. O layout já está preparado para bobina térmica (76–80 mm): o app e os modais são ocultados e só o cupom é impresso. Nas opções de impressão do navegador, desative cabeçalhos/rodapés e escolha o tamanho de papel correto.

A logo aparece no topo da comanda, do comprovante e do relatório (52 mm na bobina e 40 mm no A4). No app ela é exibida em branco sobre o cabeçalho escuro; na impressão sai em preto para ficar legível no papel. Para imprimir sem ela, desmarque **Imprimir a logo da cafeteria** em **Configurações**.

O relatório de vendas é impresso em folha **A4 em retrato**, com o resumo do dia e a lista de vendas. Na tela de relatórios, escolha a data e clique em **Imprimir relatório**. Se não houver vendas no dia, o relatório sai com os totais zerados.

## Ícones

A interface usa ícones de linha desenhados em SVG, com a mesma linguagem visual em todo o app: cardápio, filtros, comandas, pagamentos, caixa, relatórios e botões. Os ícones herdam a cor do texto ao redor, então acompanham o contraste de cada área automaticamente.

- **Produtos e categorias:** no cadastro, escolha o ícone na grade visual. O produto sem foto usa esse ícone no cardápio; a categoria usa no filtro e na lista de produtos.
- **Compatibilidade:** backups antigos que guardavam emojis são convertidos para o ícone equivalente ao abrir ou importar os dados.
- **Impressão:** comandas, comprovantes e relatórios são impressos sem emojis; a logo e o texto continuam em preto para leitura no papel.

## Onde os dados ficam

- Chave: `pdv.cafeteria.v1` no `localStorage` do navegador.
- Nada é enviado para a internet.
- Limpar os dados do site no navegador apaga o PDV. Faça backup em **Configurações → Exportar backup**.
- Fotos de produtos são comprimidas automaticamente (até 640 px) e salvas junto com os dados. Como o `localStorage` tem limite de alguns MB, dezenas de fotos já ocupam boa parte do espaço — o backup JSON também inclui as imagens.
- Para trocar de computador: exporte o JSON em um, importe no outro.

## Estrutura

```
pdv-cafeteria/
├── index.html   # app completo (HTML + CSS + JS)
└── README.md
```

## Limitações conhecidas

- É um app local: os dados não sincronizam entre dispositivos e dependem do navegador usado.
- A impressão depende do navegador e da impressora; não há integração direta com gaveta de dinheiro, balança ou TEF.
- Sem controle de usuários/permissões — indicado para um operador por caixa.
