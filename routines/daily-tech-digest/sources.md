# daily-tech-digest — sources

Fichier de référence de la routine. **C'est lui qui fait foi**, pas le prompt : pour changer ce qui
est collecté, on édite ce fichier sur `main`.

Stratégie **hybride** : on passe d'abord sur les sources fixes de chaque thème, puis on comble avec
WebSearch les thèmes restés vides ou trop maigres.

Deux régimes cohabitent :
- les **sources quotidiennes** (ci-dessous par thème), soumises au filtre 48h ;
- les **radars et rapports de tendances** (section dédiée en fin de fichier), périodiques, qui
  suivent leurs propres règles — ils ne sont pas consultés tous les jours.

---

## Règles de sélection

- **Fraîcheur** : uniquement ce qui est paru dans les **dernières 48h**. Un article de la semaine
  dernière ne passe pas, même s'il est bon.
- **Volume** : 8 à 10 items au total, 2 à 3 par thème. Mieux vaut 6 bons items que 10 tièdes.
- **Anti-doublon** : rien qui figure déjà dans les 7 derniers fichiers de `digests/`.
- **Exclusions** : annonces marketing, levées de fonds, classements « top 10 outils », contenu
  généré à la chaîne, articles derrière un paywall dur.
- **Critère de tri** : est-ce que ça change quelque chose à la façon de construire des systèmes ?
  Une release de modèle qui débloque un usage, oui. Un benchmark de plus, non.
- **Pas de remplissage** : si un thème n'a rien de solide aujourd'hui, on omet la section.

---

## 🤖 IA / LLM / agents

Sources fixes :
- https://www.anthropic.com/news
- https://deepmind.google/discover/blog/
- https://simonwillison.net/
- https://huggingface.co/papers
- https://news.ycombinator.com/ — ne retenir que les items IA avec de la discussion

⚠️ `openai.com/news` renvoie **403** à WebFetch (protection anti-bot). Ne pas le fetcher :
passer par WebSearch avec `site:openai.com news` ou `OpenAI announcement this week`.

Requêtes de secours :
- `LLM release this week`
- `AI agents framework announcement`
- `inference cost breakthrough`
- `OpenAI announcement this week`

## 🏗 Architecture logicielle

Sources fixes :
- https://martinfowler.com/
- https://www.infoq.com/architecture-design/

`thoughtworks.com/radar` a migré vers la section **Radars & rapports de tendances** en fin de
fichier — il est semestriel, il n'a rien à faire dans le passage quotidien.

Requêtes de secours :
- `software architecture article this week`
- `microservices monolith lessons learned`

## 🧱 System design / scalabilité

Sources fixes :
- https://blog.cloudflare.com/
- https://stripe.dev/blog/topic/engineering

⚠️ Sources retirées, vérifiées défaillantes au premier run :
- `netflixtechblog.com` → **403** à WebFetch (Medium bloque les bots).
- `highscalability.com` → contenu figé en 2024, le site ne publie plus.
- `discord.com/category/engineering` → la page n'affiche aucune date de publication,
  impossible d'appliquer le filtre 48h.
- `stripe.com/blog/engineering` → redirige en 301 vers `stripe.dev/blog/topic/engineering`,
  utiliser directement la cible.

Ces trois premiers sont à couvrir par WebSearch.

Requêtes de secours :
- `engineering blog post-mortem outage`
- `database scaling engineering blog`
- `Netflix OR Discord engineering blog this week`

## 🛠 Dev / langages / craft

Sources fixes :
- https://github.blog/
- https://blog.rust-lang.org/
- https://go.dev/blog/
- https://devblogs.microsoft.com/typescript/

Requêtes de secours :
- `programming language release notes this week`

---

## 📡 Radars & rapports de tendances

Sources **périodiques** (semestrielles à annuelles) qui cadrent le paysage plutôt que d'annoncer
l'actualité. Elles ne relèvent pas du même régime que le reste du fichier.

### Comment on les exploite

Un radar n'est pas une news : c'est un gisement. Le signaler une fois le jour de sa parution
gâcherait 95% de son contenu. On l'**exploite progressivement** à la place.

**Chaque jour**, piocher **2 à 3 entrées** encore non traitées dans l'édition courante — une
seule source à la fois, épuisée avant de passer à la suivante.

La cadence quotidienne n'est pas cosmétique. Un ThoughtWorks Radar compte ~100 blips : à 2-3 par
semaine il faudrait ~40 semaines pour l'épuiser, soit plus qu'un semestre — l'édition suivante
sortirait avant la fin et on n'aurait jamais fait le tour. En quotidien, c'est **5 à 7 semaines**,
puis on enchaîne sur le radar suivant. Les quatre sources tiennent dans l'année.

Ce qu'on retient d'une entrée : ce que c'est, pourquoi le radar la place là (*Adopt*, *Trial*,
*Assess*, *Hold*), et ce que ça change concrètement. Une entrée en *Hold* vaut souvent mieux
qu'une entrée en *Adopt* : elle dit ce qu'il faut arrêter de faire.

**Priorité de sélection**, dans cet ordre :
1. Ce qui touche **agents, harness, RAG, orchestration LLM**.
2. Ce qui est en *Adopt* ou en *Hold* — les positions tranchées.
3. Ce qui contredit une pratique répandue.
Ignorer ce qui est purement écosystème cloud/infra sans lien avec la façon de construire.

### Le registre — indispensable

