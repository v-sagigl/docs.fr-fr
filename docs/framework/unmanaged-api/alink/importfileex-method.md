---
title: ImportFileEx, méthode
ms.date: 03/30/2017
api_name:
- IALink2.ImportFileEx
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ImportFileEx
helpviewer_keywords:
- ImportFileEx method
ms.assetid: ad276f3f-b303-46ac-97e0-66a377adaa4f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3b3cf91ad4e048ddfccb4086f36923f33d754ac0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61949121"
---
# <a name="importfileex-method"></a>ImportFileEx, méthode
Importations indiqué assembly ou module indépendant.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT ImportFileEx(  
    LPCWSTR pszFilename,  
    LPCWSTR pszTargetName,  
    BOOL fSmartImport,  
    DWORD dwOpenFlags,  
    mdToken* pImportToken,  
    IMetaDataAssemblyImport** ppAssemblyScope,  
    DWORD* pdwCountOfScopes  
) PURE;  
```  
  
## <a name="parameters"></a>Paramètres  
 `pszFilename`  
 Nom qualifié complet du fichier à partir duquel importer.  
  
 `pszTargetName`  
 Nom facultatif du fichier cible.  
  
 `fSmartImport`  
 Si la valeur est TRUE, ImportTypes est utilisé, sinon l’importation doit être effectuée manuellement.  
  
 `dwOpenFlags`  
 Indicateurs à passer à [OpenScope, méthode](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md).  
  
 `pImportToken`  
 Reçoit l’ID du fichier en cours d’importation.  
  
 `ppAssemblyScope`  
 Reçoit la portée d’importation assembly [IMetaDataAssemblyImport, Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface. A la valeur null si le fichier n’est pas un assembly.  
  
 `pdwCountOfScopes`  
 Reçoit le nombre de fichiers importés et/ou étendues.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne S_OK si la méthode réussit.  
  
## <a name="requirements"></a>Configuration requise  
 Nécessite alink.h.  
  
## <a name="see-also"></a>Voir aussi

- [IALink2, interface](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [IALink, interface](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [API ALink](../../../../docs/framework/unmanaged-api/alink/index.md)
