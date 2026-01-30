# 🇫🇷 reMarkable Paper Pro - Traduction française

Ce dépôt fournit une **traduction française de l’interface utilisateur des tablettes reMarkable** à l’aide des fichiers de traduction Qt (`.qm`).

## ⚠️ Avertissement

reMarkable **ne propose pas officiellement le français** comme langue système.

Cette traduction fonctionne en **remplaçant la langue allemande** :

Fichier concerné :
- `reMarkable_de.qm`

Le système pense utiliser l’allemand, mais affiche en réalité le français.

## 📁 Contenu du dépôt

- **`reMarkable_de_original.qm`**
- **`reMarkable_de.qm`**
  → Fichier de traduction **française**  
  → ⚠️ Doit **remplacer** le fichier `reMarkable_de.qm` original

Aucun autre fichier n’est requis.

## 🛠️ Installation

⚠️ La tablette doit impérativement rester allumée pendant toute la durée de la manipulation.

### 1️⃣ Activer le mode développeur

Sur la tablette :
- Settings → Software → Advanced → Developer mode
- Redémarrer la tablette

### 2️⃣ Connexion SSH à la tablette et passage en écriture

Depuis votre ordinateur, ouvrez [PuTTY](https://putty.org/index.html):

Sur la tablette :
- Allez dans **Settings → Help → Copyrights and licenses**
- En bas de la page se trouve l’adresse IP : **10.11.99.1**
- Utilisez le **port 22**
- Dans la section **GPLv3 Compliance**, se trouve votre **mot de passe SSH**

Dans PuTTY :
- Host Name (or IP address) : **10.11.99.1**
- Port : **22**
- Connection type : **SSH**
- Cliquez sur **Open**

Une fenêtre noire s’ouvre :
- `login as:` **root**
- `root@10.11.99.1's password:` **votre mot de passe**
  - ⚠️ Le mot de passe **ne s’affiche pas pendant la saisie**, c’est normal
  
Une fois connecté, vous êtes en **SSH sur la tablette**

Passer la tablette en écriture (read-only → read-write) :

Par défaut, le système de la reMarkable est en **lecture seule**.  
Pour remplacer le fichier de traduction, il faut remonter la partition système en écriture.

- Copier :
`   mount -o remount,rw /
    mount -o remount,rw /usr`
- Coller dans la fenêtre PuTTY (clique droit)

Une fois ces commandes exécutées, le système n’est plus en lecture seule et les fichiers système peuvent être modifiés.

### 3️⃣ Remplacement du fichier "reMarkable_de.qm"

Depuis votre ordinateur, ouvrez [WinSCP](winscp.net/eng/download.php):

Dans WinSCP :
- Protocole de fichier : **SCP**
- Nom d'hôte : **10.11.99.1**
- Numéro de port : **22**
- Nom d'utilisateur : **root**
- Mot de passe : **votre mot de passe**
  - ⚠️ Il s'agit du même que pour PuTTY
 
Après la session lancé :
- A gauche les dossiers de votre PC et à droite ceux de la tablette
- Vous êtes dans **/home/root/**
- Allez dans **/usr/share/remarkable/xochitl/translations/**
- Remplacez le fichier `reMarkable_de.qm` original par **celui du dépôt**
  - 💡 Astuce : ouvrez l’Explorateur de fichiers de votre PC et glissez-déposez simplement le fichier téléchargé dans la fenêtre WinSCP
- Redémarrez votre tablette

### 4️⃣ Changer la langue

Sur la tablette :
- Allez dans **Settings → General → Language and keyboard → System language**
- Sélectionnez **Deutsch**

### 🎉 Et voilà : votre reMarkable est désormais en français !

Afin de rétablir le fichier d'origine, il suffit de suivre les mêmes instructions mais en renommant le fichier `reMarkable_de_original.qm` en `reMarkable_de.qm` dans le dossier **translations**.
