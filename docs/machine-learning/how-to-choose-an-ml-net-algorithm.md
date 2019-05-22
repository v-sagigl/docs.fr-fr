---
title: Guide pratique pour choisir un algorithme ML.NET
description: Découvrez comment choisir un algorithme ML.NET pour votre modèle Machine Learning
author: natke
ms.topic: overview
ms.date: 04/20/1029
ms.openlocfilehash: d1c637437a7b285f2b66b597d616fcf39248697f
ms.sourcegitcommit: 682c64df0322c7bda016f8bfea8954e9b31f1990
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2019
ms.locfileid: "65557776"
---
# <a name="how-to-choose-an-mlnet-algorithm"></a><span data-ttu-id="41518-103">Guide pratique pour choisir un algorithme ML.NET</span><span class="sxs-lookup"><span data-stu-id="41518-103">How to choose an ML.NET algorithm</span></span>

<span data-ttu-id="41518-104">Pour chaque [tâche ML.NET](resources/tasks.md), il existe plusieurs algorithmes d’entraînement possibles.</span><span class="sxs-lookup"><span data-stu-id="41518-104">For each [ML.NET task](resources/tasks.md), there are multiple training algorithms to choose from.</span></span> <span data-ttu-id="41518-105">Le choix de l’algorithme dépend du problème que vous essayez de résoudre, des caractéristiques de vos données ainsi que des ressources de calcul et de stockage à votre disposition.</span><span class="sxs-lookup"><span data-stu-id="41518-105">Which one to choose depends on the problem you are trying to solve, the characteristics of your data, and the compute and storage resources you have available.</span></span> <span data-ttu-id="41518-106">Il est important de savoir que l’entraînement d’un modèle Machine Learning est un processus itératif.</span><span class="sxs-lookup"><span data-stu-id="41518-106">It is important to note that training a machine learning model is an iterative process.</span></span> <span data-ttu-id="41518-107">Vous devrez peut-être essayer plusieurs algorithmes avant de trouver celui qui marche le mieux.</span><span class="sxs-lookup"><span data-stu-id="41518-107">You might need to try multiple algorithms to find the one that works best.</span></span>

<span data-ttu-id="41518-108">Les algorithmes fonctionnent avec des **caractéristiques**.</span><span class="sxs-lookup"><span data-stu-id="41518-108">Algorithms operate on **features**.</span></span> <span data-ttu-id="41518-109">Les caractéristiques sont des valeurs numériques calculées à partir de vos données d’entrée.</span><span class="sxs-lookup"><span data-stu-id="41518-109">Features are numerical values computed from your input data.</span></span> <span data-ttu-id="41518-110">Elles constituent des entrées optimales pour les algorithmes de machine learning.</span><span class="sxs-lookup"><span data-stu-id="41518-110">They are optimal inputs for machine learning algorithms.</span></span> <span data-ttu-id="41518-111">Vous transformez vos données d’entrée brutes en caractéristiques par le biais d’une ou de plusieurs [transformations de données](resources/transforms.md).</span><span class="sxs-lookup"><span data-stu-id="41518-111">You transform your raw input data into features using one or more [data transforms](resources/transforms.md).</span></span> <span data-ttu-id="41518-112">Par exemple, les données texte sont transformées en un certain nombre de mots et de combinaisons de mots.</span><span class="sxs-lookup"><span data-stu-id="41518-112">For example, text data is transformed into a set of word counts and word combination counts.</span></span> <span data-ttu-id="41518-113">Une fois que les caractéristiques ont été extraites d’un type de données brutes à l’aide de transformations de données, elles sont dites **caractérisées**.</span><span class="sxs-lookup"><span data-stu-id="41518-113">Once the features have been extracted from a raw data type using data transforms, they are referred to as **featurized**.</span></span> <span data-ttu-id="41518-114">Par exemple, du texte caractérisé ou des données image caractérisées.</span><span class="sxs-lookup"><span data-stu-id="41518-114">For example, featurized text, or featurized image data.</span></span>

