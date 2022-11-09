# Commandes Git

Ci-dessous se trouve une série de commandes utiles pour travailler avec Git. Ces commandes sont à taper dans un terminal.

- Sur Mac le terminal se trouve dans le dossier Applications/Utilities/Terminal
- Sur Pc vous devez installer l'application "Git bash" (https://gitforwindows.org/) et lancer l'application.

Les commandes peuvent aussi être mobilisées via Visual Studio Code.

## Notes préliminaires 🗒

Dans les commandes qui suivent, il y a des mentions entre crochets [  ]. Ces crochets signifient que vous devez fournir une information à cet emplacement de la commande, par exemple :

-	git branch [le nom de la nouvelle branche]

Signifie qu’il faut inscrire dans le terminal, à la place des crochets le nom de la branche que vous souhaitez créer, par exemple :

```bash
git branch transcription_branche
```

A noter qu’il ne faut pas mettre d’accents, de majuscules ou d’espaces lorsque vous fournissez le nom d’une branche.

# Commandes

1. **Git clone [lien vers le dossier distant framagit]**

    Git est avant tout un système qui permet de conserver une version d'un projet dans un dossier distant et de partager ce dossier avec d'autres membres de votre équipe.

    Pour accéder à ces dossiers, il faut, pour commencer, obtenir le lien qui pointe vers le dossier. Dans le cas du projet enlac, ce lien se trouve sur Framagit. Voici comment l'obtenir :

    1. Rendez vous sur la page : https://framagit.org/rerouj/vitae-prophetarum
    2. Cliquez sur le bouton **clone**
    Copiez le lien **ssh** dans la fenêtre contextuelle qui apparaît
    
        <img src="./images/vscode-clone.png" width="85%" height="85%" text-align="left" />
    
    3. Rendez-vous sur votre finder (explorateur de fichier sur pc). Choisissez un emplacement sur votre ordinateur et créez un dossier.
    4. Faites clic droit sur ce dossier et dans le menu déroulant, choissez *service -> nouveau Terminal*
    5. Si vous préférez utiliser le terminal, vous pouvez taper la commande suivante:
        ```bash
        # dossier racine sur mac = ~/
        cd ~/[mon_dossier_préféré]
        ```
    6. Depuis Windows, choisissez un dossier de destination, puis faîtes clic droit dans le dossier ouvert et sélectionnez dans le menu déroulant **ouvrir une fenêtre powershell ici** 
    7. Une fois que vous avez choisi un dossier de destination et ouvert le terminal au bon endroit, tapez la commande suivante :
        ```bash
        git clone git@framagit.org:rerouj/vitae-prophetarum.git
        ```
    8. Si tout s'est bien passé, le nouveau dossier est présent dans le dossier de destination. Pour le vérifier tapez dans le terminal:
        ```bash
        ls
        ```
    9. entrez dans le dossier avec la commande.

        ```bash
        cd vitae-prophetarum
        ```

    **Note** : Toutes les commandes Git doivent être executées à la racine du dossier que vous venez de télécharger.

2. **git branch [nom de la nouvelle branche]**

    Permet de créer une nouvelle branche.

    example : 
    ```bash
    git branch transcription_anonyme1_mss1
    ```

    **Sur vscode :**
    1. Ouvrez l'éditeur vscode.
    2. Placez-vous sur la branche qui sera la branche mère de la nouvelle branche.
    3. Cliquez sur l'onglet "contrôle de code source" (controle source).

        <img src="./images/vscode-git.png" width="60%" height="60%" text-align="left" />
    4. Dans la fenêtre contextuelle, cliquez sur les trois petits points (...) en haut à droite et choisissez *branche -> créer branche*.

        <img src="./images/vscode-branch.png" width="85%" height="85%" text-align="left" />

    5. Une lacune va apparaître en haut de vscode. Indiquez un nom de branche dans cette lacune, tapez "enter".
        
        <img src="./images/vscode-branchname.png" width="85%" height="85%" text-align="left" />

