---
title: 'Guide pratique : Améliorer la précision du modèle'
description: Découvrez comment améliorer la précision du modèle
ms.date: 04/29/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc
ms.openlocfilehash: 8bb47102ede8e135090b1381eb815dccd512e03d
ms.sourcegitcommit: 682c64df0322c7bda016f8bfea8954e9b31f1990
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2019
ms.locfileid: "65557808"
---
# <a name="improve-mlnet-model-accuracy"></a><span data-ttu-id="f5785-103">Améliorer la précision du modèle ML.NET</span><span class="sxs-lookup"><span data-stu-id="f5785-103">Improve ML.NET Model Accuracy</span></span>

<span data-ttu-id="f5785-104">Découvrez comment améliorer la précision de votre modèle.</span><span class="sxs-lookup"><span data-stu-id="f5785-104">Learn how to improve the accuracy of your model.</span></span>

## <a name="reframe-the-problem"></a><span data-ttu-id="f5785-105">Redéfinir le problème</span><span class="sxs-lookup"><span data-stu-id="f5785-105">Reframe the problem</span></span>

<span data-ttu-id="f5785-106">Parfois, l’amélioration d’un modèle peut n’avoir rien à voir avec les données ou techniques utilisées pour entraîner le modèle.</span><span class="sxs-lookup"><span data-stu-id="f5785-106">Sometimes, improving a model may have nothing to do with the data or techniques used to train the model.</span></span> <span data-ttu-id="f5785-107">En effet, il se peut simplement que la question posée ne soit pas la bonne.</span><span class="sxs-lookup"><span data-stu-id="f5785-107">Instead, it may just be that the wrong question is being asked.</span></span> <span data-ttu-id="f5785-108">Envisagez d’examiner le problème sous différents angles et exploitez les données pour extraire les indicateurs latents et les relations masquées afin d’affiner la question.</span><span class="sxs-lookup"><span data-stu-id="f5785-108">Consider looking at the problem from different angles and leverage the data to extract latent indicators and hidden relationships in order to refine the question.</span></span>

## <a name="provide-more-data-samples"></a><span data-ttu-id="f5785-109">Fournir davantage d’échantillons de données</span><span class="sxs-lookup"><span data-stu-id="f5785-109">Provide more data samples</span></span>

<span data-ttu-id="f5785-110">Comme dans le cas des êtres humains, plus les algorithmes sont entraînés, plus les performances sont susceptibles de s’améliorer.</span><span class="sxs-lookup"><span data-stu-id="f5785-110">Like humans, the more training algorithms get, the likelihood of better performance increases.</span></span> <span data-ttu-id="f5785-111">Une façon d’améliorer les performances d’un modèle consiste à fournir aux algorithmes davantage d’échantillons de données d’entraînement.</span><span class="sxs-lookup"><span data-stu-id="f5785-111">One way to improve model performance is to provide more training data samples to the algorithms.</span></span> <span data-ttu-id="f5785-112">Plus un modèle dispose de données d’entraînement, plus il peut correctement identifier des observations.</span><span class="sxs-lookup"><span data-stu-id="f5785-112">The more data it learns from, the more cases it is able to correctly identify.</span></span>

## <a name="add-context-to-the-data"></a><span data-ttu-id="f5785-113">Ajouter un contexte aux données</span><span class="sxs-lookup"><span data-stu-id="f5785-113">Add context to the data</span></span>

