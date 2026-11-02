# 🎂 Rappels d’anniversaire avec n8n

Projet réalisé par **Bastian Bellard** dans le cadre de la semaine de cours sur n8n.

L’objectif : ne plus oublier les anniversaires de mes proches. L’automatisation m’envoie un rappel par email avec un message personnalisé, prêt à copier et à adapter avant de l’envoyer moi-même.

## 📂 Accès aux éléments du rendu

| Élément | Lien |
| --- | --- |
| Workflow TypeScript, prompt XML et notes | [Own workflow.workflow.ts](Workflow%20Bastian/Workflow%20format%20ts/Own%20workflow.workflow.ts) |
| Les trois skills | [Skills Bastian](Skills%20Bastian/) |
| Vidéo de démonstration | [Regarder la vidéo sur Loom](https://www.loom.com/share/b8019deac1f448c7b0d6bf09b0cb1acd) |
| Lien vidéo dans le dépôt | [Présentation vidéo](Vid%C3%A9o%20n8n%20Bastian/Vide%CC%81o%20/README.md) |
| Transcript horodaté | [Lire le transcript](Vid%C3%A9o%20n8n%20Bastian/Transcript/transcript.md) |

La vidéo est fournie sous forme de **lien Loom**, et non de fichier vidéo compressé déposé dans le repository.

## 🎯 Le besoin

J’ai tendance à oublier les anniversaires, même lorsque je reçois une notification sur mon calendrier. Ce projet rassemble dans un même email le rappel et une proposition de message, pour faciliter le passage à l’action.

Le projet concerne moins de 20 personnes. Les informations nécessaires sont :

- Le prénom.
- La date d’anniversaire.
- La relation avec la personne.

**Aucun message n’est envoyé automatiquement à mes proches.** Les rappels et les alertes sont destinés uniquement à mon adresse de réception.

## 🛠️ Les outils

| Outil | Rôle |
| --- | --- |
| **n8n** | Exécuter l’automatisation et coordonner les étapes. |
| **Google Sheets** | Conserver la liste des anniversaires. |
| **Google Gemini** | Préparer un message adapté au prénom et à la relation. |
| **Gmail** | M’envoyer les rappels et les alertes. |
| **n8ncli** | Synchroniser et gérer le workflow sous forme de code TypeScript. |

La feuille Google Sheets utilise les colonnes **Prénom**, **Date anniversaire** et **Relation**. Les dates peuvent notamment être renseignées en `JJ/MM` ou `JJ/MM/AAAA`. L’année ne sert pas à calculer l’âge.

## ⚙️ Fonctionnement du workflow

La vérification se déclenche chaque jour à **9 h, heure de Paris**, avec prise en compte de l’heure d’été et de l’heure d’hiver.

### 1. Safe Preview — Vérifier sans envoyer

Cette branche se lance manuellement. Elle lit la feuille, vérifie les contacts et affiche un aperçu avec des exemples de messages de secours.

Elle **n’envoie aucun email**, ne fait **aucun appel à Gemini** et ne modifie pas le journal.

### 2. Exclusive Run — Préparer et protéger le traitement

Cette partie charge les paramètres et le journal persistant des rappels. Elle utilise un verrou pour éviter que deux exécutions traitent la file en même temps.

Le journal conserve les envois réussis et les opérations en attente. Il ne faut pas le vider : il participe à la prévention des doublons.

### 3. Birthday Reminders — Préparer et envoyer les rappels

Cette partie détermine les anniversaires à rappeler et choisit l’action nécessaire :

1. Lire les données de Google Sheets.
2. Générer un message personnalisé avec Gemini.
3. Vérifier les messages déjà envoyés.
4. Envoyer un rappel ou une alerte au propriétaire.
5. Attendre 15 minutes lorsqu’une reprise est nécessaire.
6. Produire un bilan lorsque le traitement est terminé.

Un email distinct est prévu pour chaque anniversaire. Un jour sans anniversaire ni erreur à signaler ne produit aucun email.

## ✨ Le prompt XML et la personnalisation

Le nœud **Generate Birthday Message** contient un prompt structuré en XML. Ses balises séparent :

- Le rôle de l’IA et l’objectif du message.
- Les données d’entrée.
- Les contraintes de longueur et de contenu.
- Le ton à adopter selon la relation.
- Le format de sortie attendu.

Le message doit tenir en **une ou deux phrases**, avec un maximum de **400 caractères**. Il ne doit inventer ni âge, ni souvenir, ni projet, ni autre détail personnel.

| Relation | Ton attendu |
| --- | --- |
| Famille | Chaleureux et affectueux. |
| Ami proche | Complice et chaleureux. |
| Ami | Joyeux et simple. |
| Collègue | Cordial et professionnel. |
| Connaissance | Poli et sobre. |
| Copine : Emma | Complice et drôle, avec une touche de tendresse. |

**Les consignes sont en XML, mais la réponse reste un message en texte normal, prêt à copier.** Les données d’entrée restent un objet JSON contenant uniquement le prénom et la relation.

## 🔒 Confidentialité et cas particuliers

- Gemini reçoit uniquement **le prénom et la relation**, sans date d’anniversaire ni adresse email.
- Les dates manquantes ou invalides sont signalées sans interrompre le traitement des autres contacts.
- Le 29 février est rappelé le 28 février les années non bissextiles.
- Une opération externe en échec peut être reprise après 15 minutes.
- Après deux échecs Gemini, un message de secours prend le relais.
- Un rappel peut être rattrapé jusqu’à la fin du lendemain, avec un message adapté au retard. Au-delà, il expire et une alerte est préparée.
- Le journal et la recherche des emails déjà envoyés évitent de renvoyer un rappel réussi.
- Si le résultat d’un envoi Gmail est incertain, le workflow cherche sa trace et signale l’incertitude au lieu de renvoyer aveuglément.

Une indisponibilité complète de n8n empêche également l’exécution des reprises tant que l’instance n’est pas rétablie.

## 🧩 Les trois skills du rendu

Les skills décrivent une démarche pour cadrer, construire et examiner un projet. Ils servent à guider le travail de l’assistant, indépendamment des nœuds exécutés par n8n.

| Skill | Petite note explicative |
| --- | --- |
| [Interview-projet](Skills%20Bastian/Interview-projet/SKILL.md) | Clarifier l’idée par des questions progressives et formaliser un cahier des charges avec les objectifs, les contraintes et les critères de réussite. |
| [Doubt-driven-dev](Skills%20Bastian/Doupt-driven-dev/SKILL.md) | Identifier les hypothèses risquées et chercher des preuves concrètes avant de considérer une solution comme fiable. |
| [Hostile-review](Skills%20Bastian/Hostil-review/SKILL.md) | Examiner le projet de manière critique pour repérer les failles importantes et les écarts avec les exigences. |

Les noms des dossiers existants ont été conservés dans les liens.

## 💻 Commandes présentées dans la vidéo

La démonstration utilise **n8ncli 1.2.45**, installé localement sur mon ordinateur. Depuis le dossier de cette installation :

```bash
./n8ncli --help
./n8ncli --version
./n8ncli changelog
```

| Commande | Explication |
| --- | --- |
| `--help` | Affiche l’aide et les commandes disponibles. |
| `--version` | Affiche la version installée. |
| `changelog` | Présente les nouveautés et les corrections des versions. |

Ces commandes consultent des informations et ne modifient pas le workflow.

## ✅ Vérifications réalisées pendant le projet

- Lecture réelle des trois contacts de la feuille.
- Exécution sans anniversaire : aucun rappel envoyé.
- Génération réelle avec Gemini et envoi d’emails clairement marqués **TEST**, notamment pour Papa.
- Test de Papa après passage du prompt en XML.
- Relance d’un test identique sans deuxième email ni nouvel appel Gemini.
- Validation du fichier TypeScript par n8ncli.
- Tests locaux de la logique : dates invalides, années bissextiles, fuseau Paris, plusieurs anniversaires, reprises, secours et expiration.

Les scénarios d’erreur ont été simulés dans les tests de la logique. Ils ne constituent pas une interruption réelle des services Google pendant 15 minutes.

## 📦 Réutilisation et budget

Le fichier `.workflow.ts` est un export pour l’écosystème **n8ncli / n8n Workflow SDK**. Il nécessite une instance n8n configurée, les connexions Google Sheets, Gmail et Gemini, ainsi que la table persistante **Birthday Reminder State**.

Pour une autre instance, il faut recréer ou reconnecter ces ressources et adapter leurs références. Les secrets d’authentification ne sont pas inclus dans l’export.

L’objectif initial était de rester à **0 €**. La clé Gemini a été déclarée en offre gratuite sans facturation. **n8n Cloud a été utilisé dans le cadre d’un essai temporaire** : la gratuité durable du projet n’est donc pas acquise. Aucun abonnement payant n’a été souscrit dans le cadre de la réalisation.

## 🎥 Présentation et retour d’expérience

La vidéo présente le dépôt GitHub, le besoin personnel, les trois parties du workflow, un exemple d’email reçu, les commandes du terminal et mon retour sur la semaine de cours.

J’ai apprécié de découvrir n8n et de construire une automatisation concrète, avec l’aide de l’IA. Le rythme du cours et le nombre de participants rendaient parfois les questions difficiles à poser, mais l’entraide entre camarades m’a permis de comprendre les notions qui me manquaient.

Merci à Lucas pour la semaine de cours, les échanges et le moment partagé autour du goûter.