## <a name="trainer--algorithm--task"></a><span data-ttu-id="41518-115">Entraîneur = algorithme + tâche</span><span class="sxs-lookup"><span data-stu-id="41518-115">Trainer = Algorithm + Task</span></span>

<span data-ttu-id="41518-116">Un algorithme est une opération mathématique qui s’exécute pour produire un **modèle**.</span><span class="sxs-lookup"><span data-stu-id="41518-116">An algorithm is the math that executes to produce a **model**.</span></span> <span data-ttu-id="41518-117">Différents algorithmes produisent des modèles avec des caractéristiques différentes.</span><span class="sxs-lookup"><span data-stu-id="41518-117">Different algorithms produce models with different characteristics.</span></span> 

<span data-ttu-id="41518-118">Avec ML.NET, il est possible d’appliquer le même algorithme à différentes tâches.</span><span class="sxs-lookup"><span data-stu-id="41518-118">With ML.NET, the same algorithm can be applied to different tasks.</span></span> <span data-ttu-id="41518-119">Par exemple, l’algorithme Stochastic Descent Coordinated Ascent peut s’appliquer aux tâches de classification binaire, de classification multiclasse et de régression.</span><span class="sxs-lookup"><span data-stu-id="41518-119">For example, Stochastic Descent Coordinated Ascent can be used for Binary Classification, Multiclass Classification, and Regression.</span></span> <span data-ttu-id="41518-120">Le changement se trouve dans l’interprétation de la sortie de l’algorithme par rapport à la tâche.</span><span class="sxs-lookup"><span data-stu-id="41518-120">The difference is in how the output of the algorithm is interpreted to match the task.</span></span> 

<span data-ttu-id="41518-121">Pour chaque combinaison algorithme/tâche, ML.NET fournit un composant qui exécute l’algorithme d’entraînement et interprète la sortie.</span><span class="sxs-lookup"><span data-stu-id="41518-121">For each algorithm/task combination, ML.NET provides a component that executes the training algorithm and does the interpretation.</span></span> <span data-ttu-id="41518-122">Ces composants sont appelés des « entraîneurs ».</span><span class="sxs-lookup"><span data-stu-id="41518-122">These components are called trainers.</span></span> <span data-ttu-id="41518-123">Par exemple, <xref:Microsoft.ML.Trainers.SdcaRegressionTrainer> utilise l’algorithme **StochasticDualCoordinatedAscent** appliqué à la tâche de **régression**.</span><span class="sxs-lookup"><span data-stu-id="41518-123">For example, the <xref:Microsoft.ML.Trainers.SdcaRegressionTrainer> uses the **StochasticDualCoordinatedAscent** algorithm applied to the **Regression** task.</span></span>

## <a name="linear-algorithms"></a><span data-ttu-id="41518-124">Algorithmes linéaires</span><span class="sxs-lookup"><span data-stu-id="41518-124">Linear algorithms</span></span>

<span data-ttu-id="41518-125">Les algorithmes linéaires produisent un modèle qui calcule des **scores** à partir d’une combinaison linéaire des données d’entrée et d’un ensemble de **pondérations**.</span><span class="sxs-lookup"><span data-stu-id="41518-125">Linear algorithms produce a model that calculates **scores** from a linear combination of the input data and a set of **weights**.</span></span> <span data-ttu-id="41518-126">Les pondérations sont des paramètres du modèle qui sont évalués au moment de l’entraînement.</span><span class="sxs-lookup"><span data-stu-id="41518-126">The weights are parameters of the model estimated during training.</span></span>

