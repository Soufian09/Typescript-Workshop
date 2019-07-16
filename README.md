## Workshop sur Typescript + React 

TypeScript est un langage de programmation libre et open source développé par Microsoft qui a pour but d'améliorer et de sécuriser la production de code JavaScript. C'est un sur-ensemble de JavaScript (c'est-à-dire que tout code JavaScript correct peut être utilisé avec TypeScript). Le code TypeScript est transcompilé en JavaScript, et peut ainsi être interprété par n'importe quel navigateur web ou moteur JavaScript. TypeScript a été cocréé par Anders Hejlsberg, principal inventeur de C#.

Il permet un typage statique optionnel des variables et des fonctions, la création de classes et d'interfaces, l'import de modules, tout en conservant l'approche non-contraignante de JavaScript. Il supporte la spécification ECMAScript 6.


== Fonctionnalités ==
Le langage ajoute les fonctionnalités suivantes à [[ECMAScript]] 6 :

* [[Typage statique]]
* [[Généricité|Typage générique]]
* [[Interface (programmation orientée objet)|Interfaces]]
* [[Classe (informatique)|Classe]], [[classe abstraite]], [[expressions de classe]]
* Modules
* Mixin
* [[Type énuméré|Enumérations]]
* Paramètres optionnels
* Unions
* Alias, alias de type générique
* Instruction 
* [[Symboles]]
* [[Propriété calculées|Propriétés calculées]]
* Mots clés <code>let</code>, <code>const</code> et <code>for … of</code>

Depuis la version 1.6, la syntaxe [[JSX]] est supportée.

=== Typage statique ===
Le langage permet de préciser le contenu d'une variable ou la valeur de retour d'une fonction (ou d'une méthode) :
<syntaxhighlight lang="typescript">
// Création d'une variable contenant une valeur booléenne.
```var maValeurBooleenne: boolean = false;```

// Création d'une variable contenant une chaîne de caractère.
```var maChaineDeCaractere: string = "Hello World";```

// Création d'une variable contenant un nombre.
```var monNombre: number = 1;```

// Création d'une fonction retournant une chaîne de caractère.
```function maFonction(): string {```
    ```return "Ma valeur de retour";```
```}``` 
</syntaxhighlight>

=== Type générique ===
Il est également possible de créer des types génériques. Pour une méthode :
<syntaxhighlight lang="typescript">
```function maFonction<T>(parametre: T) {```
    // Contenu de la fonction.
}
</syntaxhighlight>

Pour une classe :

<syntaxhighlight lang="typescript">
class MaClasse<T> {
    maVariable : T;
    // Contenu de la classe.
}

// Création d'une instance de la classe "MaClasse" en définissant un type.
var monInstance = new MaClasse<string>();
monInstance.maVariable = "Hello World";
</syntaxhighlight>

=== Interfaces ===
==== Exemple ====
Les interfaces sont un concept essentiel et permettent d'avoir cette notion de typage. En créant une interface, il devient alors possible de l'utiliser pour préciser le contenu d'une variable ou d'une classe :

<syntaxhighlight lang="typescript">
interface MonInterface {
    // Création d'une signature de variable.
    maVariable: string;
    // Création d'une signature de méthode.
    maMethode(parametre: string): void;
}

class MaClasse implements MonInterface {
    maVariable: string;
    maMethode(parametre: string): void {
        // Contenu de la méthode.
    }
}

// Précision du type de la variable en utilisant l'interface.
var instance: MonInterface = new MaClasse();
</syntaxhighlight>

==== DefinitelyTyped ====
Une large bibliothèque d'interface, destinée à des classes (ou fonctions) qui ont été développés en JavaScript, est disponible sur un dépôt GitHub par borisyankov.

=== Classes ===
Le langage apporte le support des classes. L'héritage y est également pris en charge :
<syntaxhighlight lang="typescript">
class MaClasseDeBase {
    private _firstname;
    private _lastname;

    public constructor(firstname: string, lastname: string) {
        this._firstname = firstname;
        this._lastname = lastname;
    }

    public direBonjour(): string {
        return "Bonjour " + this._firstname + ", " + this._lastname;
    }
}

// La classe hérite de "MaClasseDeBase".
class MaClasse extends MaClasseDeBase {
    public constructor(firstname: string, lastname: string) {
        // Accède au constructeur de "MaClasseDeBase".
        super(firstname, lastname);
    }
}

// Création d'une instance de "MaClasse" et 
// appel de la méthode: "direBonjour" de la classe parente : "MaClasseDeBase".
var monInstance: MaClasse = new MaClasse("Jean", "Dupond");
monInstance.direBonjour();
</syntaxhighlight>

Comme il est montré dans l'exemple ci-dessus, le langage autorise les trois types de visibilités, à c'est-à-dire : <code>public</code>, <code>private</code> et <code>protected</code>. Ce dernier est arrivé avec la version 1.3<ref>[http://blogs.msdn.com/b/typescript/archive/2014/11/12/announcing-typescript-1-3.aspx Announcing TypeScript 1.3]</ref>.

=== Modules ===
La création de module (que l'on peut qualifier d'espace de nommage) est permise en utilisant le mot-clé <code>module</code> :
<syntaxhighlight lang="typescript">
module mon.espace.de.nom {
    // Contenu du module: classe, fonction, etc.
}
</syntaxhighlight>

TypeScript distingue les modules internes des modules externes. Les modules internes sont basées sur la syntaxe de ECMAScript 6, tandis que les modules externes exploitent une bibliothèque externe : [[Asynchronous module definition|AMD]] ou [[CommonJS]]<ref>[http://blog.oio.de/2014/01/31/an-introduction-to-typescript-module-system/ An introduction to TypeScript’s module system]</ref>.

=== Énumérations ===
L'utilisation d'énumération dans du code TypeScript est offerte à travers le mot-clé <code>enum</code>. 

Sans la définition de valeur à une constante :
<syntaxhighlight lang="typescript">
enum Couleur {Bleu, Rouge, Vert};
</syntaxhighlight>

Il est à noter que, par défaut, la première constante de l'énumération aura pour valeur, 0.

Avec la définition de valeur :
<syntaxhighlight lang="typescript">
enum Couleur {Bleu = 0, Rouge = 1, Vert = 2};
</syntaxhighlight>

Il est tout à fait possible de donner la valeur "'''1'''" (ou tout autre nombre) à la première constante.

=== Paramètres optionnels ===
Un paramètre peut être défini comme optionnel en TypeScript, en ajoutant le caractère <code>?</code> après le nom de la variable :
<syntaxhighlight lang="typescript">
function maFonction(monParametre?: string) {
    // On teste si le paramètre "monParametre" a une valeur.
    if (monParametre) {
        return monParametre;
    } else {
        // Dans le cas contraire, une valeur par défaut est retournée.
        return "Hello World";
    }
}

// La valeur retournée sera : "Hello World" sans avoir un message d'avertissement lors de la compilation.
var resultat: string = maFonction();
// La valeur retournée sera : "Ma valeur".
var resultat: string = maFonction("Ma valeur");
</syntaxhighlight>

=== Unions ===
Les unions sont arrivées avec la version 1.4 du langage<ref>[http://blogs.msdn.com/b/typescript/archive/2015/01/16/announcing-typescript-1-4.aspx Announcing TypeScript 1.4]</ref>. Cette fonctionnalité autorise l'ajout de multiples types pour le paramètre d'une fonction (ou d'une méthode) :
<syntaxhighlight lang="typescript">
// La fonction autorise que le paramètre soit une chaîne de caractère ou un tableau de chaîne de caractère.
function maFonction(monParametre: string|string[]): void {
    if (typeof monParametre === "string") {
        // Traitement de ma chaîne de caractère.
    } else {
        // Traitement de mon tableau.
    }
}
</syntaxhighlight>

=== Alias ===
En plus des unions, la version 1.4 apporte la possibilité de créer des alias :
<syntaxhighlight lang="typescript">
// Création d'un alias basé sur le type "number".
type MonAlias = number;
// Utilisation de l'alias ci-dessus.
var monNombre: MonAlias = 1;
</syntaxhighlight>
