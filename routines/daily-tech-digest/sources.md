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

### Règles propres à cette section

- **Ne pas les fetcher tous les jours.** Elles ne bougent que quelques fois par an ; les
  interroger quotidiennement ne produirait que du « rien de neuf » et gaspillerait le run.
  → **Les vérifier le lundi uniquement** (jour UTC du run).
- **Le filtre 48h porte sur la parution de l'édition, pas sur son contenu.** Un radar publié
  avant-hier est éligible même si le fond couvre les douze derniers mois.
- **Une édition déjà signalée ne repasse jamais** : vérifier les `digests/` avant d'inclure.
  Un radar publié une fois est mentionné une fois.
- **Quand une nouvelle édition paraît, elle prime** : elle vaut mieux qu'un article quelconque
  du jour, et peut occuper deux items du digest si le contenu le justifie.
- **Angle de lecture** : ce qui est passé en *Adopt* ou en *Hold*, et ce qui touche
  agents / harness / RAG / orchestration. Pas le catalogue complet.
- **Rien de neuf le lundi = section muette.** Ne jamais republier une édition ancienne pour
  meubler.

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
  agentic RAG, pas un rapport. Exception à la règle du lundi — peut être consulté n'importe quel
  jour où le thème IA manque de matière. Fetcher l'URL `raw.githubusercontent.com` correspondante
  plutôt que la page GitHub, et ne retenir qu'un papier réellement nouveau et marquant.

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
