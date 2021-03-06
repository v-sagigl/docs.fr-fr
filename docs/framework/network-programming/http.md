---
title: HTTP
ms.date: 03/30/2017
helpviewer_keywords:
- protocols, HTTP
- sending data, HTTP
- HttpWebResponse class, sending and receiving data
- HTTP
- receiving data, HTTP
- application protocols, HTTP
- Internet, HTTP
- network resources, HTTP
- HTTP, about HTTP
- HttpWebRequest class, sending and receiving data
ms.assetid: 985fe5d8-eb71-4024-b361-41fbdc1618d8
ms.openlocfilehash: abbb02b7bd22c4b301c5565037f55aa1019fc3ce
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59170597"
---
# <a name="http"></a>HTTP
Avec les classes <xref:System.Net.HttpWebRequest> et <xref:System.Net.HttpWebResponse>, le .NET Framework offre une prise en charge complète du protocole HTTP sur lequel repose la majeure partie du trafic Internet global. Ces classes, dérivées de <xref:System.Net.WebRequest> et <xref:System.Net.WebResponse>, sont retournées par défaut dès que la méthode statique <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> détecte un URI commençant par « http » ou « https ». Dans la plupart des cas, les classes **WebRequest** et **WebResponse** fournissent tous les éléments nécessaires pour effectuer une demande mais, si vous avez besoin d’un accès aux fonctionnalités spécifiques à HTTP exposées en tant que propriétés, vous pouvez effectuer un cast du type de ces classes en **HttpWebRequest** ou **HttpWebResponse**.  
  
 **HttpWebRequest** et **HttpWebResponse** encapsulent une transaction de demande et réponse HTTP standard et fournissent l’accès aux en-têtes HTTP communs. Ces classes prennent également en charge la plupart des fonctionnalités HTTP 1.1, y compris le traitement « pipeline », l’envoi et la réception des données en bloc, l’authentification, la pré-authentification, le chiffrement, la prise en charge de proxy, la validation du certificat de serveur et la gestion des connexions. Les en-têtes personnalisés et les en-têtes non fournis par le biais de propriétés peuvent être stockés dans la propriété **Headers** qui permet d’y accéder.  
  
 **HttpWebRequest** est la classe par défaut utilisée par **WebRequest**. Vous n’avez pas besoin de l’inscrire pour pouvoir passer un URI à la méthode **WebRequest.Create**.  
  
 Vous pouvez configurer votre application pour qu’elle suive automatiquement les redirections HTTP, en définissant la propriété <xref:System.Net.HttpWebRequest.AllowAutoRedirect%2A> sur **true** (valeur par défaut). L’application redirigera les demandes, et la propriété <xref:System.Net.HttpWebResponse.ResponseUri%2A> de **HttpWebResponse** contiendra la ressource web qui a répondu à la demande. Si vous définissez **AllowAutoRedirect** sur **false**, votre application doit être en mesure de traiter les redirections en tant qu’erreurs de protocole HTTP.  
  
 Les applications obtiennent des erreurs de protocole HTTP quand elles interceptent un <xref:System.Net.WebException> avec un <xref:System.Net.WebException.Status%2A> défini à la valeur <xref:System.Net.WebExceptionStatus>. La propriété <xref:System.Net.WebException.Response%2A> contient la **WebResponse** envoyée par le serveur et indique l’erreur HTTP rencontrée.  
  
## <a name="see-also"></a>Voir aussi

- [Accès à Internet via un proxy](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)
- [Utilisation de protocoles d’application](../../../docs/framework/network-programming/using-application-protocols.md)
- [Guide pratique pour accéder aux propriétés spécifiques à HTTP](../../../docs/framework/network-programming/how-to-access-http-specific-properties.md)
