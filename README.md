# claude-routines-telegram

Configuration des [routines Claude Code](https://code.claude.com/docs/en/routines) qui poussent
de l'information dans Telegram.

Chaque routine tourne dans une session cloud Anthropic, sur un cron, et envoie son résultat via
l'API Bot Telegram. Ce repo ne contient **que la configuration** : le prompt de chaque routine vit
côté Anthropic (claude.ai/code/routines), et les secrets vivent dans les variables d'environnement
de l'environnement cloud. Rien de sensible n'est versionné ici.

## Branches

| Branche | Rôle |
|---|---|
| `main`  | la configuration : sources, formats, README. Protégée en écriture. |
| `state` | ce que les agents produisent (archives de digests). Seule branche où ils poussent. |

Un agent lit sa config depuis `main` sans changer de branche
(`git show origin/main:routines/<nom>/sources.md`) et ne bascule sur `state` que pour écrire son
archive. **Pour affiner une routine, on édite `main`** ; c'est pris en compte au run suivant.

## Routines

| Dossier | Quoi | Quand |
|---|---|---|
| [`routines/daily-tech-digest`](routines/daily-tech-digest) | Veille tech quotidienne (IA, archi, system design, dev) | tous les jours, `0 6 * * *` UTC |

## Ajouter une routine

1. Créer `routines/<nom>/` avec un `sources.md` (quoi collecter) et un `format.md` (à quoi
   ressemble le message).
2. Créer la routine avec `/schedule` dans Claude Code, en pointant sur ce repo et sur
   l'environnement cloud `Routines Telegram` (accès réseau `Full`, variables `TELEGRAM_BOT_TOKEN`
   et `TELEGRAM_CHAT_ID`).
3. Lancer la routine une fois à la main pour vérifier avant de laisser le cron s'en charger.
