---
title: Интерфейс метод ijsdebugframe | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 5af46b18-9d25-4a23-b8d1-fa23bea3efcf
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 91fe8cdf91b0c2121f4a1a7f111794b0fbe36669
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575107"
---
# <a name="ijsdebugframe-interface"></a>Интерфейс IJsDebugFrame
Представляет кадр стека.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
IJsDebugFrame : public IUnknown;  
```  
  
## <a name="members"></a>Члены  
  
### <a name="public-methods"></a>Открытые методы  
  
|Название|Описание|  
|----------|-----------------|  
|[Метод IJsDebugFrame::Evaluate](../../winscript/reference/ijsdebugframe-evaluate-method.md)|Вычисление выражения в контексте этого кадра стека.|  
|[Метод IJsDebugFrame::GetDebugProperty](../../winscript/reference/ijsdebugframe-getdebugproperty-method.md)|Возвращает браузер свойств для данного кадра стека.|  
|[Метод IJsDebugFrame::GetDocumentPositionWithId](../../winscript/reference/ijsdebugframe-getdocumentpositionwithid-method.md)|Возвращает текущую координату этого кадра стека в документе уровня пользователя.|  
|[Метод IJsDebugFrame::GetDocumentPositionWithName](../../winscript/reference/ijsdebugframe-getdocumentpositionwithname-method.md)|Возвращает текущую координату этого кадра стека в документе уровня пользователя.|  
|[Метод IJsDebugFrame::GetName](../../winscript/reference/ijsdebugframe-getname-method.md)|Возвращает понятное имя кадра стека.|  
|[Метод IJsDebugFrame::GetReturnAddress](../../winscript/reference/ijsdebugframe-getreturnaddress-method.md)|Возвращает обратный адрес, отправленный в "Start" (см. GetStackRange) кадра.|  
|[Метод IJsDebugFrame::GetStackRange](../../winscript/reference/ijsdebugframe-getstackrange-method.md)|Возвращает диапазон абсолютных адресов логического кадра стека JavaScript.|  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** jscript9diag. h  
  
## <a name="see-also"></a>См. также  
 [Справочник по интерфейсам скриптов Windows](../../winscript/reference/windows-script-interfaces-reference.md)