<span data-ttu-id="f5785-114">La signification d’un seul point de données peut être difficile à interpréter.</span><span class="sxs-lookup"><span data-stu-id="f5785-114">The meaning of a single data point can be difficult to interpret.</span></span> <span data-ttu-id="f5785-115">La génération d’un contexte autour des points de données améliore les prises de décision des algorithmes et experts en la matière.</span><span class="sxs-lookup"><span data-stu-id="f5785-115">Building context around the data points helps algorithms as well as subject matter experts better make decisions.</span></span> <span data-ttu-id="f5785-116">Par exemple, le fait qu’une maison a trois chambres n’est pas en soi une bonne indication de son prix.</span><span class="sxs-lookup"><span data-stu-id="f5785-116">For example, the fact that a house has three bedrooms does not on its own give a good indication of its price.</span></span> <span data-ttu-id="f5785-117">Toutefois, si vous ajoutez le contexte et que vous savez maintenant qu’elle se trouve dans une banlieue d’une grande zone métropolitaine où l’âge moyen est de 38 ans, le revenu moyen des ménages est de 80 000 € et les écoles se trouvent dans le 20ème centile supérieur, l’algorithme a plus d’informations sur lesquelles baser ses décisions.</span><span class="sxs-lookup"><span data-stu-id="f5785-117">However, if you add context and now know that it is in a suburban neighborhood outside of a major metropolitan area where average age is 38, average household income is $80,000 and schools are in the top 20th percentile then the algorithm has more information to base its decisions on.</span></span> <span data-ttu-id="f5785-118">Tout ce contexte peut être ajouté en tant qu’entrée au modèle Machine Learning sous la forme de caractéristiques.</span><span class="sxs-lookup"><span data-stu-id="f5785-118">All of this context can be added as input to the machine learning model as features.</span></span>

## <a name="use-meaningful-data-and-features"></a><span data-ttu-id="f5785-119">Utiliser des données et des caractéristiques significatives</span><span class="sxs-lookup"><span data-stu-id="f5785-119">Use meaningful data and features</span></span>

<span data-ttu-id="f5785-120">Bien que l’ajout d’échantillons de données et de caractéristiques puisse aider à améliorer la précision du modèle, cela peut également introduire du bruit, dans la mesure où toutes les données et caractéristiques ne sont pas significatives.</span><span class="sxs-lookup"><span data-stu-id="f5785-120">Although more data samples and features can help improve the accuracy of the model, they may also introduce noise since not all data and features are meaningful.</span></span> <span data-ttu-id="f5785-121">Ainsi, il est important de comprendre quelles sont les caractéristiques qui impactent le plus les décisions prises par l’algorithme.</span><span class="sxs-lookup"><span data-stu-id="f5785-121">Therefore, it is important to understand which features are the ones that most heavily impact decisions made by the algorithm.</span></span> <span data-ttu-id="f5785-122">L’utilisation de techniques telles que PFI (Permutation Feature Importance) peut aider à identifier ces caractéristiques déterminantes, à expliquer le modèle, mais aussi à utiliser la sortie comme méthode de sélection de caractéristiques pour réduire la quantité de caractéristiques bruyantes introduites dans le processus d’entraînement.</span><span class="sxs-lookup"><span data-stu-id="f5785-122">Using techniques like Permutation Feature Importance (PFI) can help identify those salient features and not only help explain the model but also use the output as a feature selection method to reduce the amount of noisy features going into the training process.</span></span>

<span data-ttu-id="f5785-123">Apprenez à utiliser la technique PFI en visitant ce [lien](../how-to-guides/explain-machine-learning-model-permutation-feature-importance-ml-net.md).</span><span class="sxs-lookup"><span data-stu-id="f5785-123">Learn to use PFI by visiting the following [link](../how-to-guides/explain-machine-learning-model-permutation-feature-importance-ml-net.md)</span></span>

## <a name="cross-validation"></a><span data-ttu-id="f5785-124">Validation croisée</span><span class="sxs-lookup"><span data-stu-id="f5785-124">Cross-validation</span></span>

<span data-ttu-id="f5785-125">La validation croisée est une technique d’entraînement et d’évaluation de modèle qui fractionne les données en plusieurs partitions sur lesquelles elle entraîne plusieurs algorithmes.</span><span class="sxs-lookup"><span data-stu-id="f5785-125">Cross-validation is a training and model evaluation technique that splits the data into several partitions and trains multiple algorithms on these partitions.</span></span> <span data-ttu-id="f5785-126">Cette technique améliore la robustesse du modèle en réservant des données à partir du processus d’entraînement.</span><span class="sxs-lookup"><span data-stu-id="f5785-126">This technique improves the robustness of the model by holding out data from the training process.</span></span> <span data-ttu-id="f5785-127">En plus d’améliorer les performances sur les observations invisibles, dans les environnements limités en données, cette technique peut être un outil efficace pour entraîner des modèles avec un jeu de données plus petit.</span><span class="sxs-lookup"><span data-stu-id="f5785-127">In addition to improving performance on unseen observations, in data-constrained environments it can be an effective tool for training models with a smaller dataset.</span></span>

