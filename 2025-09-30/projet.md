objectif : passer par l'IA pour ecrire des post facebook impactants

un formulaire : une requette par ligne
adresse mail :
gemini (c'est normalement claude ai pour la création de contenu)

ici pour eviter les souci, l'ia ne va pas nous fornir l'article au format texte, ou html, ou tout autre format
il va nous le fournir au fomat json

{
    "titre": "...",
    "contenu": [
        "p1..",
        "p2..",
        "...",
        ...
    ],
    "hastags": [
        ...
    ]
}

donc on aura besojn d'un noeud code pour recuperer et mettre au format : html
le titre sera : en gras html 
la liste de paragraphe sera transformée en une liste de paragraphe balise p
et les hatstag touts en bas de l'article, en gras, separées par des visgules