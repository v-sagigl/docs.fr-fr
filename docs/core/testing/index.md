---
title: Tests unitaires dans .NET Core et .NET Standard
description: Cet article offre une courte vue d’ensemble des tests unitaires pour les projets .NET Core et .NET Standard.
author: ardalis
ms.author: wiwagn
ms.date: 08/30/2017
ms.custom: seodec18
ms.openlocfilehash: 73667843452bbcab52a8cd4aa7906beecc095677
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61614867"
---
# <a name="unit-testing-in-net-core-and-net-standard"></a>Tests unitaires dans .NET Core et .NET Standard

.NET Core permet de créer facilement des tests unitaires. Cet article présente les tests unitaires et explique ce qui les distingue des autres types de test. Les ressources connexes au bas de la page vous montrent comment ajouter un projet de test à votre solution. Après avoir configuré votre projet de test, vous pouvez exécuter vos tests unitaires à l’aide de la ligne de commande ou de Visual Studio.

.NET Core 2.0 et ultérieur prend en charge [.NET Standard 2.0](../../standard/net-standard.md) et nous allons utiliser ses bibliothèques pour illustrer les tests unitaires.

Vous pouvez utiliser des modèles de projet de test unitaire .NET Core 2.0 et ultérieur intégrés pour C#, F# et Visual Basic comme point de départ de votre projet personnel.

## <a name="what-are-unit-tests"></a>Que sont les tests unitaires ?

L’utilisation de tests automatisés est un très bon moyen de vérifier qu’une application logicielle se comporte comme ses auteurs l’avaient prévu. Il existe plusieurs types de tests pour les applications logicielles. Citons par exemple les tests d’intégration, les tests web, les tests de charge, etc. Les **tests unitaires** testent les méthodes et les composants logiciels individuels. Les tests unitaires doivent uniquement tester le code sous le contrôle du développeur. Ils ne doivent pas tester les problèmes d’infrastructure. Les problèmes d’infrastructure comprennent les bases de données, les systèmes de fichiers et les ressources réseau. 

Par ailleurs, n’oubliez pas qu’il existe des bonnes pratiques pour écrire des tests. Par exemple, le [développement piloté par les tests (TDD)](https://deviq.com/test-driven-development/) est lorsqu’un test unitaire est écrit avant le code qu’il est destiné à vérifier. Le développement TDD est comme créer le plan d’un livre avant de l’écrire. Il est conçu pour aider les développeurs à écrire du code plus simple, plus lisible et plus efficace. 

> [!NOTE]
> L’équipe ASP.NET suit [ces conventions](https://github.com/aspnet/Home/wiki/Engineering-guidelines#unit-tests-and-functional-tests) pour aider les développeurs à trouver des noms qui conviennent pour les méthodes et les classes de test.

Essayez de ne pas introduire de dépendances à l’infrastructure quand vous écrivez des tests unitaires. Elles rendent les tests lents et fragiles et doivent être réservées aux tests d’intégration. Vous pouvez éviter ces dépendances dans votre application en suivant le [principe des dépendances explicites](https://deviq.com/explicit-dependencies-principle/) et en utilisant l’[injection de dépendances](/aspnet/core/fundamentals/dependency-injection). Vous pouvez également conserver vos tests unitaires dans un projet distinct de vos tests d’intégration. Ainsi, vous avez la garantie que votre projet de test unitaire n’a pas de références ou de dépendances aux packages de l’infrastructure.

## <a name="next-steps"></a>Étapes suivantes

Pour en savoir plus sur les tests unitaires dans les projets .NET Core :

Les projets de test unitaire .NET Core sont pris en charge pour :
* [C#](../../csharp/index.md)
* [F#](../../fsharp/index.md)
* [Visual Basic](../../visual-basic/index.md) 

Vous pouvez également choisir entre :
* [xUnit](https://xunit.github.io) 
* [NUnit](https://nunit.org)
* [MSTest](https://github.com/Microsoft/testfx-docs)

Vous pouvez en savoir plus dans les procédures suivantes :

* Créer des tests unitaires à l’aide de [*xUnit* et *C#* avec l’interface CLI .NET Core](unit-testing-with-dotnet-test.md).
* Créer des tests unitaires à l’aide de [*NUnit* et *C#* avec l’interface CLI .NET Core](unit-testing-with-nunit.md).
* Créer des tests unitaires à l’aide de [*MSTest* et *C#* avec l’interface CLI .NET Core](unit-testing-with-mstest.md).
* Créer des tests unitaires à l’aide de [*xUnit* et *F#* avec l’interface CLI .NET Core](unit-testing-fsharp-with-dotnet-test.md).
* Créer des tests unitaires à l’aide de [*NUnit* et *F#* avec l’interface CLI .NET Core](unit-testing-fsharp-with-nunit.md).
* Créer des tests unitaires à l’aide de [*MSTest* et *F#* avec l’interface CLI .NET Core](unit-testing-fsharp-with-mstest.md).
* Créer des tests unitaires à l’aide de [*xUnit* et *Visual Basic* avec l’interface CLI .NET Core](unit-testing-visual-basic-with-dotnet-test.md).
* Créer des tests unitaires à l’aide de [*NUnit* et *Visual Basic* avec l’interface CLI .NET Core](unit-testing-visual-basic-with-nunit.md).
* Créer des tests unitaires à l’aide de [*MSTest* et *Visual Basic* avec l’interface CLI .NET Core](unit-testing-visual-basic-with-mstest.md).

Vous pouvez en savoir plus dans les articles suivants :

* Visual Studio Enterprise propose des outils de test très performants pour .NET Core. Pour en savoir plus, découvrez [Live Unit Testing](/visualstudio/test/live-unit-testing) ou la[couverture du code](https://github.com/Microsoft/vstest-docs/blob/master/docs/analyze.md#working-with-code-coverage).
* Pour plus d’informations sur l’exécution de tests unitaires sélectifs, consultez [Exécution de tests unitaires sélectifs](selective-unit-tests.md) ou [Inclusion et exclusion de tests avec Visual Studio](/visualstudio/test/live-unit-testing#include-and-exclude-test-projects-and-test-methods).
* [Guide pratique pour utiliser xUnit avec .NET Core et Visual Studio](https://xunit.github.io/docs/getting-started-dotnet-core.html).
