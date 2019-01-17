---
title: Интерфейс IJsDebugFrame | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 5af46b18-9d25-4a23-b8d1-fa23bea3efcf
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2fa491a02d289a0a92a70348ec5ef483dd8f8467
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2019
ms.locfileid: "54093306"
---
# <a name="ijsdebugframe-interface"></a>Интерфейс IJsDebugFrame
Представляет кадр стека.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
IJsDebugFrame : public IUnknown;  
```  
  
## <a name="members"></a>Члены  
  
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