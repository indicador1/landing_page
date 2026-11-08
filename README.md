# Site do desenvolvedor

Site estático (somente HTML e CSS, sem build e sem dependências) para o GitHub Pages, em português do Brasil.

Páginas: `index.html`, `privacy.html`, `termos.html`, `excluir-conta.html` e `404.html`. Estilos em `style.css`; imagens em `img/`.

## Antes de publicar

Procure o que ainda precisa ser ajustado (o link do Google Play):

```bash
grep -rn "URL DO GOOGLE PLAY" *.html
```

Também troque `img/icone-visao.png` pelo ícone real do app (a imagem atual é um placeholder).

## Ver o site no seu computador

Dentro desta pasta, rode:

```bash
python3 -m http.server 8000
```

Depois abra <http://localhost:8000/>. Deixe o terminal aberto enquanto estiver testando; ao fechá-lo, o endereço deixa de funcionar. Também dá para abrir o `index.html` direto no navegador.

## Publicar no GitHub Pages

O repositório é <https://github.com/indicador1/landing_page>.

1. Neste diretório, conecte e envie:

   ```bash
   git remote add origin https://github.com/indicador1/landing_page.git
   git push -u origin main
   ```

2. No GitHub, abra **Settings > Pages**, em **Build and deployment** escolha **Deploy from a branch**, selecione **main** e **/ (root)** e salve.
3. Aguarde alguns minutos até o site ficar no ar. O repositório precisa ser **público** (Pages em repositório privado exige plano pago), e o Google Play precisa conseguir abrir as URLs sem login.

## Usar o seu domínio

Com domínio próprio, o `/landing_page` some das URLs. O melhor é usar um **subdomínio** (por exemplo `visao.seudominio.com.br`).

1. O arquivo `CNAME` (sem extensão) já está na raiz do projeto com `page.estrategico.tec.br`. Se mudar o domínio, edite esse arquivo, faça commit e push.
2. No painel de DNS do seu domínio (para `.br`, em registro.br ou no provedor de DNS), crie:
   - **Subdomínio:** registro `CNAME`, nome `visao`, valor `indicador1.github.io`.
   - **Domínio raiz (sem subdomínio):** quatro registros `A` com `185.199.108.153`, `185.199.109.153`, `185.199.110.153` e `185.199.111.153`.
3. No GitHub, em **Settings > Pages > Custom domain**, digite o domínio e salve. Espere a verificação do DNS (pode levar de minutos a algumas horas).
4. Marque **Enforce HTTPS** quando a opção ficar disponível.
5. Opcional, mas recomendado: em <https://github.com/settings/pages>, verifique o domínio na sua conta.

## URLs finais esperadas

Sem domínio próprio:

| Campo no Google Play Console | URL |
| --- | --- |
| Site do desenvolvedor | `https://indicador1.github.io/landing_page/` |
| Política de privacidade | `https://indicador1.github.io/landing_page/privacy.html` |
| Termos de uso | `https://indicador1.github.io/landing_page/termos.html` |
| Exclusão de conta | `https://indicador1.github.io/landing_page/excluir-conta.html` |

Com o domínio próprio `page.estrategico.tec.br` (arquivo `CNAME` já incluído):

| Campo no Google Play Console | URL |
| --- | --- |
| Site do desenvolvedor | `https://page.estrategico.tec.br/` |
| Política de privacidade | `https://page.estrategico.tec.br/privacy.html` |
| Termos de uso | `https://page.estrategico.tec.br/termos.html` |
| Exclusão de conta | `https://page.estrategico.tec.br/excluir-conta.html` |

## Adicionar um novo app

Em `index.html`, copie o bloco comentado **MODELO PARA UM NOVO APP** para dentro de `<div class="apps-grid">` e ajuste id, ícone, textos e link do Google Play.

## Observações

- Todos os caminhos são relativos, então o site funciona em `indicador1.github.io/landing_page/` e também em domínio próprio.
- O ano do copyright (2026) está escrito direto no HTML, pois não há JavaScript. Atualize-o a cada ano nos rodapés.
- A `404.html` tem estilos embutidos, porque o GitHub Pages a serve em qualquer endereço inexistente (inclusive em subpastas). O botão "Voltar ao início" é relativo e só funciona quando o endereço errado está na raiz do site.
- O arquivo `.nojekyll` desativa o Jekyll no GitHub Pages.
