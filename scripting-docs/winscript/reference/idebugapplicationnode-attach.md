---
title: IDebugApplicationNode::Attach | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 49df95e2c5298fc9bb7025982e75a90548d9613f
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2019
ms.locfileid: "54094956"
---
# <a name="idebugapplicationnodeattach"></a>IDebugApplicationNode::Attach
Добавляет этот узел приложения в дерево указанный проект.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT Attach(  
   IDebugApplicationNode*  pdanParent  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pdanParent`  
 [in] Дерево проекта, где будет добавляться этот узел приложения.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание:|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод добавляет этот узел приложения в проект дерева, с помощью `pdanParent` как родительский. Если `pdanParent` является `NULL`, этот узел приложение будет размещаться узел верхнего уровня.  
  
## <a name="see-also"></a>См. также  
 [IDebugApplicationNode::Detach](../../winscript/reference/idebugapplicationnode-detach.md)   
 [Интерфейс IDebugApplicationNode](../../winscript/reference/idebugapplicationnode-interface.md)