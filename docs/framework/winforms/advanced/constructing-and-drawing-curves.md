---
title: Génération et dessin de courbes
ms.date: 03/30/2017
helpviewer_keywords:
- drawing [Windows Forms], curves
- examples [Windows Forms], drawing curves
- curves [Windows Forms], drawing
ms.assetid: 76e92623-4130-4644-b867-faca58bdb3a2
ms.openlocfilehash: 92e7b1e8b4ce37db633b5dafe212a252b854d1af
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61935445"
---
# <a name="constructing-and-drawing-curves"></a>Génération et dessin de courbes
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] prend en charge plusieurs types de courbes : splines de Bézier, des splines cardinales, des arcs et des points de suspension. Une ellipse est définie par son rectangle englobant ; un arc est une partie d’une ellipse définie par un angle de départ et un angle de balayage. Une spline cardinale est définie par un tableau de points et un paramètre de tension, la courbe passe sans heurts par chaque point dans le tableau, et le paramètre tension influence la courbure de la courbe. Une spline de Bézier définie par deux points de terminaison et deux points de contrôle que la courbe ne passe pas par les points de contrôle, mais les points de contrôle influencent la direction et de pliage comme la courbe passe à partir d’un point de terminaison à l’autre.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Guide pratique pour Dessiner des splines cardinales](how-to-draw-cardinal-splines.md)  
 Décrit des splines cardinales et comment les dessiner.  
  
 [Guide pratique pour Dessiner une Spline de Bézier unique](how-to-draw-a-single-bezier-spline.md)  
 Décrit une spline de Bézier et comment dessiner un.  
  
 [Guide pratique pour Dessiner une séquence de Splines de Bézier](how-to-draw-a-sequence-of-bezier-splines.md)  
 Explique comment dessiner plusieurs splines de Bézier dans la séquence.
