## Workshop sur Typescript + React 
# Installation :

- Via votre terminal , tapez :  ```npx create-react-app NOM-APP --typescript``` .
- ``` cd NOM-APP```



## Qu'est ce que Typescript ?? 
TypeScript est un langage de programmation libre et open source développé par Microsoft qui a pour but d'améliorer et de sécuriser la production de code JavaScript. C'est un sur-ensemble de JavaScript (c'est-à-dire que tout code JavaScript correct peut être utilisé avec TypeScript). Le code TypeScript est transcompilé en JavaScript, et peut ainsi être interprété par n'importe quel navigateur web ou moteur JavaScript. TypeScript a été cocréé par Anders Hejlsberg, principal inventeur de C#.

Il permet aussi un typage statique optionnel des variables et des fonctions, la création de classes et d'interfaces, l'import de modules, tout en conservant l'approche non-contraignante de JavaScript. Il supporte la spécification ECMAScript 6.


Le système de typage
Les déclarations: L’un des principes de base de TypeScript, et la possibilité de définir les types des variables et des objets utilisés dans le code.

1-La définition du type d’une donnée s’effectue lors de sa déclaration

``` 
var a : number = 2;
var b : string = "Test";
var c : boolean = false;
var x : any ;
```
2-Le type Array  : TypeScript, comme JavaScript, vous permet de travailler avec des tableaux de valeurs. Les types de tableaux peuvent être écrits de deux façons. Vous utilisez le type des éléments suivi de « [] » pour désigner un tableau de ce type où vous utilisez un type de tableau générique, Array "elementType"

``` 
var tab : string[] = ["a","b","c"];
var tab : Array<string> = ["a","b","c"];
```
3-Les Fonctions: Nous pouvons ajouter des types à chacun des paramètres, puis à la fonction elle- même pour ajouter un type de retour. TypeScript peut comprendre le type de retour en regardant les instructions de retour, donc nous pouvons aussi le laisser dans plusieurs cas.

```
function maFonction():string {
    return "Ma valeur de retour";
} 
```

4- Les types primitifs :  TypeScript dispose d’un ensemble de types primitifs. Parmi ceux-ci se trouvent bien entendu les types primitifs déjà présents dans JavaScript tels queString, Number, Boolean et Arrays pour les tableaux.

À ces types primitifs issus de JavaScript s’ajoutent les énumérations. Elles se déclarent avec le mot-clé enum au lieu de var.

```
enum Color {rouge , vert , bleu }
let c : Color = Color.rouge; 
```

5-Le type void : Le type void permet de déterminer l’absence totale de type. Il est utilisé pour les fonctions ne retournant aucune valeur.

Attention ! Void ne désigne que l’absence de valeur et non pas un type indéfini.

```
function alertInfo():void {
    alert("Ceci est un msg d'alerte");
} 
```


### L'Objet

1-Les classes Avec l'ES2015 le JavaScript supporte l'utilisation du mot clef class. TypeScript implémente le système de classe d’ES2015 et définit un constructor comme méthode d’instanciation.

```
class Livre {
    titre :string;
    auteur : string;

    constructor(titre: string , auteur: string){
        this.titre = titre;
        this.auteur = auteur;
    }
}
```

2- Les interfaces : TypeScript permet de définir des interfaces très simplement grâce au mot-clé interface. Les interfaces, comme dans tous les langages objet, définissent des contrats que d’autres objets doivent respecter.

- Exemple : Dans une usine qui produit des moteurs, chaque moteur doit pouvoir "démarrer" et "arrêter".

``` 
interface Moteur{
    demarrer();
    arreter();
}
class Moteur implements Moteur{
    start(){
        //Votre code
    }
    arreter(){
        //Votre code
    }
}
```
3- Les Namespaces: Les namespaces vous permettent d'organiser les variables dans un groupe donné afin d'éviter les problèmes d'écrasement des variables.

``` 
namespace Exemple {
    export let variable-1 = 1
    let variable-2 = 2
    export class Demo { }
}
Exemple.variable-1
Exemple.variable-2
let demo = new Exemple.Demo()
```
4- Les Modules: Les modules se présentent comme des namespaces que l'on va pouvoir isoler dans un fichier séparé.

Pour concevoir un module, il suffit d’avoir le mot-clé export  ou import  dans un fichier TypeScript. Pour rendre disponible une variable, fonction, interface ou classe dans un module, on la préfixe par export.

``` 
class Personne {
    private nom : string;
    private prenom : string;
    public constructor (nom:string , prenom:string){
        this.nom;
        this.prenom;
    }
    public hello():void {
        alert ("hello" + this.nom + " "+ this.prenom);
    }
}
```
