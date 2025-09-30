Parfait — voici un modèle d’email HTML prêt à l’emploi, responsive et compatible avec la plupart des clients mail. J’ai laissé l’emplacement où insérer votre variable `{{ $json.text }}` — il suffit de remplacer / injecter la variable à cet endroit (ou coller `{{ $json.text }}` si vous l’utilisez tel quel dans n8n).

Je fournis aussi quelques objets (subject) et une version texte simple (pour la partie plain-text).

---

### 3 propositions d'objet (subject)

* 🤯 Ce que personne ne vous dit sur la fortune d'Elon Musk
* Fortune d'Elon Musk : vision vs cash — Qu'en pensez-vous ?
* Elon Musk, richesse et innovation — votre avis ?

---

### Modèle HTML (copier-coller)

```html
<!doctype html>
<html lang="fr">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width,initial-scale=1">
  <title>Newsletter</title>
  <style>
    /* Styles inline-friendly ; garder simple pour compatibilité e-mail */
    body { margin:0; padding:0; -webkit-text-size-adjust:100%; -ms-text-size-adjust:100%; font-family: Arial, Helvetica, sans-serif; background-color:#f4f4f6; color:#333333; }
    table { border-collapse:collapse; }
    .container { width:100%; max-width:680px; margin:0 auto; background:#ffffff; border-radius:8px; overflow:hidden; }
    .header { padding:18px 24px; text-align:left; background:linear-gradient(90deg,#0f172a,#0b84ff); color:#ffffff; }
    .preheader { display:none !important; visibility:hidden; opacity:0; height:0; width:0; }
    .content { padding:22px 24px; line-height:1.5; font-size:16px; color:#1f2937; }
    .cta { display:block; width:100%; text-align:center; margin:18px 0 6px; }
    .btn { display:inline-block; padding:12px 18px; background:#0b84ff; color:#ffffff; text-decoration:none; border-radius:6px; font-weight:600; }
    .meta { font-size:13px; color:#6b7280; padding:0 24px 22px; }
    .social { padding: 0 24px 22px; }
    .footer { font-size:12px; color:#9ca3af; padding:18px 24px; text-align:center; }
    @media (max-width:480px){
      .content { font-size:15px; padding:16px; }
      .header { padding:14px 16px; }
    }
  </style>
</head>
<body>
  <!-- preheader text: visible in inbox preview -->
  <span class="preheader">Découvrez la réalité derrière la « fortune » d'Elon Musk — vision ou cash ?</span>

  <table role="presentation" width="100%" cellpadding="0" cellspacing="0">
    <tr>
      <td align="center" style="padding:20px;">
        <table role="presentation" class="container" width="100%" cellpadding="0" cellspacing="0">
          <!-- Header -->
          <tr>
            <td class="header">
              <h1 style="margin:0;font-size:20px;">[Votre Newsletter]</h1>
              <div style="font-size:13px; margin-top:4px; opacity:0.95;">Décryptage, opinions & partage</div>
            </td>
          </tr>

          <!-- Body / Content -->
          <tr>
            <td class="content">
              <!-- Ici insérer la variable contenant le contenu généré -->
              <!-- Exemple : {{ $json.text }} -->
              {{ $json.text }}

              <!-- Call to action -->
              <div class="cta">
                <a href="#" class="btn" target="_blank" rel="noopener">Répondre & partager votre avis</a>
              </div>
            </td>
          </tr>

          <!-- Meta / suggestion -->
          <tr>
            <td class="meta">
              <p style="margin:0 0 8px 0;">Vous avez aimé cet article ? Partagez-le : taguez un ami ou postez votre commentaire.</p>
              <p style="margin:0;">Suivez-nous pour plus d'analyse et d'articles exclusifs.</p>
            </td>
          </tr>

          <!-- Social (optionnel) -->
          <tr>
            <td class="social">
              <table role="presentation" cellpadding="0" cellspacing="0">
                <tr>
                  <td style="padding-right:10px;"><a href="#" target="_blank" rel="noopener">Twitter</a></td>
                  <td style="padding-right:10px;">|</td>
                  <td style="padding-right:10px;"><a href="#" target="_blank" rel="noopener">LinkedIn</a></td>
                  <td style="padding-right:10px;">|</td>
                  <td><a href="#" target="_blank" rel="noopener">Facebook</a></td>
                </tr>
              </table>
            </td>
          </tr>

          <!-- Footer -->
          <tr>
            <td class="footer">
              <div>Vous recevez cet e-mail parce que vous êtes abonné à [Votre Liste].</div>
              <div style="margin-top:6px;">
                <a href="#" style="color:#9ca3af; text-decoration:underline;">Se désabonner</a> •
                <a href="#" style="color:#9ca3af; text-decoration:underline;">Gérer mes préférences</a>
              </div>
            </td>
          </tr>

        </table>
      </td>
    </tr>
  </table>
</body>
</html>
```

---

### Version texte (plain-text) à inclure en alternative

```
[Votre Newsletter]

🤯 Ce que personne ne vous dit sur la fortune d'Elon Musk !

{{ $json.text }}

Répondre & partager votre avis : [lien]
Se désabonner : [lien]
```

---

### Remarques / conseils pratiques

* Insérez `{{ $json.text }}` EXACTEMENT à l’endroit souhaité si vous utilisez n8n et que la variable contient tout le HTML/texte déjà formaté.
* Si la variable contient des retours à la ligne `\n`, elle s’affichera comme texte brut — vous pouvez transformer les sauts de ligne en `<br>` si vous préférez conserver un rendu HTML côté contenu.
* Testez l’email avec des outils comme Litmus/Email on Acid (ou simplement en vous l’envoyant à plusieurs clients : Gmail, Outlook mobile, Apple Mail) pour vérifier le rendu.
* Si vous voulez que j’adapte le style (couleurs, logo, CTA avec un vrai lien, ou insertion automatique d’un bouton « Lire en ligne »), dites-moi les détails et je fournis la variante immédiatement.

Souhaitez-vous que j’ajoute un logo en haut, ou que je convertisse les sauts de ligne `\n` en `<p>`/`<br>` automatiquement dans le template ?
