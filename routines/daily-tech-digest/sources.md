# daily-tech-digest — sources

Fichier de référence de la routine. **C'est lui qui fait foi**, pas le prompt : pour changer ce qui
est collecté, on édite ce fichier sur `main`.

Stratégie **hybride** : on passe d'abord sur les sources fixes de chaque thème, puis on comble avec
WebSearch les thèmes restés vides ou trop maigres.

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

`thoughtworks.com/radar` est trimestriel (Vol 34 = avril 2026). Inutile de le fetcher chaque
jour : ne le consulter qu'en début de trimestre.

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

## Journal d'affinage

Noter ici ce qu'on ajoute ou retire, et pourquoi — pour ne pas réintroduire dans six mois une
source qu'on avait déjà jugée bruyante.

- 2026-08-27 — liste initiale.
- 2026-08-27 — premier run : retrait de `netflixtechblog.com` (403), `highscalability.com`
  (mort depuis 2024) et `discord.com/category/engineering` (pas de dates) ; `openai.com/news`
  passe en WebSearch (403) ; `stripe.com/blog/engineering` remplacé par sa cible de redirection ;
  `thoughtworks.com/radar` sorti du passage quotidien (trimestriel).
