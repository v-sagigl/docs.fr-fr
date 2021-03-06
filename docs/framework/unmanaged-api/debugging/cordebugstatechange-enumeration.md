---
title: CorDebugStateChange, énumération
ms.date: 02/07/2019
api_name:
- CorDebugStateChange
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 1d4424ab-5143-4e50-a84a-ceeb4ddf3bba
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 05a29022d3ebad37322aef9826f10689d2b5b06b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61723067"
---
# <a name="cordebugstatechange-enumeration"></a>CorDebugStateChange, énumération

Représente la quantité de données mises en cache à ignorer sur la base des modifications apportées au processus.

## <a name="syntax"></a>Syntaxe

```
typedef enum CorDebugStateChange
{
    PROCESS_RUNNING = 0x0000001,
    FLUSH_ALL       = 0x0000002,
} CorDebugStateChange;
```

## <a name="members"></a>Membres

| Membre            | Description                                                              |
| ----------------- | ------------------------------------------------------------------------ |
| `PROCESS_RUNNING` | Le processus a atteint un nouvel état de mémoire via l'exécution en avant.            |
| `FLUSH_ALL`       | La mémoire du processus peut être arbitrairement différente de ce qu'elle était précédemment. |

## <a name="remarks"></a>Notes

 Un membre de la `CorDebugStateChange` énumération est fournie en tant qu’argument lorsque le débogueur appelle la `ProcessStateChanged` méthode avec [ICorDebugProcess4::ProcessStateChanged](icordebugprocess4-processstatechanged-method.md) ou [ICorDebugProcess6 :: ProcessStateChanged](icordebugprocess6-processstatechanged-method.md)

## <a name="requirements"></a>Configuration requise

 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).

 **En-tête :** CorDebug.idl, CorDebug.h

 **Bibliothèque :** CorGuids.lib

 **Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]

## <a name="see-also"></a>Voir aussi

- [Énumérations de débogage](debugging-enumerations.md)
- [Débogage](index.md)
