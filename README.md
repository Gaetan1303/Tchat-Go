# Tchat-Go
📦 Chat WebSocket Go – README complet
Ce petit projet est un serveur de chat temps-réel écrit en Go.
Il utilise :

    le langage Go 1.20+
    la librairie gorilla/websocket (téléchargée automatiquement)
    une page HTML/JS côté client

# Prérequis
Table
Copy
Outil	Version minimale	Lien / Commande de vérification
Go	1.20	go version
Git	2.x (facultatif mais recommandé)	git --version

    Sous Windows, préférez l’installateur officiel (MSI) :
    https://go.dev/dl/

# Installation de Go
Ubuntu / Debian
bash
Copy

sudo apt update
sudo apt install golang-go
go version

# Cloner / créer le projet
bash
Copy

#  Créer un dossier
mkdir chat-go && cd chat-go

# Initialiser le module Go (nom du module = chat-go)
go mod init chat-go

# Créer le fichier main.go
#    → Copier-coller le contenu fourni plus haut
#    (ou : wget https://raw.githubusercontent.com/votre fork/main.go)

# 4. Créer le dossier qui contiendra la page HTML
mkdir static

5. Télécharger les dépendances
bash
Copy

go mod tidy

    Cette commande :

        analyse les imports de votre code
        télécharge gorilla/websocket dans le cache Go
        génère/maj go.mod et go.sum

6. Lancer le serveur
bash
Copy

go run .

Vous devez voir :
2025/10/17 14:23:45 Serveur démarré sur http://localhost:8080
7. Tester

    Ouvrez plusieurs onglets de votre navigateur sur :
    http://localhost:8080
    Choisissez un pseudo, tapez un message, « Envoyer ».
    Les messages apparaissent instantanément dans tous les onglets.

Route utilitaire :
http://localhost:8080/status
→ renvoie un JSON {connected_users: X, timestamp: "... "}
8. Build & run « en production »
bash
Copy

# Compiler un binaire natif
go build -o chat-server .

# Lancer
./chat-server        # Linux / macOS
chat-server.exe      # Windows

Le binaire est autonome (pas besoin de Go installé sur la machine cible).
9. Arborescence finale
Copy

chat-go/
├─ go.mod
├─ go.sum
├─ main.go
├─ static/
│  └─ index.html
└─ chat-server      (binaire créé par go build)

10. Commandes utiles
Table
Copy
But	Commande
Mettre à jour les dépendances	go get -u ./...
Voir les modules utilisés	go list -m all
Formater le code	go fmt
Linter	go vet
Vider le cache modules	go clean -modcache
11. Problèmes fréquents
Table
Copy
Erreur	Solution
go: command not found	Installer Go (voir §2)
404 / dans le navigateur	Vous avez oublié le dossier static/index.html
websocket: bad handshake	Vérifier l’URL JS : ws://localhost:8080/ws
go mod tidy bloque	Derrière proxy ? go env -w GOPROXY=https://proxy.golang.org,direct