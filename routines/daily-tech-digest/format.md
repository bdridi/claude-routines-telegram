# daily-tech-digest — format du message

Un **seul** message Telegram par jour, envoyé avec `parse_mode=HTML` et
`disable_web_page_preview=true`. Limite dure de Telegram : 4096 caractères.

## Gabarit

```
🗞 <b>Veille — dimanche 30 août</b>

🤖 <b>IA / Agents</b>
• <a href="URL">Titre court</a>
  Ce que c'est, en une phrase. Puis ce que ça change concrètement —
  l'angle qui permet de décider si ça mérite un clic.

🏗 <b>Archi</b>
• <a href="URL">Titre court</a>
  Idem : le fond, puis la portée.

🧱 <b>System design</b>
• <a href="URL">Titre court</a>
  …

🛠 <b>Dev</b>
• <a href="URL">Titre court</a>
  …

📡 <b>Radar — ThoughtWorks Vol 34</b>
• <b>Nom de l'entrée</b> — Adopt
  Ce que c'est, et pourquoi le radar la place à ce niveau.
```

## Profondeur des résumés

**Deux à trois lignes par item.** Le test à appliquer : le lecteur doit pouvoir décider de **ne
pas** ouvrir le lien. Dire ce que c'est, puis ce que ça change — jamais une paraphrase du titre.

Si un item n'apporte rien qu'on puisse formuler ainsi, c'est qu'il ne mérite pas sa place dans le
digest. Le supprimer plutôt que de le meubler.

## Section 📡 Radar

**Quotidienne.** Elle porte 2 à 3 entrées piochées dans le radar en cours d'exploitation (voir la
section dédiée de `sources.md`) et se place en dernier.

Ces entrées ne sont pas de l'actualité. Pour chacune : le nom, la position du radar
(*Adopt* / *Trial* / *Assess* / *Hold*), **puis une ligne d'explication**. Une entrée en *Hold*
vaut souvent mieux qu'une en *Adopt* : elle dit ce qu'il faut arrêter de faire.

**La ligne d'explication n'est pas optionnelle.** Sans elle, l'entrée n'a aucune valeur : le nom
et la position ne disent pas *pourquoi*, et obligent à ouvrir le radar — exactement ce que le
digest doit éviter.

❌ Insuffisant, à ne pas reproduire :

```
📡 <b>Radar — ThoughtWorks Vol 34</b>
• MCP par défaut — Hold
• Instructions d'agent qui s'accumulent — Hold
```

✅ Attendu :

```
📡 <b>Radar — ThoughtWorks Vol 34</b>
• <b>MCP par défaut</b> — Hold
  Brancher un serveur MCP là où un appel d'outil simple suffirait. Le radar
  déconseille d'en faire le réflexe : la couche de protocole coûte plus qu'elle
  ne rapporte tant qu'il n'y a qu'un seul client.
• <b>Instructions d'agent qui s'accumulent</b> — Hold
  Les fichiers de consignes grossissent à chaque incident et personne n'enlève
  jamais rien. Au-delà d'un certain volume l'agent les suit moins bien — le
  radar recommande de les tailler régulièrement.
```

Si tu ne sais pas expliquer une entrée, ne la retiens pas : prends-en une autre. La marquer
traitée dans le registre sans l'avoir expliquée la gâche définitivement, elle ne repassera plus.

L'édition figure dans l'en-tête de section, pas sur chaque ligne :
`📡 <b>Radar — ThoughtWorks Vol 34</b>`. **Un seul radar par jour** — la rotation entre les
quatre est décrite dans `sources.md`.

Les jours où plus aucune entrée n'est disponible — édition épuisée, aucune nouvelle parue — la
section est absente. On ne recycle pas pour meubler.

## Longueur

C'est le point de tension du format : ~12 items à 2-3 lignes, URLs comprises, situent le message
autour de **3700-3900 caractères** pour un plafond dur à 4096. **Viser 3800 maximum.**

Mesurer avant d'envoyer (`wc -c`). Si ça dépasse, couper dans cet ordre :

1. **les news les plus faibles** — une news manquée revient le lendemain ;
2. en dernier recours, ramener les news restantes à une seule ligne.

**Ne jamais sacrifier les entrées de radar.** Elles ne reviendront pas : elles auront été marquées
traitées dans le registre. C'est la partie non rattrapable du digest.

## Règles de rédaction

- **Français**, y compris pour résumer une source anglophone. Garder les termes techniques en
  anglais quand la traduction serait maladroite (`prompt caching`, pas « mise en cache d'invite »).
- **Titre court** : reformuler si le titre d'origine fait trois lignes.
- **Sections vides omises**, en-tête compris. Pas de « rien à signaler aujourd'hui » par section.
- **Journée vide** : si vraiment rien ne passe le filtre, envoyer un message d'une ligne le disant,
  plutôt que de remplir.

## HTML autorisé par Telegram

`<b>`, `<i>`, `<u>`, `<s>`, `<code>`, `<pre>`, `<a href="">`. Rien d'autre — pas de `<ul>`, pas de
`<br>` (les sauts de ligne sont littéraux). Échapper `&`, `<` et `>` dans le **texte** en
`&amp;`, `&lt;`, `&gt;`, sinon Telegram rejette le message entier avec `can't parse entities`.