<span data-ttu-id="f5785-128">Consultez le lien suivant pour savoir [comment utiliser la validation croisée dans ML.NET](../how-to-guides/train-machine-learning-model-cross-validation-ml-net.md).</span><span class="sxs-lookup"><span data-stu-id="f5785-128">Visit the following link to learn [how to use cross validation in ML.NET](../how-to-guides/train-machine-learning-model-cross-validation-ml-net.md)</span></span>

## <a name="hyperparameter-tuning"></a><span data-ttu-id="f5785-129">Réglage des hyperparamètres</span><span class="sxs-lookup"><span data-stu-id="f5785-129">Hyperparameter tuning</span></span>

<span data-ttu-id="f5785-130">L’entraînement des modèles Machine Learning est un processus itératif et exploratoire.</span><span class="sxs-lookup"><span data-stu-id="f5785-130">Training machine learning models is an iterative and exploratory process.</span></span> <span data-ttu-id="f5785-131">Par exemple, quel est le nombre optimal de clusters quand un modèle est entraîné à l’aide de l’algorithme k-moyennes ?</span><span class="sxs-lookup"><span data-stu-id="f5785-131">For example, what is the optimal number of clusters when training a model using the K-Means algorithm?</span></span> <span data-ttu-id="f5785-132">La réponse dépend de nombreux facteurs tels que la structure des données.</span><span class="sxs-lookup"><span data-stu-id="f5785-132">The answer depends on many factors such as the structure of the data.</span></span> <span data-ttu-id="f5785-133">La recherche de ce nombre nécessiterait d’expérimenter différentes valeurs pour k, puis d’évaluer les performances afin de déterminer la meilleure valeur.</span><span class="sxs-lookup"><span data-stu-id="f5785-133">Finding that number would require experimenting with different values for k and then evaluating performance to determine which value is best.</span></span> <span data-ttu-id="f5785-134">La pratique de l’ajustement de ces paramètres pour rechercher un modèle optimal est appelée ajustement des hyperparamètres.</span><span class="sxs-lookup"><span data-stu-id="f5785-134">The practice of tuning these parameters to find an optimal model is known as hyper-parameter tuning.</span></span>

## <a name="choose-a-different-algorithm"></a><span data-ttu-id="f5785-135">Choisir un algorithme différent</span><span class="sxs-lookup"><span data-stu-id="f5785-135">Choose a different algorithm</span></span>

<span data-ttu-id="f5785-136">Les tâches de machine learning comme la régression et la classification contiennent diverses implémentations d’algorithmes.</span><span class="sxs-lookup"><span data-stu-id="f5785-136">Machine learning tasks like regression and classification contain various algorithm implementations.</span></span> <span data-ttu-id="f5785-137">Il est possible que le problème que vous essayez de résoudre et que la structure de vos données ne soient pas réellement compatibles avec l’algorithme actuel.</span><span class="sxs-lookup"><span data-stu-id="f5785-137">It may be the case that the problem you are trying to solve and the way your data is structured does not fit well into the current algorithm.</span></span> <span data-ttu-id="f5785-138">Dans ce cas, envisagez d’utiliser un algorithme différent pour votre tâche pour voir s’il apprend mieux à partir de vos données.</span><span class="sxs-lookup"><span data-stu-id="f5785-138">In such case, consider using a different algorithm for your task to see if it learns better from your data.</span></span>

<span data-ttu-id="f5785-139">Le lien suivant fournit plus de [conseils sur l’algorithme à choisir](../how-to-choose-an-ml-net-algorithm.md).</span><span class="sxs-lookup"><span data-stu-id="f5785-139">The following link provides more [guidance on which algorithm to choose](../how-to-choose-an-ml-net-algorithm.md).</span></span>