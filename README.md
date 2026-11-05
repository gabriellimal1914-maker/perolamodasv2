# Pérola Modas — Loja virtual

Site estático (HTML, CSS e JavaScript puros), sem build e sem dependências. Pronto para GitHub + Vercel.

Desenvolvido por **GL Business Tech** · [@glbusinesstech](https://www.instagram.com/glbusinesstech/)

---

## Estrutura

```
perola-modas/
├── index.html                  ← página da loja (todas as telas)
├── vercel.json                 ← configuração da Vercel (cache e segurança)
├── robots.txt
├── site.webmanifest            ← ícone ao "adicionar à tela inicial" no celular
├── assets/
│   ├── css/style.css           ← visual
│   ├── js/produtos.js          ← CATÁLOGO E CONFIGURAÇÕES (o arquivo que a loja edita)
│   ├── js/app.js               ← funcionamento da loja (não precisa mexer)
│   └── img/
│       ├── favicon.svg, apple-touch-icon.png, og.jpg
│       └── produtos/           ← fotos dos produtos (900×1200, proporção 3:4)
└── README.md
```

## Publicar (GitHub + Vercel)

1. Crie um repositório no GitHub (ex.: `perola-modas`).
2. Envie **todos os arquivos desta pasta** para a raiz do repositório, mantendo a pasta `assets` como está.
   O `index.html` precisa ficar na raiz, não dentro de outra pasta.
3. Na Vercel: **Add New → Project → Import** o repositório.
   - Framework Preset: **Other**
   - Build Command: deixe vazio
   - Output Directory: deixe vazio (raiz)
4. Clique em **Deploy**. A cada commit no GitHub, a Vercel publica a nova versão sozinha.
5. Domínio próprio: Vercel → projeto → **Settings → Domains**.

> Os botões de WhatsApp, Instagram, Google Maps e o preenchimento de endereço pelo CEP
> funcionam no site publicado. Na prévia dentro do Claude eles ficam bloqueados.

## Como a compra funciona

1. A cliente monta a sacola (cor, tamanho e quantidade).
2. No checkout informa nome, WhatsApp e entrega: em casa (endereço preenchido pelo CEP) ou retirada em Madureira ou Irajá.
3. Escolhe a forma de pagamento preferida (Pix, cartão ou combinar).
4. Ao enviar, o WhatsApp da loja abre com o pedido completo: itens, cores, tamanhos, valores, total, dados e entrega.
5. A loja confirma estoque, frete e envia a cobrança pelo WhatsApp.

Há também o botão **"Pedir direto pelo WhatsApp"** na sacola, que envia só a lista de itens.

## Editar produtos, preços e fotos

Tudo fica em `assets/js/produtos.js`:

- **Preço:** altere `preco` (e `promo` para preço promocional; `0` = sem promoção).
- **Novo produto:** copie um bloco `{ id: ..., nome: ..., ... }` e ajuste.
  O `id` vira o endereço da página (`#produto-seu-id`), sem espaços ou acentos.
- **Fotos:** coloque o arquivo em `assets/img/produtos/` (de preferência 900×1200) e liste o nome em `fotos`, por cor.
  A primeira foto é a capa; a segunda aparece ao passar o mouse.
- **Estoque real (opcional):** `estoque: { "P|preto": 3, "M|preto": 0 }`.
  Sem isso, o site mostra uma disponibilidade de demonstração.
- **Cupons:** em `config.cupons`.
- **Aviso de demonstração:** quando os preços forem os reais, mude `modoDemonstracao` para `false`.

## Antes de divulgar para clientes

- [ ] Substituir os preços ilustrativos pelos reais (hoje só o Conjunto Canelado tem preço real) e mudar `modoDemonstracao` para `false`.
- [ ] Confirmar se a retirada nas lojas é oferecida (está como opção no checkout).
- [ ] Revisar o texto de trocas e privacidade (página "Trocas, privacidade e LGPD").
- [ ] Informar o CNPJ no rodapé (`index.html`, procure "CNPJ a informar").
- [ ] Fotos das categorias que ainda aparecem com "Foto em breve" (alfaiataria, fitness, cintos, semijoias, bijuterias, relógios, beleza).
- [ ] Remover o cupom `DEMO10` de `config.cupons`.

## Próximas etapas (fora desta versão)

- Pagamento online (Mercado Pago) e cálculo de frete automático (Melhor Envio/Correios).
- Painel com login e banco de dados (ex.: Supabase).
  O painel atual (`#painel`, link "Acesso da equipe" em Minha conta) é uma prévia que guarda dados só no navegador de quem usa.
- Google Analytics 4 / Meta Pixel: os eventos já são enviados ao `dataLayer`; basta adicionar o código de instalação no `index.html`.
