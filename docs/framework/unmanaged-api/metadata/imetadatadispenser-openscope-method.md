---
title: IMetaDataDispenser::OpenScope, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataDispenser.OpenScope
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenser::OpenScope
helpviewer_keywords:
- IMetaDataDispenser::OpenScope method [.NET Framework metadata]
- OpenScope method, IMetaDataDispenser interface [.NET Framework metadata]
ms.assetid: 65063ad5-e0d9-4c01-8f8b-9a5950109fa6
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5b94987631f7dbbe39e585a8ea2c2252b9427613
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62050166"
---
# <a name="imetadatadispenseropenscope-method"></a>IMetaDataDispenser::OpenScope, méthode
Ouvre un fichier sur disque existant et mappe ses métadonnées dans la mémoire.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT OpenScope (  
    [in]  LPCWSTR     szScope,   
    [in]  DWORD       dwOpenFlags,   
    [in]  REFIID      riid,   
    [out] IUnknown    **ppIUnk  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `szScope`  
 [in] Le nom du fichier à ouvrir. Le fichier doit contenir des métadonnées du common language runtime (CLR).  
  
 `dwOpenFlags`  
 [in] Une valeur de la [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) énumération pour spécifier le mode (lecture, écriture et ainsi de suite) pour l’ouverture.  
  
 `riid`  
 [in] L’IID de l’interface de métadonnées souhaitée doit être retournée ; l’appelant utilisera l’interface à importer (lecture) ou émettre des métadonnées de (écriture).  
  
 La valeur de `riid` doit spécifier une des interfaces « importation » ou « émettre ». Les valeurs valides sont IID_IMetaDataEmit, IID_IMetaDataImport, IID_IMetaDataAssemblyEmit, IID_IMetaDataAssemblyImport, IID_IMetaDataEmit2 ou IID_IMetaDataImport2.  
  
 `ppIUnk`  
 [out] Pointeur vers l’interface retournée.  
  
## <a name="remarks"></a>Notes  
 La copie en mémoire des métadonnées peut être interrogée à l’aide de méthodes à partir d’une des interfaces « importation » ou ajouté à l’aide des méthodes à partir de l’une des interfaces « émettre ».  
  
 Si le fichier cible ne contient-elle pas de métadonnées CLR, la `OpenScope` méthode échoue.  
  
 Dans le .NET Framework versions 1.0 et 1.1, si une étendue est ouvert avec `dwOpenFlags` défini sur ofRead, elle est éligible pour le partage. Autrement dit, si suivantes les appels à `OpenScope` transmettez le nom d’un fichier qui a été ouverte précédemment, la portée existante est réutilisée et un nouvel ensemble de structures de données n’est pas créé. Toutefois, des problèmes peuvent survenir en raison de ce partage.  
  
 Dans la version 2.0 du .NET Framework, les portées ouvertes avec `dwOpenFlags` défini sur ofRead ne sont plus partagées. Utilisez la valeur ofReadOnly pour autoriser l’étendue à partager. Lorsqu’une étendue est partagée, les requêtes qui utilisent des « en lecture/écriture » des interfaces de métadonnées échoue.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Cor.h  
  
 **Bibliothèque :** Utilisé en tant que ressource dans MsCorEE.dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataDispenser, interface](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
- [IMetaDataDispenserEx, interface](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [IMetaDataAssemblyEmit, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
- [IMetaDataAssemblyImport, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
- [IMetaDataEmit, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [IMetaDataImport, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
