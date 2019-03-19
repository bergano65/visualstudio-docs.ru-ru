---
title: Интерфейс IJsDebugFrame | Документация Майкрософт
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
ms.openlocfilehash: 57f5a848967148705a2b8dcd3f6b75dcb3a5db26
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58156818"
---
# <a name="ijsdebugframe-interface"></a>Интерфейс IJsDebugFrame
Представляет кадр стека.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
IJsDebugFrame : public IUnknown;  
```  
  
## <a name="members"></a>Участники  
  
### <a name="public-methods"></a>Открытые методы  
  
|Имя|Описание|  
|----------|-----------------|  
|[Метод IJsDebugFrame::Evaluate](../../winscript/reference/ijsdebugframe-evaluate-method.md)|Вычисление выражения в контексте этого кадра стека.|  
|[Метод IJsDebugFrame::GetDebugProperty](../../winscript/reference/ijsdebugframe-getdebugproperty-method.md)|Возвращает браузер свойств для этого кадра стека.|  
|[Метод IJsDebugFrame::GetDocumentPositionWithId](../../winscript/reference/ijsdebugframe-getdocumentpositionwithid-method.md)|Возвращает текущее положение этого кадра стека в пределах пользовательского документа.|  
|[Метод IJsDebugFrame::GetDocumentPositionWithName](../../winscript/reference/ijsdebugframe-getdocumentpositionwithname-method.md)|Возвращает текущее положение этого кадра стека в пределах пользовательского документа.|  
|[Метод IJsDebugFrame::GetName](../../winscript/reference/ijsdebugframe-getname-method.md)|Получает понятное имя кадра стека.|  
|[Метод IJsDebugFrame::GetReturnAddress](../../winscript/reference/ijsdebugframe-getreturnaddress-method.md)|Получает обратный адрес, отправленный в «start» (см. GetStackRange) кадра.|  
|[Метод IJsDebugFrame::GetStackRange](../../winscript/reference/ijsdebugframe-getstackrange-method.md)|Возвращает диапазон абсолютных адресов логического фрейма стеков JavaScript.|  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** jscript9diag.h  
  
## <a name="see-also"></a>См. также  
 [Справочник по интерфейсам скриптов Windows](../../winscript/reference/windows-script-interfaces-reference.md)