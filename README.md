# Martyre de Philippe

Ici une brève introduction du git.

# Nouvelle version :
Ici les principaux et récents changements

# Stratégie de ramification (branching strategy) :

## Résumé :

id | Branche (nomenclature) | Exemple | Usage
--- | ----------- | ----------- | -----------
1|[accronyme]-ready|pm-ready|déploiement/acquisition de l'édition actuelle
2|[acronyme]-e[numéro de l'édition]|pm-e1|développement de l'édition
3|trans_[recension]_[code_manuscrit]| trans_anonyme_ambros-h104|transcription
4(optionel)|rtext_[recension]_[code_manuscrit]| rtext_anonyme_ambros-h104|révision du text
5(optionel)|rbalise_[recension]_[code_manuscrit]| rbalise_anonyme_ambros-h104|révision des balises
6(optionel)|rsyntax_[recension]_[code_manuscrit]| rsyntaxe_anonyme_ambros-h104|révision de la syntaxe
7(optionel)|rev2_[recension]_[code_manuscrit]| rev2_anonyme_ambros-h104|seconde révision

*Il est possible de travailler à plusieurs sur les branches 3, 4 et 5.*

## Stratégie :

1. *La branche 1 [accronyme]-ready(master):*
    la branche [accronyme]-ready est bloquée, elle doit recevoir tous les manuscrits transcrits et révisés qui constituent "l'édition" finale des transcriptions.
2. *La branche 2 ([acronyme]-e[numéro de l'édition]):*
    la branche 2 désigne l'édition en cours (e) et comporte tous les manuscrits révisés dont le status est sur l'état "revised". Tous les membres de l'équipe peuvent merger sur cette branche. **Ne pas verser sur cette branche des transcriptions qui n'ont pas été entièrement révisées.**

La transcription des manuscrits suit en tout quatre étapes:

1. **La transcription:**
    Décrit le travail de création du fichier xml et de transcription du manuscrit.
2. **La révision du text:**
    Révision du contenu de la transcription (fautes de frappes, erreurs de transcription etc)
3. **La révision du balisage:**
    Cette étape porte sur les erreurs possibles de balisage au regard du contenu de la transcription. Par exemple : erreur d'appréciation sur la nature d'un symbole dans le manuscrit qui a aboutit à l'usage de la mauvaise balise dans le fichier xml.
4. **La révision de la syntaxe du balisage:**
    concerne la syntaxe des balises dans le fichier xml (allignement, cohérence vis à vis de la DTD etc.).
5. **Deuxième tour de révision:**
    Si nécessaire, il est possible de poursuivre la révision en proposant un deuxième tour de révision.

La stratégie des branches doit au possible suivre cette structure:

## 1. les branches **"trans"** (transcription)
Pour transcrire un document, on pourra créer une branche de type transcription depuis la branche vp-v1. Il est aussi possible de créer une branche orpheline.

**⚠️ Le recours à cette branche est obligatoire**

nomenclature recommandée:

>trans_[recension]_[nom_du_fichier]
    
exemple (création d'une branche):
``` 
git branch trans_anonyme_ambros-h104
```
**⚠️Attention:** il faut veiller à créer la branche à partir de la branche **vp-v1** pour avoir un historique des commits à jour et cohérent. Il n'est pas nécessaire de mettre l'extension dans le nom (.xml ou autre)

## 2. Les branches/commits **"rtext"** (révision du text) :

Lorsqu'une transcription s'achève, on peut créer et se placer sur une branche de révision du texte. La révision du texte précède les deux autres révisions et doit être achevée avant de passer aux deux autres.

Il est aussi possible de rester sur la même branche (trans). Si c'est votre souhait, il faudra intituler le message des commits avec la mention **rtext**

**contraintes :**

- Si possible, la personne qui révise n'est pas celle qui a transcrit.
- Plusieurs personnes peuvent travailler sur cette branche.
- Succède à la transcription d'un manuscrit.

nomenclature recommandée:
>rtext_[recension]_[code_manuscrit]

**exemple :**

```
git branch rtext_anonyme_ambros-h104
```
**⚠️ Attention :** il faut veiller à créer la branche à partir d'une branche de **transcription** pour avoir un historique des commits à jour et cohérent.

## 3. Les branches **"rbalise"** (révision des balises):

Lorsque la première révision s'achève, on peut créer et se placer sur une branche de révision des balises.

Il est aussi possible de rester sur la même branche (trans). Si c'est votre souhait, il faudra intituler le message des commits avec la mention **rbalise**

**contraintes :**

- Si possible, la personne qui révise n'est pas celle qui a transcrit. 
- Plusieurs personnes peuvent travailler sur cette branche.
- Succède à la révision du text.

nomenclature recommandée:
>rbalise_[recension]_[code_manuscrit]

**exemple :**

```
git branch rbalise_anonyme_ambros-h104
```

**⚠️ Attention :** il faut veiller à créer la branche à partir d'une branche de **revision de balises** pour avoir un historique des commits à jour et cohérent.


## 4. les branches **"rsyntax"** (révision de la syntaxe):

Lorsque la révision des balises est terminée, on peut créer une branche et basculer sur une branche de révision de la syntax (**rsyntax**). 

Il est aussi possible de rester sur la même branche (trans). Si c'est votre souhait, il faudra intituler le message des commits avec la mention **rtext**

**contraintes :**

- Si possible, la personne qui révise n'est pas celle qui a transcrit.
- Plusieurs personnes peuvent travailler sur cette branche.
- Succède à l'étape de la révision des balises.

## 5. les branches **"r2"** (deuxième tour de révision):

Si on souhaite faire un second tour de révision, on pourra poursuivre ce travail sur une branche nommée **r2**. En pricipe le second tour de révision comporte moins de chose à examiner. On pourra donc par commodité utiliser une seule branche pour parcourir le texte, le balisage et la syntaxe lors de cette phase.

A noter que la branch qui contient la transcription (trans) et les premières révisions doivent idéalement être mergées dans la branche de développement (branche 2, c.f.: stratégie des branche -> résumé)

nomenclature recommandée:
>r2_[recension]_[code_manuscrit]

**exemple:**

```
r2_anonyme_ambros-h-104
```

**Note :** il est toutefois possible de créer à partir de cette branche des branches plus spécifiques consacrées à la seconde révision du texte, du balisage ou de la syntaxe.

**Exemple :**

```
r2syntaxe_anonyme_ambros-h-104
```

# Fichier de révision (DTD)

Le fichier de révision vous sera utile pour éliminer les erreurs grossières dans la syntaxe des fichiers de transcription et il vous assistera dans le travail de transcription.

Ce fichier se trouve à la racine du dossier vitae-prophetarum sous le nom :

- tei-irsb.dtd

Pour vous référer à ce fichier depuis un fichier de transcription, vous pouvez insérer la balise suivante après la déclaration (balise) xml :

```xml
<!DOCTYPE TEI SYSTEM "../../tei-irsb.dtd">
```

**cela signifie qu'il n'est plus nécessaire de copier/coller la dtd dans les dossiers !🎉**

note : vous pouvez indiquer la profondeur du dossier avec l'aide des points (..) et du symbole slash(/). Dans l'exemple précédent, on indique que dans l'organisation des dossiers le fichier .dtd se trouve deux niveaux au-dessus de l'emplacement du fichier de transcription. Schématiquement, cela donne :

```
vitae-prophetarum/
├─ recension_x/
│  ├─ transcription_y.xml
├─ tei-irsb.dtd
├─ README.md
```

Sur Vscode, il existe une extension qui vous permettra d'utiliser les suggestions de balises et la validation de votre document : xml (redhat).

Ici le lien d'installation et la documentation complète :

https://marketplace.visualstudio.com/items?itemName=redhat.vscode-xml

# Modification massive du texte : regex

Lorsqu'on travail sur un texte numérisé, il arrive que l'on souhaite proposer des modifications en masse, prenons un exemple : dans une transcriptions xml, il y a une erreur récurrente sur la transcription des points médians. Cette erreur est sytématiquement la même et se trouve à travers tous le document. La modification de ce type de situation peut être longue et laborieuse. Pour éviter une approche "ligne par ligne", il est possible d'utiliser des expressions régulières.

Les expressions régulières permettent de décrire des motifs textuels, de repérer ces motifs dans le text. Une fois les motifs repérés dans le texte il est possible de procéder à une série d'actions standards comme le remplacement du motif par un autre motif ou simplement l'effacement.

Les expressions régulières sont simples à apprendre et très utiles. Vous trouverez de nombreuses ressources pour vous initier à cette technique, par exemple :

https://regexone.com/
https://regexlearn.com/learn

Il existe aussi des sites qui permettent de tester des motifs de texte avant de les appliquer sur l'un de vos documents, par exemple :

https://regex101.com/