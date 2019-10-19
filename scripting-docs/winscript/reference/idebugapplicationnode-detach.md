---
title: Идебугаппликатионноде::D етач | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplicationNode.Detach
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplicationNode::Detach
ms.assetid: 36bb3e54-a4df-48d5-a6de-3b8d4c0e98a8
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3ffb422bec21bec65f1550368d898608a5f65015
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574813"
---
# <a name="idebugapplicationnodedetach"></a>IDebugApplicationNode::Detach
Удаляет этот узел приложения из дерева проекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT Detach();  
```  
  
#### <a name="parameters"></a>Параметры  
 Этот метод не принимает параметров.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|значения|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Заметки  
 Этот метод удаляет этот узел приложения из дерева проекта.  
  
## <a name="see-also"></a>См. также  
 [Идебугаппликатионноде:: Attach](../../winscript/reference/idebugapplicationnode-attach.md)    
 [Интерфейс IDebugApplicationNode](../../winscript/reference/idebugapplicationnode-interface.md)