3. **git checkout [nom d’une branche]**

    Permet de basculer sur une branche.
    
    **exemple :** 
    ```bash 
    git checkout transcription_anonyme1_mss
    ```

    **sur vscode :**

    1. Sur vs code, les branches se trouvent dans la barre de status en bas à gauche de l'éditeur. Pour faire appraître la liste cliquez sur le nom qui apparaît dans la barre.

    2. La liste des branches appraît en haut de l'éditeur. Là vous pouvez choisir la branche sur laquelle vous souhaitez basculer.

        <img src="./images/vscode-checkout.png" width="85%" height="85%" text-align="left" />

4. **git push -u origin [nom de la branche]**

    Permet de pousser le branche et les commits qui s'y trouvent dans un dossier distant. 

    Les branches peuvent être créées et utilisées librement en local (sur votre ordinateur). Elle permettent de faire des modifications sans menacer l'état d'un fichier qui serait à vos yeux satisfaisant. Mais les branches peuvent aussi être partagées. Cela peut arriver lorsqu'il est néecessaire de travailler en commun sur une branche. 
    
    Prenons un exemple, admettons que je crée une branche de révision nommée **revision_manuscrit_a** et que je souhaite partager cette branche avec d'autres philologues afin qu'il puissent proposer eux aussi des révisions sur ce manuscrit ; lorsque la branche est créé, je peux pousser cette branche avec la commande suivante :

    ```bash
    git push -u origin revision_manuscrit_a
    ```

    Si vous sous rendez sur Framagit, après avoir effectué ce type de commandes, et parcourez les branches qui se trouvent dans votre projet, vous trouverez la nouvelle branche. Cette branche les autres utilisateurs peuvent l'obtenir grâce à la commande suivante :

    ```bash
    git fetch
    ```

    Enfin, pour travailler sur cette branche, ils devront faire un **git checkout**.

    **Sur vscode :**
    
    1. Cliquez sur l'onglet "contrôle de code source" (controle source) tout à gauche de l'éditeur.
    2. Si vous venez de créer la branche, un bouton bleu labelisé **"publier"** apparaît dans la colonne de gauche. Cliquez sur ce bouton. La branche est publiée dans le dossier Framagit.

    </br>Si le bouton n'apparaît pas, c'est que des changements ont été détecté dans les fichiers qui se trouvent dans le dossier. Vous devez donc d'abord enregistrer les changements avec les commandes **git add** et **git commit**, voir ci-dessous.


5. **git add .**

    Permet d'indexer les derniers changements (staging). L'indexation est l'étape préalable à l'enregistrement (commit).

    **exemple :**

    ```bash
    git add .
    ```

    A noter que le point (.) signifie que vous souhaitez verser l'ensemble du contenu du dossier. Si vous souhaitez un niveau de détail plus fin, vous pouvez indiquer un nom de fichier comme ceci :

    ```bash
    git add /dossier_x/fichier_x.xml
    ```
    **Sur vscode**

    1. Pour indexer des modifications sur vscode, il faut basculer sur l'onglet "contrôle de code source" (source control).
    2. Dans la colonne de gauche apparaissent vos fichiers sous la rubrique "changements" (changes).
    3. Vous pouvez indexer les changements en passant votre souris au-dessus du fichier que vous souhaitez ajouter et en cliquant sur le petit symbole + qui apparaît à côté du fichier, le fichier va alors basculer dans la rubrique "changements indexés".

        <img src="./images/vscode-add.png" width="50%" height="50%" text-align="left" />
    </br>
