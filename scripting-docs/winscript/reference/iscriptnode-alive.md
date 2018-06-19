---
title: IScriptNode::Alive | Документы Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 0631690cbd961273175cf8dfbe35550980d4994d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24728664"
---
# <a name="iscriptnodealive"></a>IScriptNode::Alive
Указывает, является ли объект все еще активны.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT Alive();  
```  
  
#### <a name="parameters"></a>Параметры  
 Метод не принимает параметры.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Узел сценария, по-прежнему активна.|  
  
## <a name="remarks"></a>Примечания  
 Если объект не активен, компонент модели объектов (COM) возвращает ошибку из маршалинга прокси для вызова этого метода.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IScriptNode](../../winscript/reference/iscriptnode-interface.md)