# I.E.T.A

*Commandes git à réaliser selon les étapes*

## Première fois sur le repo

- Faire la commande : ```npm install```
- Aller sur la branche sur laquelle on souhaite travailler : ```git checkout nomBranche```
- Lancer la commande pour ouvrir le serveur et voir le résultat : ```npm run dev```
- Commencer à travailler

## Sauvegarde et push sur GitHub

- Ajouter les changements : ```git add .```
- Faire un commit : ```git commit -m "commit-name"```
- Pousser les changements sur la branche distante : ```git push -u origin nomDeLaBranche```

## Fusion sur GitHub

- Aller dans la section Pull requests
- Cliquer sur "New pull request"
- Configurer la fusion : ```base : main <-- compare : dev``` = on compare 'dev' à 'main', 'dev' sera donc fusionné sur 'main'
  
## Après une fusion

- Aller sur la branche sur laquelle on a fusionné : ```git checkout nomBranche```
- Récupérer les dernières modifications : ```git pull```
- Créer une nouvelle branche sur laquelle travailler : ```git checkout -b nomNouvelleBranche```

## Retravailler sur le projet

- Aller sur la branche principale : 'main' ou 'master' : ```git checkout main``` ou ```git checkout master```
- Récupérer les dernières modifications : ```git pull```
- Aller sur la branche sur laquelle on souhaite travailler : ```git checkout nomBranche```
