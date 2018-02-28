---
title: "IRemoteDebugApplication::GetRootNode | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IRemoteDebugApplication.GetRootNode
apilocation:
- pdm.dll
helpviewer_keywords:
- IRemoteDebugApplication::GetRootNode
ms.assetid: 6c043aba-1dc5-41de-9711-96cde5e040f6
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2ef19861e0f386eb7139ec3e732068e4d2b6e7ba
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="iremotedebugapplicationgetrootnode"></a>IRemoteDebugApplication::GetRootNode
Возвращает узел приложения, в которой добавляются все узлы, связанные с приложением.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT GetRootNode(  
   IDebugApplicationNode**  ppdanRoot  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppdanRoot`  
 [out] Узел отладки приложения, в которой добавляются все узлы, связанные с приложением.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод возвращает узел приложения, в которой добавляются все узлы, связанные с приложением.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IRemoteDebugApplication](../../winscript/reference/iremotedebugapplication-interface.md)