6. **git commit -m [votre message entre guillemets]**
	
    Permet d’enregistrer les changements dans l’historique des versions (commit) avec un court message d’explication. 
    
    Un commit décrit l'état d'un fichier avec ses modifications à un temps T. Tous les commits sont enregistrés dans un historique de modifications : les branches ; ils sont tous datés et attribués à un auteur.

    exemple : 
    ```bash
    git commit -m « révision paragraphe 1 »
    ```

    A noter que tous les commits doivent être accompagnés d'un message (option -m). Le message de commit décrit le changement apporté à un fichier.

    **Sur vscode**

    1. Pour commiter un changement sur vscode, vous devez cliquer sur l'icone "contrôle de code source" (source control).
    2. Dans la colonne de gauche, sous la rubrique "changements indexés" apparaissent les fichiers prêts à être commité.
    3. Pour commiter, insérer un message de commit dans le champ "message" au-dessus du bouton "validation" (validate).
    4. Cliquer sur le bouton bleu "validation".
    
        <img src="./images/vscode-commit.png" width="50%" height="50%" text-align="left" />

    </br>S'il n'y a rien dans la rubrique changements indexés, il faut ajouter vos changements avec la commande "add", ***cf. commande 3***

    Lorsque vous avez fait un commit, il est possible de le retrouver via le terminal avec la commande **git log**

    ```bash
    git log
    ``` 

    ou alors

    ```bash
    git log --graph
    ```

7. **git merge [la branche que vous souhaitez merger]**
    
    <span style="color:orange">**⚠️ Warning ⚠️ :** Cette manipulation est délicate. A utiliser avec modération !</span>

    La commande **"merge"** permet de réconcilier des branches qui divergent. *Une divergence entre les branches sous-entend une divergence entre les versions d'un même fichier.* 
    
    Pour merger, il faut toujours se placer sur la branche qui va accueillir la réconciliation et appliquer la commande en indiquant la branche que vous souhaitez merger. 
    
    Prenons un exemple : Vous travaillez sur un fichier de transcription. Vous avez terminé vos révisions sur une branche **"revis_a"**. Entre temps, des éléments ont été ajouté par une autre personne sur le fichier de transcription mais sur une branche **"trans_a"**. Il y a donc une divergence entre les deux versions du fichier de transcription. La situation est la suivante :
    
    <img src="./images/vscode-merge_start.png" width="85%" height="85%" text-align="left" />
    
    Pour poursuivre le travail de révision sur un texte à jour, vous devez rafraîchir la branche **"revis_a"** en *rapatriant*, en quelque sorte, les dernières modifications qui se trouvent sur la branche **"trans_a"**.

    A ce moment, vous devez procéder de la manière suivante :

    **étape 1 :** checkout sur la branche d'accueil

    ```bash
    git checkout revis_a
    ```
    
    **étape 2 :** Réconciliation (merge) de la branche qui a divergé

    ```bash
    git merge trans_a
    ```

    Cette opération aboutit à l'ajout de tous les commits de la branche **"trans_a"** sur la branche **"revis_a"** :

    <img src="./images/vscode-merge_stop.png" width="85%" height="85%" text-align="left" />

    A présent, la branche **revis_a** et **trans_a** ont une histoire commune (qui est matérialisée dans le commit c7) : vous travaillez sur une version à jour de votre fichier de transcription.

    **Sur vscode**

    1. Pour merger sur vscode vous devez cliquer sur l'onglet "contrôle de code source" (source controle) tout à gauche de l'éditeur de text.
    2. Cliquez sur les trois points qui apparaissent en haut à droite du menu contextuel
    3. Dans le menu déroulant, choisissez *branche -> fusionner branche*

    4. Une lacune va apparaître en haut de l'éditeur. Indiquez le nom de la branche à fusionner dans cette lacune.

        <img src="./images/vscode-merge.png" width="75%" height="75%" text-align="left" />

    
    </br>S'il n'y a pas eu de conflits, la branche sur laquelle vous vous trouvez comporte les dernières modifications apportées sur la branche que vous venez de fusionner.
    
    <img src="./images/vscode-merge_select_branch.png" width="75%" height="75%" text-align="left" />
