# Site do desenvolvedor

Site estático (somente HTML e CSS, sem build e sem dependências) para o GitHub Pages, em português do Brasil.

Páginas: `index.html`, `privacy.html`, `termos.html`, `excluir-conta.html` e `404.html`. Estilos em `style.css`; imagens em `img/`.

## Antes de publicar

Procure e substitua os campos pendentes:

```bash
grep -rnE "\[(NOME DA EMPRESA|EMAIL|PREENCHER|DATA|REVISAR|URL DO GOOGLE PLAY)" *.html
grep -rn "REVISAR" *.html
```

Também troque `img/icone-visao.png` pelo ícone real do app (a imagem atual é um placeholder).

## Ver o site no seu computador

Dentro desta pasta, rode:

```bash
python3 -m http.server 8000
```

Depois abra <http://localhost:8000/>. Deixe o terminal aberto enquanto estiver testando; ao fechá-lo, o endereço deixa de funcionar. Também dá para abrir o `index.html` direto no navegador.

## Publicar no GitHub Pages

1. Crie um repositório vazio no GitHub (por exemplo `site-desenvolvedor`), sem README.
2. Neste diretório, conecte e envie:

   ```bash
   git remote add origin https://github.com/USUARIO/REPO.git
   git push -u origin main
   ```

3. No GitHub, abra **Settings > Pages**, em **Build and deployment** escolha **Deploy from a branch**, selecione **main** e **/ (root)** e salve.
4. Aguarde alguns minutos até o site ficar no ar.

## URLs finais esperadas

Troque `USUARIO` e `REPO` pelos seus. Se o repositório se chamar `USUARIO.github.io`, o `/REPO` não existe.

| Campo no Google Play Console | URL |
| --- | --- |
| Site do desenvolvedor | `https://USUARIO.github.io/REPO/` |
| Política de privacidade | `https://USUARIO.github.io/REPO/privacy.html` |
| Termos de uso | `https://USUARIO.github.io/REPO/termos.html` |
| Exclusão de conta | `https://USUARIO.github.io/REPO/excluir-conta.html` |

## Adicionar um novo app

Em `index.html`, copie o bloco comentado **MODELO PARA UM NOVO APP** para dentro de `<div class="apps-grid">` e ajuste id, ícone, textos e link do Google Play.

## Observações

- Todos os caminhos são relativos, então o site funciona em `usuario.github.io/repo/`.
- O ano do copyright (2026) está escrito direto no HTML, pois não há JavaScript. Atualize-o a cada ano nos rodapés.
- A `404.html` tem estilos embutidos, porque o GitHub Pages a serve em qualquer endereço inexistente (inclusive em subpastas). O botão "Voltar ao início" é relativo e só funciona quando o endereço errado está na raiz do site.
- O arquivo `.nojekyll` desativa o Jekyll no GitHub Pages.
