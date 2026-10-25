# Apex Sprint, la vraie plateforme (version de test)

Ici, il y a de vrais comptes : l'athlète et le coach se connectent chacun sur leur téléphone, et les données sont enregistrées en ligne.

## Ce que tu dois créer (gratuit)
1. Un compte sur **supabase.com**, puis un nouveau projet. Note le mot de passe de la base.
2. Un dépôt sur **github.com** et un **Static Site** sur **render.com** (voir l'étape 4).

## Étapes
1. Dans Supabase : menu **SQL Editor**, nouvelle requête. Colle tout le contenu de `schema.sql`, puis clique sur **Run**. Il ne doit y avoir aucune erreur.
2. Dans Supabase : **Authentication**, **Providers**, **Email**. Désactive « Confirm email » pour tes essais (sinon chaque compte demande un e-mail de confirmation).
3. Dans Supabase : **Project Settings**, **API**. Copie « Project URL » et la clé « anon public ».
4. GitHub : crée un dépôt, dépose `index.html`, `render.yaml` et `README.md` à la racine. Render : **New**, **Static Site**, choisis le dépôt, Build Command vide, Publish Directory `.`.
5. Ouvre le lien Render. Au premier lancement, colle l'URL et la clé de l'étape 3.
6. Crée un compte **Coach** (menu « Créer un compte »). Son code apparaît dans « Ton équipe ».
7. Sur un autre appareil (ou une fenêtre privée), crée un compte **Athlète**, choisis « J'ai un coach » et saisis le code.

## Parcours à tester
- Coach : ouvre l'athlète, écris son programme, choisis ses exercices mentaux, envoie. Écris-lui un message. Ajoute une note privée.
- Athlète : reçois le programme, fais l'état du matin, ouvre la séance, valide-la, coche ce qui était prévu (fait, en partie, pas fait), réponds aux 5 questions, enregistre. Écris au coach.
- Coach : vérifie que tu vois le bilan et « Ce qui a été fait ».
- Sécurité : l'athlète ne doit jamais voir la note privée du coach (vérifie dans Supabase, table `coach_notes` : seul le coach y a accès).

## Le paiement (facultatif, plus tard)
Voir `create-checkout.ts` et `stripe-webhook.ts`. Il faut un compte Stripe et les deux fonctions déployées dans Supabase. Les identifiants de prix se collent dans l'écran de configuration (menu « Paiement »). Pour l'instant, l'abonnement n'est pas obligatoire : tout fonctionne sans.

## Ce qui n'est pas fait ou pas testé
- Le code a été testé sur une base simulée, jamais sur un vrai Supabase ni un vrai paiement. Attends-toi à des erreurs à corriger au premier essai.
- Les messages se rafraîchissent toutes les 7 secondes (pas de notification).
- Les voix enregistrées ne sont pas branchées : l'application utilise la voix du téléphone.
- Il faut faire valider les programmes par un entraîneur diplômé et les textes légaux par un juriste avant toute vraie utilisation.
