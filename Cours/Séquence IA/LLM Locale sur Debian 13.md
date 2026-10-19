### Guide d'installation d'une instance LLM locale sur Debian 13

Ce guide détaille la méthode la plus rapide et efficace pour faire tourner un grand modèle de langage (LLM) en local sur **Debian 13 (Trixie)** en utilisant **Ollama**.

---

#### Étape 1 : Mettre à jour le système

Ouvrez votre terminal et assurez-vous que votre système est parfaitement à jour :

```bash
sudo apt update && sudo apt upgrade -y
```
```
**Note** : se logger en Root permet de ne pas inscrire le sudo
```
---

#### Étape 2 : Installer Ollama

Ollama automatise la gestion et l'exécution des LLM. Installez-le à l'aide du script officiel :

```bash
curl -fsSL https://ollama.com/install.sh | sh
```

> **Note :** Si la commande `curl` n'est pas installée sur votre machine, exécutez d'abord `sudo apt install curl -y`.

---

#### Étape 3 : Télécharger et lancer un modèle léger

Pour une configuration standard (8 Go à 16 Go de RAM), les modèles de taille réduite offrent un excellent compromis entre vitesse et pertinence.

Exécutez la commande suivante pour télécharger et lancer **Llama 3.2 (3B)** :

```bash
ollama run llama3.2
```

##### Alternatives recommandées :
* **Très léger (PC modestes) :** `ollama run qwen2.5:1.5b`
* **Performant (Code & Logique) :** `ollama run phi3`

Une fois le téléchargement terminé, une invite de commande `>>>` apparaît. Vous pouvez directement chatter avec l'IA. Pour quitter, tapez `/bye`.

---

#### Étape 4 : (Optionnel) Installer une interface Web (Style ChatGPT)

Pour éviter d'utiliser le terminal à chaque fois, vous pouvez déployer **Open WebUI** via Docker.

##### 1. Installer Docker
```bash
sudo apt install docker.io -y
sudo systemctl enable --now docker
```

##### 2. Lancer le conteneur Open WebUI
Cette commande télécharge et configure l'interface Web en la connectant automatiquement à votre instance Ollama locale :

```bash
docker run -d -p 3000:8080 --add-host=host.docker.internal:host-gateway -v open-webui:/app/backend/data --name open-webui --restart always ghcr.io/open-webui/open-webui:main
```

##### 3. Accéder à l'interface
Ouvrez votre navigateur web et rendez-vous à l'adresse suivante :
👉 [http://localhost:3000](http://localhost:3000)
```
Note : parfois, le localhost ne prend pas. Dans ce cas, employer http://*@ip*:3000/
```

*La première connexion nécessitera la création d'un compte administrateur local (vos données restent stockées sur votre machine).*