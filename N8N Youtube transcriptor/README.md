Description du Workflow : Automatisation de Transcription et Formatage HTML
Ce workflow automatise le processus de récupération, de traduction, de formatage et d'envoi de transcriptions de vidéos YouTube sous forme de fichier HTML interactif via un bot Telegram.
1. Réception et Extraction de l'ID YouTube
Le cycle commence lorsque l'utilisateur envoie un lien YouTube au bot Telegram personnalisé (Trigger Node). Le nœud suivant extrait et isole uniquement l'ID de la vidéo à partir de l'URL reçue pour préparer l'étape de requêtage.
⚠️ Remarque : Si l'entrée fournie par l'utilisateur n'est pas un lien valide, le processus d'automatisation s'arrête immédiatement dès le deuxième nœud.
2. Récupération et Nettoyage de la Transcription
Une fois l'ID obtenu, un nœud dédié récupère la transcription brute de la vidéo. Ensuite, un autre nœud intervient pour nettoyer et restructurer le texte afin de le rendre parfaitement lisible et compréhensible.
3. Sélection de la Langue (Interaction Bot)
Le bot Telegram envoie un message interactif à l'utilisateur, lui demandant de choisir la langue de traduction souhaitée.
4. Routage Conditionnel (Code Switch)
Les données passent ensuite par un nœud de code qui agit comme un switch selon le choix de l'utilisateur :
1 : Anglais
2 : Espagnol
3 : Français
(Et ainsi de suite pour les autres options)
5. Génération et Traduction via l'IA
La langue sélectionnée est injectée dynamiquement dans le prompt envoyé à Gemini. Pour optimiser les performances du modèle et éviter les erreurs de surcharge, Gemini se concentre uniquement sur la traduction et la structuration du texte.
6. Formatage HTML/JS Avancé
Pour alléger la charge de Gemini, un nœud distinct prend le relais pour générer le code HTML et JavaScript. Ce code applique un design soigné et intègre un script JS pour assurer une transition fluide d'une ligne à l'autre, tout en respectant scrupuleusement le timestamp (le repère temporel) de chaque phrase.
7. Conversion en Fichier et Envoi
Enfin, les données textuelles et le code sont convertis en données brutes (data), puis transformés en un véritable fichier .html. Le dernier nœud du workflow se charge d'envoyer ce fichier directement à l'utilisateur sur Telegram.
Résumé technique des étapes :
Telegram Input ➔ ID Extraction & Validation ➔ Transcript Fetch ➔ Text Formatting ➔ Language Selection ➔ Switch Code ➔ Gemini Translation ➔ HTML/JS Generator ➔ Data Conversion ➔ HTML File Creation ➔