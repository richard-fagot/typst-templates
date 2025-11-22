# Template pour les réunions
`obsidian-meeting.typ`est un template pour convertir une note *Obsidian* de type réunion en un pdf distribuable aux personnes n'ayant pas accès au Vault *Obsidian*.

Pour lancer la convertion :
```shell
pandoc source.md \
      --wrap=none \
      --pdf-engine=typst \
      --template=template.typ  \
      -V filename="<NOM_REUNION>"  \
      --lua-filter=checkbox-preserve.lua  \
      -o out.pdf
``` 

Où `template.type` permet de configurer le template :

```typst
#import "obsidian.typ": obsidian

#let titre = "$filename$"
#show: doc => obsidian(titre, "Réunion de travail", "17/11/2025", doc)

$body$
```
