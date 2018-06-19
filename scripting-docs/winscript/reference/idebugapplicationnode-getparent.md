---
title: IDebugApplicationNode::GetParent | Документы Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplicationNode.GetParent
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplicationNode::GetParent
ms.assetid: 88ba3a53-0cd7-4e1f-8558-79c20ac76cc9
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 23dbc8b4dc0c12a25349ddaf7d8fd711df0a9f4b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24725364"
---
# <a name="idebugapplicationnodegetparent"></a>IDebugApplicationNode::GetParent
Возвращает родительский узел данного узла приложения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT GetParent(  
   IDebugApplicationNode**  pprddp  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pprddp`  
 [out] Родительский узел приложения этого узла приложения.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод возвращает родительский узел данного узла приложения.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDebugApplicationNode](../../winscript/reference/idebugapplicationnode-interface.md)