La déduplication ordinaire ne regarde que les **7 derniers digests**. À 2-3 entrées par jour,
cette fenêtre est franchie en trois jours : tout ce qui a été traité il y a plus d'une semaine
redevient invisible et serait réémis. Sur un cycle d'exploitation de plusieurs mois, le registre
est **la seule mémoire réelle** — sans lui, le mécanisme tourne en rond sans jamais signaler
d'erreur.

Le registre vit sur la branche `state`, à côté des archives :

```
routines/daily-tech-digest/radar-ledger.md
```

Protocole, à chaque run :

1. **Lire** `radar-ledger.md` — il liste, par édition, les entrées déjà traitées.
2. **Choisir** 2 à 3 entrées qui n'y figurent pas.
3. **Écrire** le digest normalement.
4. **Après envoi confirmé**, ajouter les entrées traitées au registre et le commiter
   **dans le même commit que le digest du jour**.

Si une édition n'a pas encore de section dans le registre, la créer avec son nom et sa date de
parution.

**Édition épuisée** — toutes les entrées intéressantes traitées : le noter dans le registre et
passer au radar suivant. Ne jamais recycler une entrée pour meubler ; s'il ne reste rien nulle
part, la section 📡 est simplement absente ce jour-là.

**Nouvelle édition** — ouvrir une nouvelle section dans le registre et repartir de zéro dessus.
L'ancienne section reste en place, comme trace. Le jour où une nouvelle édition paraît, l'annoncer
en tant que telle, puis reprendre l'exploitation dès le lendemain.

### Les sources

- **ThoughtWorks Technology Radar** — https://www.thoughtworks.com/radar
  Semestriel. La référence sur techniques / tools / platforms / languages. Le quadrant
  **Techniques** est le plus pertinent ici (agents, harness, RAG).

- **CNCF Technology Landscape Radar** — https://www.cncf.io/reports/cncf-technology-landscape-radar/
  Trimestriel, adossé à un sondage de 300+ développeurs. Couvre l'inference IA, l'orchestration
  ML et les plateformes agentiques.

- **InfoQ Trends Reports** — https://www.infoq.com/infoq-trends-report/
  Annuel, en plusieurs éditions échelonnées dans l'année (AI/ML/Data Engineering,
  Culture & Methods, Cloud/DevOps). Modèle « crossing the chasm ». Surveiller surtout
  l'édition AI/ML.

- **Gartner Hype Cycle for Agentic AI** — https://www.gartner.com/en/articles/hype-cycle-for-agentic-ai
  Annuel. Vue analyste sur la maturité, la gouvernance et les coûts des agents.
  ⚠️ Le rapport complet est payant — la règle « pas de paywall dur » s'applique. S'en tenir aux
  synthèses publiques (article Gartner en accès libre, communiqué de presse, reprises presse) et
  ne jamais lier vers une page qui exige un compte.

- **awesome-generative-ai-guide — RAG research table** —
  https://github.com/aishwaryanr/awesome-generative-ai-guide/blob/main/research_updates/rag_research_table.md
  Mise à jour **continue**, contrairement aux quatre autres : c'est un suivi de papers RAG et
  agentic RAG, pas un rapport. Elle échappe donc à la logique d'exploitation par édition : pas
  d'édition, pas de registre, rien à épuiser. À consulter les jours où le thème IA manque de
  matière, en ne retenant qu'un papier réellement nouveau et marquant. Fetcher l'URL
  `raw.githubusercontent.com` correspondante plutôt que la page GitHub.

### Requêtes de secours

- `ThoughtWorks Technology Radar new volume`
- `CNCF technology radar report`
- `InfoQ trends report AI ML`
- `Gartner hype cycle agentic AI`

---

## Journal d'affinage

Noter ici ce qu'on ajoute ou retire, et pourquoi — pour ne pas réintroduire dans six mois une
source qu'on avait déjà jugée bruyante.

- 2026-08-27 — liste initiale.
- 2026-08-27 — premier run : retrait de `netflixtechblog.com` (403), `highscalability.com`
  (mort depuis 2024) et `discord.com/category/engineering` (pas de dates) ; `openai.com/news`
  passe en WebSearch (403) ; `stripe.com/blog/engineering` remplacé par sa cible de redirection ;
  `thoughtworks.com/radar` sorti du passage quotidien (trimestriel).
- 2026-08-30 — ajout d'une section **Radars & rapports de tendances** (ThoughtWorks, CNCF, InfoQ
  Trends, Gartner Hype Cycle agentic AI, RAG research table). Ces sources sont périodiques et
  incompatibles avec le filtre 48h appliqué tel quel : elles sont donc vérifiées **le lundi
  seulement**, avec le filtre portant sur la date de parution de l'édition. `thoughtworks.com/radar`
  y est déplacé depuis le thème Archi (et corrigé : semestriel, pas trimestriel).
- 2026-08-30 — les radars passent d'un signalement ponctuel à une **exploitation progressive** :
  2-3 entrées par lundi jusqu'à épuisement de l'édition. Nécessite un registre persistant
  (`radar-ledger.md` sur `state`), la déduplication à 7 jours étant aveugle sur un cycle de
  plusieurs mois.
- 2026-08-30 — exploitation des radars **quotidienne** au lieu d'hebdomadaire. Motif chiffré :
  ~100 blips par édition, à 2-3/semaine il faut ~40 semaines soit plus qu'un semestre, l'édition
  suivante sort avant qu'on ait fait le tour. En quotidien : 5-7 semaines par radar, les quatre
  sources tiennent dans l'année. Rend le registre d'autant plus critique — la fenêtre de
  déduplication de 7 jours est désormais franchie en trois jours.
