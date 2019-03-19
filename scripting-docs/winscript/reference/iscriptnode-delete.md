---
title: IScriptNode::Delete | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptNode.Delete
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptNode::Delete
ms.assetid: 6765ff80-a9a8-40a3-a669-7fcc284c87af
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 41bf932b242865b1deac4c61db400f973bd0b00c
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58145009"
---
# <a name="iscriptnodedelete"></a>IScriptNode::Delete
Удаление этого дерева объектов.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT Delete();  
```  
  
#### <a name="parameters"></a>Параметры  
 Метод не принимает параметров.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание:|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 После `Delete` вызывается метод, [IScriptNode::Alive](../../winscript/reference/iscriptnode-alive.md) метода должно быть указано, этот узел скриптов не активна.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IScriptNode](../../winscript/reference/iscriptnode-interface.md)