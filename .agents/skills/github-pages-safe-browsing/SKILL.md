---
name: github-pages-safe-browsing
description: Prevents "Deceptive site ahead" (Site Perigoso) warnings on GitHub Pages by automatically injecting the Google Search Console verification meta tag and guiding the user to request a review.
---

# GitHub Pages Safe Browsing Skill

## Context
When publishing static HTML pages to GitHub Pages (especially those with forms or specific keywords), Google Safe Browsing often flags them as "Deceptive site ahead" (Site Perigoso) by mistake. To quickly resolve this, the domain needs to be verified in Google Search Console (GSC) so a review can be requested.

## Trigger
Use this skill whenever you are asked to create, modify, or publish an HTML file to GitHub Pages in this workspace.

## Instructions
1. **Inject the Verification Tag**: Always ensure that the following Google Site Verification meta tag is present inside the `<head>` of the HTML file before pushing it to GitHub:
   ```html
   <meta name="google-site-verification" content="a8G8-IzgJ9CWSWxhc-M0z06hG_lF-TDM7bJU0BZdSKE" />
   ```

2. **Inform the User**: After pushing the code, always inform the user that:
   - The verification tag has been embedded automatically.
   - If they encounter a red "Site Perigoso" screen when accessing the link, they do NOT need to run any scripts.
   - They just need to go directly to [Google Search Console](https://search.google.com/search-console), select the property (or add the URL prefix), click **"Solicitar Revisão"** (Request Review), and paste the standard justification.

3. **Standard Justification**: Provide the user with this exact justification to copy and paste in GSC:
   > "Este é um projeto de estudo/portfólio pessoal estático hospedado no GitHub Pages. Não há coleta de dados de usuários e não há envio de formulários (trata-se apenas de texto de orientação com links, não há captura de senhas). Houve um falso positivo pelo algoritmo do Google Safe Browsing. Peço que a restrição seja removida."
