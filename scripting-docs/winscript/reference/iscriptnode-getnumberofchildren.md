---
title: 'Искриптноде:: Жетнумберофчилдрен | Документация Майкрософт'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptNode.GetNumberOfChildren
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptNode::GetNumberOfChildren
ms.assetid: 3451c7e9-cb50-482e-9038-6e7d7ce1ecdf
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 67912194b051574d4b4a37e897ec7cac14b02ae2
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577527"
---
# <a name="iscriptnodegetnumberofchildren"></a>IScriptNode::GetNumberOfChildren
Возвращает количество дочерних узлов объекта `IScriptNode`.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT GetNumberOfChildren(  
   ULONG              *pcsn  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pcsn`  
 заполняет Количество дочерних узлов, которые содержит объект `IScriptNode`.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|значения|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Заметки  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IScriptNode](../../winscript/reference/iscriptnode-interface.md)