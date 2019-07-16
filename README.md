# Workshop : Typescript + React
 ![]()
## INSTALLATION ET CONFIGURATION DE TYPESCRIPT: 

### Installation
###### TypeScript peut être installé via le gestionnaire de packages NPM :
* `npm install -g typescript`

Le  `-g`  signifie qu'il est installé en globale afin que le compilateur dactylographiée peut être utilisé dans l'un de vos projets.

###### Vérifiez via votre terminal si TypeScript est correctement installé en tapant :
 * ` tsc -v`   

###### Pour obtenir de l'aide sur les arguments possibles, vous pouvez taper:

* ` tsc -h`

 Voici quelques utilisations courantes utiles: 
###### La commande suivante compilera un fichier.ts unique dans un fichier.js :
* ` tsc fichier.ts`


###### Pour compiler plusieurs `fichiers.ts` :

* `tsc app.ts autresFichier.ts  etc.ts`
###### Cela entraînera 3 fichiers :
* `app.js`
* `autresFichier.js`
* `etc.js`

###### Vous pouvez également utiliser des caractères génériques . La commande suivante compilera tous les fichiers TypeScript du dossier actuel.

* `tsc *.ts` 


