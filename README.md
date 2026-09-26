# Vigtos — landing page

Página única e estática: `index.html` com CSS e JS embutidos. Sem build, sem Node. Abre direto no navegador.

| Arquivo | Para quê |
|---|---|
| `index.html` | a página |
| `og.png` | imagem do preview ao compartilhar o link (1200×630) |
| `apple-touch-icon.png` | ícone na tela de início do iPhone (180×180) |
| `.nojekyll` | impede o GitHub Pages de passar o site pelo Jekyll |
| `CNAME` | **ainda não existe** — ver "Domínio próprio" |

## Antes de publicar

1. **E-mail (desligado)** — o e-mail do rodapé está comentado no `index.html`. Para religar, busque por `contato@`,
   troque o endereço e tire a linha do comentário.
2. **Endereço público** — as tags `canonical`, `og:url` e `og:image` apontam para `https://vigtos.com.br/`.
   Enquanto o domínio não estiver ativo, troque pelo endereço do GitHub Pages
   (`https://USUARIO.github.io/REPOSITORIO/`). O `og:image` precisa de URL absoluta, senão o LinkedIn não mostra a imagem.
3. **Formulário (Web3Forms, gratuito)** — em [web3forms.com](https://web3forms.com), informe o e-mail que vai
   receber os pedidos; a chave de acesso chega nesse e-mail. No `index.html`, troque `SUA_CHAVE_WEB3FORMS`
   (busque por esse texto) pela chave. A chave pode ficar pública no HTML — ela só permite *enviar* para o seu e-mail.
   Enquanto não trocar, o formulário avisa "ainda não configurado". Todo botão de contato leva a este formulário.
4. **Analytics (opcional)** — o trecho do Cloudflare Web Analytics está comentado no fim do `<body>`, com o passo a passo.

## Publicar no GitHub Pages

1. Crie o repositório no GitHub e envie os arquivos para a branch `main`, na raiz:

   ```bash
   git init
   git add .
   git commit -m "Landing page Vigtos"
   git branch -M main
   git remote add origin https://github.com/USUARIO/REPOSITORIO.git
   git push -u origin main
   ```

2. No repositório: **Settings → Pages → Build and deployment**
   - Source: **Deploy from a branch**
   - Branch: **main**, pasta **/ (root)** → **Save**
3. Em um ou dois minutos o site está em `https://USUARIO.github.io/REPOSITORIO/`.

## Domínio próprio: `vigtos.com.br` pelo Registro.br

Faça só depois de comprar o domínio.

**1. DNS no Registro.br** — no painel, abra o domínio, escolha usar os servidores DNS do Registro.br e edite a zona
(modo avançado; os nomes dos menus podem mudar). Crie:

| Tipo | Nome | Valor |
|---|---|---|
| A | *(vazio — o próprio domínio)* | `185.199.108.153` |
| A | *(vazio)* | `185.199.109.153` |
| A | *(vazio)* | `185.199.110.153` |
| A | *(vazio)* | `185.199.111.153` |
| AAAA | *(vazio)* | `2606:50c0:8000::153` |
| AAAA | *(vazio)* | `2606:50c0:8001::153` |
| AAAA | *(vazio)* | `2606:50c0:8002::153` |
| AAAA | *(vazio)* | `2606:50c0:8003::153` |
| CNAME | `www` | `USUARIO.github.io.` |

**2. CNAME no GitHub** — em **Settings → Pages → Custom domain**, digite `vigtos.com.br` e salve.
Isso cria na raiz do repositório um arquivo `CNAME` com uma linha só:

```
vigtos.com.br
```

(Criar esse arquivo à mão tem o mesmo efeito.) Não ative antes do passo 1: com o CNAME ativo, o endereço
`github.io` passa a redirecionar para o domínio, e o site fica fora do ar até o DNS responder.

**3. HTTPS** — quando o GitHub mostrar a verificação de DNS concluída, marque **Enforce HTTPS**.
A propagação do DNS e a emissão do certificado podem levar de minutos a algumas horas.

**4. Tags** — volte `canonical`, `og:url` e `og:image` para `https://vigtos.com.br/`.

**Recomendado:** verifique o domínio na sua conta (**Settings da conta → Pages → Add a domain**). O GitHub pede um
registro TXT no Registro.br e, com isso, nenhum outro repositório consegue usar o domínio.

## Conferir o preview no LinkedIn

Depois de publicar, cole a URL no [Post Inspector](https://www.linkedin.com/post-inspector/). Ele mostra o card
e força o LinkedIn a buscar a versão nova — útil sempre que trocar `og.png` ou os textos do `<head>`.
