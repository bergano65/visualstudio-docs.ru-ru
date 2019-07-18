---
title: IScriptNode::GetIndexInParent | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptNode.GetIndexInParent
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptNode::GetIndexInParent
ms.assetid: 521c1ca1-2d27-4344-bf3b-d8b53132b648
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 92f5ae074d65d2360bcfb3dda03903aa3c59209e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62786980"
---
# <a name="iscriptnodegetindexinparent"></a>IScriptNode::GetIndexInParent
Возвращает индекс объекта в списке дочерних элементов родительского элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT GetIndexInParent(  
   ULONG              pisn,  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pisn`  
 [out] Возвращает индекс объекта в списке дочерних элементов родительского элемента.  
  
 Если этот метод вызывается `IScriptNode` объект представляет веб-страницы, этот параметр возвращает 0.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IScriptNode](../../winscript/reference/iscriptnode-interface.md)