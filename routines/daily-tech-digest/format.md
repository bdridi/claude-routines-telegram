# daily-tech-digest — format du message

Un **seul** message Telegram par jour, envoyé avec `parse_mode=HTML` et
`disable_web_page_preview=true`. Limite dure de Telegram : 4096 caractères — viser < 4000.

## Gabarit

```
🗞 <b>Veille — jeudi 28 août</b>

🤖 <b>IA / Agents</b>
• <a href="URL">Titre court</a> — une phrase de contexte.
• <a href="URL">Titre court</a> — une phrase de contexte.

🏗 <b>Archi</b>
• <a href="URL">Titre court</a> — une phrase de contexte.

🧱 <b>System design</b>
• <a href="URL">Titre court</a> — une phrase de contexte.

🛠 <b>Dev</b>
• <a href="URL">Titre court</a> — une phrase de contexte.
```

## Règles de rédaction

- **Français**, y compris pour résumer une source anglophone. Garder les termes techniques en
  anglais quand la traduction serait maladroite (`prompt caching`, pas « mise en cache d'invite »).
- **Une phrase par item**, qui dit ce que ça change — pas une paraphrase du titre.
- **Titre court** : reformuler si le titre d'origine fait trois lignes.
- **Sections vides omises**, en-tête compris. Pas de « rien à signaler aujourd'hui » par section.
- **Journée vide** : si vraiment rien ne passe le filtre, envoyer un message d'une ligne le disant,
  plutôt que de remplir.

## HTML autorisé par Telegram

`<b>`, `<i>`, `<u>`, `<s>`, `<code>`, `<pre>`, `<a href="">`. Rien d'autre — pas de `<ul>`, pas de
`<br>` (les sauts de ligne sont littéraux). Échapper `&`, `<` et `>` dans le **texte** en
`&amp;`, `&lt;`, `&gt;`, sinon Telegram rejette le message entier avec `can't parse entities`.
