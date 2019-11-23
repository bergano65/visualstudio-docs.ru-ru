---
title: 'Идебугаппликатионноде:: Attach | Документация Майкрософт'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplicationNode.Attach
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplicationNode::Attach
ms.assetid: f4aad4ae-5bb0-4b5e-8f70-912a677f8f7a
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 30d4e189ec878def1cfd88517654955cd2d1aa12
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574784"
---
# <a name="idebugapplicationnodeattach"></a>IDebugApplicationNode::Attach
Добавляет этот узел приложения в указанное дерево проекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT Attach(  
   IDebugApplicationNode*  pdanParent  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pdanParent`  
 окне Дерево проекта, в котором будет добавлен узел приложения.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод добавляет этот узел приложения в дерево проекта, используя `pdanParent` в качестве родителя. Если `pdanParent` `NULL`, этот узел приложения будет узлом верхнего уровня.  
  
## <a name="see-also"></a>См. также:  
 [Идебугаппликатионноде::D етач](../../winscript/reference/idebugapplicationnode-detach.md)   
 [Интерфейс IDebugApplicationNode](../../winscript/reference/idebugapplicationnode-interface.md)