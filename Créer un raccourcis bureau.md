# Comment créer un raccourci vers un script PowerShell sur le bureau Windows

🇬🇧 [English version](README.md)

### PowerShell 7 et Windows PowerShell 5.1

## 1. PowerShell 7 ou Windows PowerShell 5.1 ?

Windows dispose nativement de **Windows PowerShell 5.1**.  
**PowerShell 7** est une version plus récente qui doit être installée séparément.

Les deux versions peuvent exécuter des scripts `.ps1`, mais elles utilisent des exécutables différents.

### PowerShell 7
**Version moderne**

Exécutable :

```text
pwsh.exe
```

PowerShell 7 doit être installé séparément. C'est une version plus récente et multiplateforme.

### Windows PowerShell 5.1
**Version intégrée à Windows**

Exécutable :

```text
powershell.exe
```

Cette version est normalement disponible directement dans Windows et ne nécessite pas d'installation supplémentaire.

---

# 2. Vérifier la version de PowerShell utilisée

Ouvrez PowerShell ou Windows Terminal et exécutez :

```powershell
$PSVersionTable.PSVersion
```

Si le numéro de version principale (`Major`) est **7**, vous utilisez PowerShell 7.

Si le numéro de version principale est **5**, vous utilisez Windows PowerShell 5.1.

---

# 3. Créer le raccourci sur le bureau

La procédure est la même pour les deux versions.

### Étape 1

Faites un clic droit sur le bureau.

Sélectionnez :

**Nouveau → Raccourci**

### Étape 2

Dans le champ :

**Entrez l'emplacement de l'élément**

entrez la commande correspondant à la version de PowerShell que vous souhaitez utiliser.

### Étape 3

Cliquez sur **Suivant**.

### Étape 4

Donnez un nom au raccourci.

Par exemple :

```text
Lancer mon script PowerShell
```

Cliquez ensuite sur **Terminer**.

Vous pouvez maintenant double-cliquer sur le raccourci pour exécuter votre script.

---

# 4. Raccourci pour PowerShell 7

Si PowerShell 7 est installé, utilisez :

```text
pwsh.exe -NoProfile -ExecutionPolicy Bypass -File "C:\Scripts\MonScript.ps1"
```

### Signification des commandes

| Commande | Description |
|---|---|
| `pwsh.exe` | Lance PowerShell 7. |
| `-NoProfile` | Empêche PowerShell de charger le profil de l'utilisateur. |
| `-ExecutionPolicy Bypass` | Contourne les restrictions de stratégie d'exécution pour ce processus. |
| `-File` | Indique à PowerShell qu'il doit exécuter un fichier de script. |
| `"C:\Scripts\MonScript.ps1"` | Chemin vers le script PowerShell à exécuter. |

---

# 5. Raccourci pour Windows PowerShell 5.1

Si vous utilisez uniquement la version native de Windows, utilisez :

```text
powershell.exe -NoProfile -ExecutionPolicy Bypass -File "C:\Scripts\MonScript.ps1"
```

### Signification des commandes

| Commande | Description |
|---|---|
| `powershell.exe` | Lance Windows PowerShell 5.1. |
| `-NoProfile` | Empêche PowerShell de charger le profil de l'utilisateur. |
| `-ExecutionPolicy Bypass` | Contourne les restrictions de stratégie d'exécution pour ce processus. |
| `-File` | Indique à PowerShell qu'il doit exécuter un fichier de script. |
| `"C:\Scripts\MonScript.ps1"` | Chemin vers le script PowerShell à exécuter. |

### La différence essentielle

Les deux commandes sont quasiment identiques.

La principale différence est l'exécutable utilisé :

```text
pwsh.exe
```

pour **PowerShell 7**

et :

```text
powershell.exe
```

pour **Windows PowerShell 5.1**.

Les paramètres `-NoProfile`, `-ExecutionPolicy Bypass` et `-File` peuvent être utilisés avec les deux versions.

---

# 6. Garder la fenêtre PowerShell ouverte

Par défaut, la fenêtre PowerShell peut se fermer lorsque le script a terminé son exécution.

Si vous souhaitez conserver la fenêtre ouverte, ajoutez :

```text
-NoExit
```

### PowerShell 7

```text
pwsh.exe -NoProfile -ExecutionPolicy Bypass -NoExit -File "C:\Scripts\MonScript.ps1"
```

### Windows PowerShell 5.1

```text
powershell.exe -NoProfile -ExecutionPolicy Bypass -NoExit -File "C:\Scripts\MonScript.ps1"
```

`-NoExit` demande à PowerShell de rester ouvert après l'exécution du script.

Cela peut être particulièrement utile pour voir les messages affichés par le script ou les éventuelles erreurs.

---

# 7. Définir le dossier de travail

Dans les propriétés du raccourci, vous pouvez également renseigner le champ **Démarrer dans**.

Par exemple :

```text
C:\Scripts
```

Cela permet de définir le répertoire de travail utilisé par le script.

C'est notamment utile lorsque le script utilise des chemins relatifs, par exemple :

```powershell
.\data.txt
```

---

# 8. Exemple complet

Supposons que votre script se trouve ici :

```text
C:\Users\Jean\Desktop\Scripts\Backup.ps1
```

### Avec PowerShell 7

```text
pwsh.exe -NoProfile -ExecutionPolicy Bypass -File "C:\Users\Jean\Desktop\Scripts\Backup.ps1"
```

### Avec Windows PowerShell 5.1

```text
powershell.exe -NoProfile -ExecutionPolicy Bypass -File "C:\Users\Jean\Desktop\Scripts\Backup.ps1"
```

Vous pouvez alors placer ce raccourci sur le bureau et simplement **double-cliquer dessus pour lancer le script**.

---

# 9. À propos de `-ExecutionPolicy Bypass`

L'option :

```text
-ExecutionPolicy Bypass
```

demande à PowerShell de ne pas appliquer les restrictions de stratégie d'exécution pour le processus lancé par cette commande.

Elle **ne modifie pas définitivement** la stratégie d'exécution de Windows ou de PowerShell.

Il est néanmoins recommandé de l'utiliser uniquement avec des scripts auxquels vous faites confiance.

---

# Résumé

Pour **PowerShell 7** :

```text
pwsh.exe -NoProfile -ExecutionPolicy Bypass -File "CHEMIN_DU_SCRIPT.ps1"
```

Pour **Windows PowerShell 5.1** :

```text
powershell.exe -NoProfile -ExecutionPolicy Bypass -File "CHEMIN_DU_SCRIPT.ps1"
```

La différence principale est donc :

**PowerShell 7 → `pwsh.exe`**

**Windows PowerShell 5.1 → `powershell.exe`**