💬 Tchat-Go : Serveur de Chat Temps-Réel avec Web Socket (Go)

Ce petit projet est un serveur de chat temps-réel minimaliste, écrit en Go, utilisant le protocole Web Socket pour une communication bidirectionnelle instantanée.

Il repose sur :

    Le langage Go (version 1.20+)

    La librairie gorilla/websocket (téléchargée automatiquement)

    Une interface client en HTML/JS pour le navigateur.

🛠️ 1. Prérequis et Installation

Assurez-vous d'avoir les outils suivants installés sur votre système.
Outil	Version minimale	Commande de vérification	Note
Go	1.20	go version	L'installateur officiel (MSI) est recommandé sous Windows.
Git	2.x (facultatif)	git --version	

Installation de Go (Exemple pour Ubuntu / Debian)

Bash

sudo apt update
sudo apt install golang-go
go version

🚀 2. Démarrage Rapide

Suivez ces étapes pour mettre en place et lancer le serveur de chat.

2.1. Créer et Initialiser le Projet

Bash

# Créer le dossier
mkdir chat-go && cd chat-go

# Initialiser le module Go
go mod init chat-go

2.2. Structure des Fichiers

Créez les fichiers et dossiers nécessaires :

    main.go : Copiez-collez votre code source du serveur Go ici.

    static/index.html : Créez le dossier static et placez la page HTML/JS du client à l'intérieur.

Bash

mkdir static
# Créez/collez le contenu de index.html dans ce dossier

2.3. Télécharger les Dépendances

La commande go mod tidy télécharge automatiquement la librairie gorilla/websocket et met à jour les fichiers de module (go.mod et go.sum).
Bash

go mod tidy

2.4. Lancer le Serveur

Exécutez l'application directement avec la commande go run.
Bash

go run .

Si le démarrage est réussi, vous verrez :

2025/10/17 14:23:45 Serveur démarré sur http://localhost:8080

✅ 3. Tester l'Application

3.1. Accéder au Chat

Ouvrez plusieurs onglets de votre navigateur à l'adresse suivante :

➡️ http://localhost:8080

    Choisissez un pseudo, tapez un message, et cliquez sur « Envoyer ».

    Les messages devraient apparaître instantanément dans tous les onglets ouverts, confirmant la connexion Web Socket temps-réel.

3.2. Route de Statut Utilitaires

Vous pouvez vérifier l'état du serveur via cette route :

    URL : http://localhost:8080/status

    Résultat : Renvoie un JSON d'état : {"connected_users": X, "timestamp": "... "}

📦 4. Compilation et Binaire Autonome

Pour déployer le serveur sans avoir Go installé sur la machine cible (mode production), compilez un binaire natif.

4.1. Compiler

Bash

go build -o chat-server .

4.2. Lancer le Binaire

Système	Commande
Linux / macOS	./chat-server
Windows	chat-server.exe

4.3. Arborescence Finale

Le binaire chat-server est créé à la racine du projet.

chat-go/
├─ go.mod
├─ go.sum
├─ main.go
├─ static/
│  └─ index.html
└─ chat-server      # Le binaire exécutable créé par 'go build'

⚙️ 5. Commandes Go Utiles

But	Commande
Mettre à jour les dépendances	go get -u ./...
Voir les modules utilisés	go list -m all
Formater le code Go	go fmt
Linter (vérification statique)	go vet
Vider le cache modules	go clean -modcache

⚠️ 6. Problèmes Fréquents

Erreur	Solution
go: command not found	Installer Go (voir section 1. Prérequis).
Erreur 404 / dans le navigateur	Vérifier que le dossier static/index.html existe et est correctement placé.
websocket: bad handshake	Vérifier que l'URL d'initialisation du WebSocket côté JS est bien ws://localhost:8080/ws.
go mod tidy bloque	Si vous êtes derrière un proxy, configurez la variable : go env -w GOPROXY=https://proxy.golang.org,direct.