<span data-ttu-id="41518-127">Les algorithmes linéaires fonctionnent bien avec des caractéristiques [séparables de façon linéaire](https://en.wikipedia.org/wiki/Linear_separability).</span><span class="sxs-lookup"><span data-stu-id="41518-127">Linear algorithms work well for features that are [linearly separable](https://en.wikipedia.org/wiki/Linear_separability).</span></span>

<span data-ttu-id="41518-128">Préalablement à l’entraînement avec un algorithme linéaire, les caractéristiques doivent être normalisées.</span><span class="sxs-lookup"><span data-stu-id="41518-128">Before training with a linear algorithm, the features should be normalized.</span></span> <span data-ttu-id="41518-129">Cela évite qu’une caractéristique ait plus d’influence que les autres sur le résultat.</span><span class="sxs-lookup"><span data-stu-id="41518-129">This prevents one feature having more influence over the result than others.</span></span>

<span data-ttu-id="41518-130">En général, les algorithmes linéaires sont scalables, rapides à exécuter, et peu coûteux à entraîner et à prédire.</span><span class="sxs-lookup"><span data-stu-id="41518-130">In general linear algorithms are scalable and fast, cheap to train, cheap to predict.</span></span> <span data-ttu-id="41518-131">Ils s’adaptent selon le nombre de caractéristiques et approximativement selon la taille du jeu de données d’entraînement.</span><span class="sxs-lookup"><span data-stu-id="41518-131">They scale by the number of features and approximately by the size of the training data set.</span></span>

<span data-ttu-id="41518-132">Les algorithmes linéaires font plusieurs passages sur les données d’entraînement.</span><span class="sxs-lookup"><span data-stu-id="41518-132">Linear algorithms make multiple passes over the training data.</span></span> <span data-ttu-id="41518-133">Si votre jeu de données tient en mémoire, l’ajout d’un [point de contrôle du cache](xref:Microsoft.ML.LearningPipelineExtensions.AppendCacheCheckpoint*) à votre pipeline ML.NET avant d’ajouter l’entraîneur accélère le processus d’entraînement.</span><span class="sxs-lookup"><span data-stu-id="41518-133">If your dataset fits into memory, then adding a [cache checkpoint](xref:Microsoft.ML.LearningPipelineExtensions.AppendCacheCheckpoint*) to your ML.NET pipeline before appending the trainer, will make the training run faster.</span></span>

<span data-ttu-id="41518-134">**Entraîneurs linéaires**</span><span class="sxs-lookup"><span data-stu-id="41518-134">**Linear Trainers**</span></span>

|<span data-ttu-id="41518-135">Algorithme</span><span class="sxs-lookup"><span data-stu-id="41518-135">Algorithm</span></span>|<span data-ttu-id="41518-136">Propriétés</span><span class="sxs-lookup"><span data-stu-id="41518-136">Properties</span></span>|<span data-ttu-id="41518-137">Entraîneurs</span><span class="sxs-lookup"><span data-stu-id="41518-137">Trainers</span></span>|
|---------|----------|--------|
|<span data-ttu-id="41518-138">Averaged perceptron</span><span class="sxs-lookup"><span data-stu-id="41518-138">Averaged perceptron</span></span>|<span data-ttu-id="41518-139">Idéal pour la classification de texte</span><span class="sxs-lookup"><span data-stu-id="41518-139">Best for text classification</span></span>|<xref:Microsoft.ML.Trainers.AveragedPerceptronTrainer>|
|<span data-ttu-id="41518-140">Stochastic descent coordinated ascent</span><span class="sxs-lookup"><span data-stu-id="41518-140">Stochastic descent coordinated ascent</span></span>|<span data-ttu-id="41518-141">Performances par défaut satisfaisantes sans réglage nécessaire</span><span class="sxs-lookup"><span data-stu-id="41518-141">Tuning not needed for good default performance</span></span>|<span data-ttu-id="41518-142"><xref:Microsoft.ML.Trainers.SdcaLogisticRegressionBinaryTrainer> <xref:Microsoft.ML.Trainers.SdcaNonCalibratedBinaryTrainer> <xref:Microsoft.ML.Trainers.SdcaMaximumEntropyMulticlassTrainer> <xref:Microsoft.ML.Trainers.SdcaNonCalibratedMulticlassTrainer> <xref:Microsoft.ML.Trainers.SdcaRegressionTrainer></span><span class="sxs-lookup"><span data-stu-id="41518-142"><xref:Microsoft.ML.Trainers.SdcaLogisticRegressionBinaryTrainer> <xref:Microsoft.ML.Trainers.SdcaNonCalibratedBinaryTrainer> <xref:Microsoft.ML.Trainers.SdcaMaximumEntropyMulticlassTrainer> <xref:Microsoft.ML.Trainers.SdcaNonCalibratedMulticlassTrainer> <xref:Microsoft.ML.Trainers.SdcaRegressionTrainer></span></span>|
|<span data-ttu-id="41518-143">L-BFGS</span><span class="sxs-lookup"><span data-stu-id="41518-143">L-BFGS</span></span>|<span data-ttu-id="41518-144">À utiliser quand il y a beaucoup de caractéristiques.</span><span class="sxs-lookup"><span data-stu-id="41518-144">Use when number of features is large.</span></span> <span data-ttu-id="41518-145">Génère des statistiques sur l’entraînement de régression logistique, mais est moins scalable que l’algorithme AveragedPerceptronTrainer</span><span class="sxs-lookup"><span data-stu-id="41518-145">Produces logistic regression training statistics, but doesn't scale as well as the AveragedPerceptronTrainer</span></span>|<span data-ttu-id="41518-146"><xref:Microsoft.ML.Trainers.LbfgsLogisticRegressionBinaryTrainer> <xref:Microsoft.ML.Trainers.LbfgsMaximumEntropyMulticlassTrainer> <xref:Microsoft.ML.Trainers.LbfgsPoissonRegressionTrainer></span><span class="sxs-lookup"><span data-stu-id="41518-146"><xref:Microsoft.ML.Trainers.LbfgsLogisticRegressionBinaryTrainer> <xref:Microsoft.ML.Trainers.LbfgsMaximumEntropyMulticlassTrainer> <xref:Microsoft.ML.Trainers.LbfgsPoissonRegressionTrainer></span></span>|
|<span data-ttu-id="41518-147">Symbolic stochastic gradient descent</span><span class="sxs-lookup"><span data-stu-id="41518-147">Symbolic stochastic gradient descent</span></span>|<span data-ttu-id="41518-148">Entraîneur de classification binaire linéaire le plus rapide et le plus précis.</span><span class="sxs-lookup"><span data-stu-id="41518-148">Fastest and most accurate linear binary classification trainer.</span></span> <span data-ttu-id="41518-149">S’adapte bien à divers processeurs</span><span class="sxs-lookup"><span data-stu-id="41518-149">Scales well with number of processors</span></span>|<xref:Microsoft.ML.Trainers.SymbolicSgdLogisticRegressionBinaryTrainer>|

## <a name="decision-tree-algorithms"></a><span data-ttu-id="41518-150">Algorithmes d’arbre de décision</span><span class="sxs-lookup"><span data-stu-id="41518-150">Decision tree algorithms</span></span>

<span data-ttu-id="41518-151">Les algorithmes d’arbre de décision créent un modèle qui contient une série de décisions : en réalité, c’est un organigramme de valeurs de données.</span><span class="sxs-lookup"><span data-stu-id="41518-151">Decision tree algorithms create a model that contains a series of decisions: effectively a flow chart through the data values.</span></span>

<span data-ttu-id="41518-152">Les caractéristiques n’ont pas besoin d’être séparables de façon linéaire pour utiliser ce type d’algorithme.</span><span class="sxs-lookup"><span data-stu-id="41518-152">Features do not need to be linearly separable to use this type of algorithm.</span></span> <span data-ttu-id="41518-153">Elles n’ont pas non plus besoin d’être normalisées, car chaque valeur dans le vecteur de caractéristiques est utilisée indépendamment dans le processus de décision.</span><span class="sxs-lookup"><span data-stu-id="41518-153">And features do not need to be normalized, because the individual values in the feature vector are used independently in the decision process.</span></span>

<span data-ttu-id="41518-154">Les algorithmes d’arbre de décision sont généralement très précis.</span><span class="sxs-lookup"><span data-stu-id="41518-154">Decision tree algorithms are generally very accurate.</span></span>

<span data-ttu-id="41518-155">À l’exception des modèles additifs généralisés, les modèles d’arbre sont parfois moins explicables quand le nombre de caractéristiques est élevé.</span><span class="sxs-lookup"><span data-stu-id="41518-155">Except for Generalized Additive Models (GAMs), tree models can lack explainability when the number of features is large.</span></span>

<span data-ttu-id="41518-156">Les algorithmes d’arbre de décision consomment davantage de ressources et ne s’adaptent pas aussi bien que les algorithmes linéaires.</span><span class="sxs-lookup"><span data-stu-id="41518-156">Decision tree algorithms take more resources and do not scale as well as linear ones do.</span></span> <span data-ttu-id="41518-157">Ils donnent de bons résultats sur les jeux de données tenant en mémoire.</span><span class="sxs-lookup"><span data-stu-id="41518-157">They do perform well on datasets that can fit into memory.</span></span>

<span data-ttu-id="41518-158">Les arbres de décision boostés sont un ensemble de petits arbres où chaque arbre évalue les données d’entrée, puis passe le score à l’arbre suivant pour produire un meilleur score, et ainsi de suite. Chaque arbre de l’ensemble représente une amélioration par rapport à l’arbre précédent.</span><span class="sxs-lookup"><span data-stu-id="41518-158">Boosted decision trees are an ensemble of small trees where each tree scores the input data and passes the score onto the next tree to produce a better score, and so on, where each tree in the ensemble improves on the previous.</span></span>

<span data-ttu-id="41518-159">**Entraîneurs d’arbre de décision**</span><span class="sxs-lookup"><span data-stu-id="41518-159">**Decision tree trainers**</span></span>

|<span data-ttu-id="41518-160">Algorithme</span><span class="sxs-lookup"><span data-stu-id="41518-160">Algorithm</span></span>|<span data-ttu-id="41518-161">Propriétés</span><span class="sxs-lookup"><span data-stu-id="41518-161">Properties</span></span>|<span data-ttu-id="41518-162">Entraîneurs</span><span class="sxs-lookup"><span data-stu-id="41518-162">Trainers</span></span>|
|---------|----------|--------|
|<span data-ttu-id="41518-163">Light gradient boosted machine</span><span class="sxs-lookup"><span data-stu-id="41518-163">Light gradient boosted machine</span></span>|<span data-ttu-id="41518-164">Entraîneur d’arbre de classification binaire le plus rapide et le plus précis.</span><span class="sxs-lookup"><span data-stu-id="41518-164">Fastest and most accurate of the binary classification tree trainers.</span></span> <span data-ttu-id="41518-165">Hautement réglable</span><span class="sxs-lookup"><span data-stu-id="41518-165">Highly tunable</span></span>|<span data-ttu-id="41518-166"><xref:Microsoft.ML.Trainers.LightGbm.LightGbmBinaryTrainer> <xref:Microsoft.ML.Trainers.LightGbm.LightGbmMulticlassTrainer> <xref:Microsoft.ML.Trainers.LightGbm.LightGbmRegressionTrainer> <xref:Microsoft.ML.Trainers.LightGbm.LightGbmRankingTrainer></span><span class="sxs-lookup"><span data-stu-id="41518-166"><xref:Microsoft.ML.Trainers.LightGbm.LightGbmBinaryTrainer> <xref:Microsoft.ML.Trainers.LightGbm.LightGbmMulticlassTrainer> <xref:Microsoft.ML.Trainers.LightGbm.LightGbmRegressionTrainer> <xref:Microsoft.ML.Trainers.LightGbm.LightGbmRankingTrainer></span></span>|
|<span data-ttu-id="41518-167">Fast tree</span><span class="sxs-lookup"><span data-stu-id="41518-167">Fast tree</span></span>|<span data-ttu-id="41518-168">À utiliser pour les données d’image caractérisées.</span><span class="sxs-lookup"><span data-stu-id="41518-168">Use for featurized image data.</span></span> <span data-ttu-id="41518-169">Résilient aux données non équilibrées.</span><span class="sxs-lookup"><span data-stu-id="41518-169">Resilient to unbalanced data.</span></span> <span data-ttu-id="41518-170">Hautement réglable</span><span class="sxs-lookup"><span data-stu-id="41518-170">Highly tunable</span></span> | <span data-ttu-id="41518-171"><xref:Microsoft.ML.Trainers.FastTree.FastTreeBinaryTrainer> <xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer> <xref:Microsoft.ML.Trainers.FastTree.FastTreeTweedieTrainer> <xref:Microsoft.ML.Trainers.FastTree.FastTreeRankingTrainer></span><span class="sxs-lookup"><span data-stu-id="41518-171"><xref:Microsoft.ML.Trainers.FastTree.FastTreeBinaryTrainer> <xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer> <xref:Microsoft.ML.Trainers.FastTree.FastTreeTweedieTrainer> <xref:Microsoft.ML.Trainers.FastTree.FastTreeRankingTrainer></span></span>|
|<span data-ttu-id="41518-172">Fast forest</span><span class="sxs-lookup"><span data-stu-id="41518-172">Fast forest</span></span>|<span data-ttu-id="41518-173">Fonctionne bien avec les données bruyantes</span><span class="sxs-lookup"><span data-stu-id="41518-173">Works well with noisy data</span></span>|<span data-ttu-id="41518-174"><xref:Microsoft.ML.Trainers.FastTree.FastForestBinaryTrainer> <xref:Microsoft.ML.Trainers.FastTree.FastForestRegressionTrainer></span><span class="sxs-lookup"><span data-stu-id="41518-174"><xref:Microsoft.ML.Trainers.FastTree.FastForestBinaryTrainer> <xref:Microsoft.ML.Trainers.FastTree.FastForestRegressionTrainer></span></span>|
|<span data-ttu-id="41518-175">GAM (modèle additif généralisé)</span><span class="sxs-lookup"><span data-stu-id="41518-175">Generalized additive model (GAM)</span></span>|<span data-ttu-id="41518-176">Idéal pour les problèmes avec des algorithmes d’arbre où l’explicabilité est une priorité</span><span class="sxs-lookup"><span data-stu-id="41518-176">Best for problems that perform well with tree algorithms but where explainability is a priority</span></span>|<span data-ttu-id="41518-177"><xref:Microsoft.ML.Trainers.FastTree.GamBinaryTrainer> <xref:Microsoft.ML.Trainers.FastTree.GamRegressionTrainer></span><span class="sxs-lookup"><span data-stu-id="41518-177"><xref:Microsoft.ML.Trainers.FastTree.GamBinaryTrainer> <xref:Microsoft.ML.Trainers.FastTree.GamRegressionTrainer></span></span>|

## <a name="matrix-factorization"></a><span data-ttu-id="41518-178">Factorisation de matrice</span><span class="sxs-lookup"><span data-stu-id="41518-178">Matrix factorization</span></span>

|<span data-ttu-id="41518-179">Propriétés</span><span class="sxs-lookup"><span data-stu-id="41518-179">Properties</span></span>|<span data-ttu-id="41518-180">Entraîneurs</span><span class="sxs-lookup"><span data-stu-id="41518-180">Trainers</span></span>|
|----------|--------|
|<span data-ttu-id="41518-181">Idéal pour les données de catégories éparses, dans des jeux de données volumineux</span><span class="sxs-lookup"><span data-stu-id="41518-181">Best for sparse categorical data, with large datasets</span></span>|<xref:Microsoft.ML.Trainers.FieldAwareFactorizationMachineTrainer>|

## <a name="meta-algorithms"></a><span data-ttu-id="41518-182">Méta-algorithmes</span><span class="sxs-lookup"><span data-stu-id="41518-182">Meta algorithms</span></span>

<span data-ttu-id="41518-183">Ces entraîneurs créent un entraîneur multiclasse à partir d’un entraîneur binaire.</span><span class="sxs-lookup"><span data-stu-id="41518-183">These trainers create a multi-class trainer from a binary trainer.</span></span> <span data-ttu-id="41518-184">À utiliser avec <xref:Microsoft.ML.Trainers.AveragedPerceptronTrainer>, <xref:Microsoft.ML.Trainers.LbfgsLogisticRegressionBinaryTrainer>, <xref:Microsoft.ML.Trainers.SymbolicSgdLogisticRegressionBinaryTrainer>, <xref:Microsoft.ML.Trainers.LightGbm.LightGbmBinaryTrainer>, <xref:Microsoft.ML.Trainers.FastTree.FastTreeBinaryTrainer>, <xref:Microsoft.ML.Trainers.FastTree.FastForestBinaryTrainer>, <xref:Microsoft.ML.Trainers.FastTree.GamBinaryTrainer>.</span><span class="sxs-lookup"><span data-stu-id="41518-184">Use with <xref:Microsoft.ML.Trainers.AveragedPerceptronTrainer>, <xref:Microsoft.ML.Trainers.LbfgsLogisticRegressionBinaryTrainer>, <xref:Microsoft.ML.Trainers.SymbolicSgdLogisticRegressionBinaryTrainer>, <xref:Microsoft.ML.Trainers.LightGbm.LightGbmBinaryTrainer>, <xref:Microsoft.ML.Trainers.FastTree.FastTreeBinaryTrainer>, <xref:Microsoft.ML.Trainers.FastTree.FastForestBinaryTrainer>, <xref:Microsoft.ML.Trainers.FastTree.GamBinaryTrainer>.</span></span>

|<span data-ttu-id="41518-185">Algorithme</span><span class="sxs-lookup"><span data-stu-id="41518-185">Algorithm</span></span>|<span data-ttu-id="41518-186">Propriétés</span><span class="sxs-lookup"><span data-stu-id="41518-186">Properties</span></span>|<span data-ttu-id="41518-187">Entraîneurs</span><span class="sxs-lookup"><span data-stu-id="41518-187">Trainers</span></span>|
|---------|----------|--------|
|<span data-ttu-id="41518-188">One versus all</span><span class="sxs-lookup"><span data-stu-id="41518-188">One versus all</span></span>|<span data-ttu-id="41518-189">Ce classifieur multiclasse entraîne un seul classifieur binaire par classe, ce qui distingue cette classe de toutes les autres classes.</span><span class="sxs-lookup"><span data-stu-id="41518-189">This multiclass classifier trains one binary classifier for each class, which distinguishes that class from all other classes.</span></span> <span data-ttu-id="41518-190">Adaptation limitée selon le nombre de classes à catégoriser</span><span class="sxs-lookup"><span data-stu-id="41518-190">Is limited in scale by the number of classes to categorize</span></span>|[<span data-ttu-id="41518-191">OneVersusAllTrainer\<BinaryClassificationTrainer></span><span class="sxs-lookup"><span data-stu-id="41518-191">OneVersusAllTrainer\<BinaryClassificationTrainer></span></span>](xref:Microsoft.ML.Trainers.OneVersusAllTrainer) |
|<span data-ttu-id="41518-192">Pairwise coupling</span><span class="sxs-lookup"><span data-stu-id="41518-192">Pairwise coupling</span></span>|<span data-ttu-id="41518-193">Ce classifieur multiclasse entraîne un algorithme de classification binaire sur chaque paire de classes.</span><span class="sxs-lookup"><span data-stu-id="41518-193">This multiclass classifier trains a binary classification algorithm on each pair of classes.</span></span> <span data-ttu-id="41518-194">Adaptation limitée selon le nombre de classes, du fait que chaque combinaison de deux classes doit être entraînée.</span><span class="sxs-lookup"><span data-stu-id="41518-194">Is limited in scale by the number of classes, as each combination of two classes must be trained.</span></span>|[<span data-ttu-id="41518-195">PairwiseCouplingTrainer\<BinaryClassificationTrainer></span><span class="sxs-lookup"><span data-stu-id="41518-195">PairwiseCouplingTrainer\<BinaryClassificationTrainer></span></span>](xref:Microsoft.ML.Trainers.PairwiseCouplingTrainer)|

## <a name="k-means"></a><span data-ttu-id="41518-196">K-Means</span><span class="sxs-lookup"><span data-stu-id="41518-196">K-Means</span></span>

|<span data-ttu-id="41518-197">Propriétés</span><span class="sxs-lookup"><span data-stu-id="41518-197">Properties</span></span>|<span data-ttu-id="41518-198">Entraîneurs</span><span class="sxs-lookup"><span data-stu-id="41518-198">Trainers</span></span>|
|----------|--------|
|<span data-ttu-id="41518-199">À utiliser pour le clustering</span><span class="sxs-lookup"><span data-stu-id="41518-199">Use for clustering</span></span>|<xref:Microsoft.ML.Trainers.KMeansTrainer>|

## <a name="principal-component-analysis"></a><span data-ttu-id="41518-200">Principal Component Analysis (PCA)</span><span class="sxs-lookup"><span data-stu-id="41518-200">Principal component analysis</span></span>

|<span data-ttu-id="41518-201">Propriétés</span><span class="sxs-lookup"><span data-stu-id="41518-201">Properties</span></span>|<span data-ttu-id="41518-202">Entraîneurs</span><span class="sxs-lookup"><span data-stu-id="41518-202">Trainers</span></span>|
|----------|--------|
|<span data-ttu-id="41518-203">À utiliser pour la détection d’anomalie</span><span class="sxs-lookup"><span data-stu-id="41518-203">Use for anomaly detection</span></span>|<xref:Microsoft.ML.Trainers.RandomizedPcaTrainer>|

## <a name="naive-bayes"></a><span data-ttu-id="41518-204">Naive Bayes</span><span class="sxs-lookup"><span data-stu-id="41518-204">Naive Bayes</span></span>

|<span data-ttu-id="41518-205">Propriétés</span><span class="sxs-lookup"><span data-stu-id="41518-205">Properties</span></span>|<span data-ttu-id="41518-206">Entraîneurs</span><span class="sxs-lookup"><span data-stu-id="41518-206">Trainers</span></span>|
|----------|--------|
|<span data-ttu-id="41518-207">Cet entraîneur de classification multiclasse s’utilise avec des caractéristiques indépendantes et un petit jeu de données d’entraînement.</span><span class="sxs-lookup"><span data-stu-id="41518-207">Use this multi-class classification trainer when the features are independent, and the training dataset is small.</span></span>|<xref:Microsoft.ML.Trainers.NaiveBayesMulticlassTrainer>|

## <a name="prior-trainer"></a><span data-ttu-id="41518-208">Prior Trainer</span><span class="sxs-lookup"><span data-stu-id="41518-208">Prior Trainer</span></span>

|<span data-ttu-id="41518-209">Propriétés</span><span class="sxs-lookup"><span data-stu-id="41518-209">Properties</span></span>|<span data-ttu-id="41518-210">Entraîneurs</span><span class="sxs-lookup"><span data-stu-id="41518-210">Trainers</span></span>|
|----------|--------|
|<span data-ttu-id="41518-211">Cet entraîneur de classification binaire s’utilise comme base de référence des performances des autres entraîneurs.</span><span class="sxs-lookup"><span data-stu-id="41518-211">Use this binary classification trainer to baseline the performance of other trainers.</span></span> <span data-ttu-id="41518-212">Pour être efficace, les métriques des autres entraîneurs doivent être meilleures que l’entraîneur précédent.</span><span class="sxs-lookup"><span data-stu-id="41518-212">To be effective, the metrics of the other trainers should be better than the prior trainer.</span></span> |<xref:Microsoft.ML.Trainers.PriorTrainer>|