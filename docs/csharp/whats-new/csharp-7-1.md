---
title: Nouveautés de C# 7.1
description: Vue d’ensemble des nouvelles fonctionnalités de C# 7.1.
ms.date: 04/09/2019
ms.openlocfilehash: c79c8576f9cbbd921ebf30bd84ee5a817d6dc6e7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59480961"
---
# <a name="whats-new-in-c-71"></a>Nouveautés de C# 7.1

C# 7.1 est la première version mineure pour le langage C#. Elle marque une cadence de publication accrue pour le langage. Vous pouvez utiliser les nouvelles fonctionnalités plus tôt, dans l’idéal quand chaque nouvelle fonctionnalité est prête. C# 7.1 ajoute la possibilité de configurer le compilateur pour le faire correspondre à une version spécifiée du langage. Ceci vous permet de séparer la décision de mettre à niveau les outils de la décision de mettre à niveau les versions du langage.

C# 7.1 ajoute l’élément de configuration de [sélection de la version du langage](../language-reference/configure-language-version.md), trois nouvelles fonctionnalités du langage et un nouveau comportement du compilateur.

Les nouvelles fonctionnalités de langage de cette version sont :

* [Méthode `async` `Main`](#async-main)
  - Le point d’entrée pour une application peut avoir le modificateur `async`.
* [Expressions littérales `default`](#default-literal-expressions)
  - Vous pouvez utiliser des expressions littérales default dans les expressions de valeur par défaut quand le type cible peut être inféré.
* [Noms des éléments de tuple inférés](#inferred-tuple-element-names)
  - Les noms des éléments de tuple peuvent être inférés dans de nombreux cas à partir de l’initialisation du tuple.
* [Critères spéciaux sur les paramètres de type générique](#pattern-matching-on-generic-type-parameters)
  - Il est possible d’utiliser des expressions de critères spéciaux sur les variables dont le type est un paramètre de type générique.

Enfin, le compilateur a deux options, `/refout` et `/refonly`, qui contrôlent la [génération d’assemblys de références](#reference-assembly-generation).

Pour utiliser les fonctionnalités les plus récentes dans une version mineure, vous devez [configurer la version du langage du compilateur](../language-reference/configure-language-version.md) et sélectionner la version.

## <a name="async-main"></a>Async main

Une méthode *async main* vous permet d’utiliser `await` dans votre méthode `Main`.
Auparavant, vous deviez écrire :

```csharp
static int Main()
{
    return DoAsyncWork().GetAwaiter().GetResult();
}
```

Vous pouvez désormais écrire :

```csharp
static async Task<int> Main()
{
    // This could also be replaced with the body
    // DoAsyncWork, including its await expressions:
    return await DoAsyncWork();
}
```

Si votre programme ne retourne pas de code de sortie, vous pouvez déclarer une méthode `Main` qui retourne une <xref:System.Threading.Tasks.Task> :

```csharp
static async Task Main()
{
    await SomeAsyncMethod();
}
```

Pour plus d’informations, voir l’article [async main](../programming-guide/main-and-command-args/index.md) du guide de programmation.

## <a name="default-literal-expressions"></a>Expressions littérales par défaut

Les expressions littérales par défaut sont une amélioration des expressions de valeur par défaut.
Ces expressions initialisent une variable à la valeur par défaut. Vous deviez écrire auparavant :

```csharp
Func<string, bool> whereClause = default(Func<string, bool>);
```

Vous pouvez désormais omettre le type du côté droit de l’initialisation :

```csharp
Func<string, bool> whereClause = default;
```

Pour plus d’informations sur cette amélioration, voir l’article [Expressions de valeur par défaut](../programming-guide/statements-expressions-operators/default-value-expressions.md) du guide de programmation C#.

Cette amélioration change également certaines des règles d’analyse pour le [mot clé default](../language-reference/keywords/default.md).

## <a name="inferred-tuple-element-names"></a>Noms des éléments de tuple inférés

Cette fonctionnalité est une petite amélioration de la fonctionnalité des tuples introduite dans C# 7.0. Très souvent, quand vous initialisez un tuple, les variables utilisées pour le côté droit de l’affectation sont identiques aux noms que vous souhaitez pour les éléments du tuple :

```csharp
int count = 5;
string label = "Colors used in the map";
var pair = (count: count, label: label);
```

Dans C# 7.1, les noms des éléments du tuple peuvent être inférés à partir des variables utilisées pour initialiser le tuple :

```csharp
int count = 5;
string label = "Colors used in the map";
var pair = (count, label); // element names are "count" and "label"
```

Pour plus d’informations sur cette fonctionnalité, voir l’article [Tuples](../tuples.md).

## <a name="pattern-matching-on-generic-type-parameters"></a>Critères spéciaux sur les paramètres de type générique

À compter de C# 7.1, l’expression de modèle de `is` et du modèle de type `switch` peut avoir le type d’un paramètre de type générique, ce qui peut se révéler particulièrement utile pour vérifier des types potentiellement `struct` ou `class` tout en évitant le boxing.

## <a name="reference-assembly-generation"></a>Génération d’assemblys de références

Il existe deux nouvelles options du compilateur qui génèrent des *assemblys de références uniquement* : [/refout](../language-reference/compiler-options/refout-compiler-option.md) et [/refonly](../language-reference/compiler-options/refonly-compiler-option.md).
Les articles en lien décrivent plus en détail ces options et les assemblys de références.
