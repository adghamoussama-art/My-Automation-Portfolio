# ultimate-n8n-ai-workflows
Une collection de workflows n8n avancés intégrant l'Intelligence Artificielle (Gemini) pour l'automatisation de tâches : assistants Telegram intelligents (téléchargement de médias, transcription et traduction de vidéos YouTube) et système automatisé de qualification de leads
n8n Automation & AI Hub
Ce dépôt regroupe trois projets d'automatisation avancés basés sur n8n et l'Intelligence Artificielle. L'espace est organisé en trois dossiers distincts. Chaque dossier contient exactement :
Un fichier explicatif qui détaille le fonctionnement du projet.
Deux images (captures d'écran du workflow).
Une vidéo de démonstration en action.
📁 Présentation des 3 Dossiers
1️⃣ Assistant Telegram Hybride : IA & Téléchargement Médias
Ce workflow gère de manière autonome un bot Telegram. Il utilise une logique conditionnelle pour séparer les messages textuels, traités par l'IA (Google Gemini), des liens de réseaux sociaux (Instagram, TikTok, YouTube) dont il extrait et télécharge automatiquement les vidéos pour les renvoyer à l'utilisateur.
2️⃣ Transcription et Traduction Automatique YouTube
Ce workflow récupère la transcription brute d'une vidéo YouTube à partir de son URL, propose un choix interactif de langue sur Telegram, traduit le texte via Gemini, puis génère un fichier HTML interactif et stylisé avec les repères temporels (timestamps). Attention : si l'entrée n'est pas un lien valide, le flux s'arrête immédiatement dès le deuxième nœud.
3️⃣ Qualification de Leads Automatisée via n8n et IA
Ce projet capture et qualifie automatiquement les prospects selon leur budget (seuil à 5000 dollars). La branche Premium utilise l'IA pour analyser la pertinence de la demande et générer un rapport stratégique par email, tandis que la branche secondaire stocke les données et utilise l'IA pour générer un rapport quotidien épuré destiné au gestionnaire
