---
ms.openlocfilehash: 88d6c166acf9e9ab72c2713b575a8453779f70d1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59774168"
---
### <a name="attempting-a-tcpip-connection-to-a-sql-server-database-that-resolves-to-localhost-fails"></a>Une tentative de connexion TCP/IP à une base de données SQL Server qui se résout en `localhost` échoue

|   |   |
|---|---|
|Détails|Dans .NET Framework 4.6 et 4.6.1, une tentative de connexion TCP/IP à une base de données SQL Server qui se résout en <code>localhost</code> échoue avec l’erreur &quot;Une erreur liée au réseau ou spécifique à l’instance s’est produite lors de l’établissement d’une connexion à SQL Server. Le serveur est introuvable ou n’est pas accessible. Vérifiez que le nom de l’instance est correct et que SQL Server est configuré pour autoriser les connexions distantes. (fournisseur : Interfaces réseau SQL, erreur : 26 - Erreur lors de la localisation de Server/Instance spécifié)&quot;|
|Suggestion|Ce problème a été résolu et le comportement précédent a été restauré dans .NET Framework 4.6.2. Pour vous connecter à une base de données SQL Server qui se résout en <code>localhost</code>, effectuez une mise à niveau vers .NET Framework 4.6.2.|
|Portée|Mineur|
|Version|4.6|
|Type|Runtime|
