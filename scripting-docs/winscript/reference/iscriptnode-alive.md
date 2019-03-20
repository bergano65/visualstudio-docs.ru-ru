---
title: IScriptNode::Alive | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptNode.Alive
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptNode::Alive
ms.assetid: d2755c83-e9b9-4c0a-acb7-25b554fc9fe8
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: da0a55d26b5ab643670ba7ed51e576eeb89d8b98
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58159222"
---
# <a name="iscriptnodealive"></a>IScriptNode::Alive
Указывает, является ли объект все еще активна.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT Alive();  
```  
  
#### <a name="parameters"></a>Параметры  
 Метод не принимает параметров.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Узел сценария, по-прежнему активна.|  
  
## <a name="remarks"></a>Примечания  
 Если объект не активен, компонент модели объектов (COM) возвращает ошибку из маршалинга прокси для вызова этого метода.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IScriptNode](../../winscript/reference/iscriptnode-interface.md)