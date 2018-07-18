---
title: Интерфейс IJsDebugFrame | Документы Microsoft
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
ms.openlocfilehash: f09a147375661fb52b88f531aff981897138adff
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24729614"
---
# <a name="ijsdebugframe-interface"></a>Интерфейс IJsDebugFrame
Представляет кадр стека.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IJsDebugFrame : public IUnknown;  
```  
  
## <a name="members"></a>Члены  
  
### <a name="public-methods"></a>Открытые методы  
  
|Имя|Описание|  
|----------|-----------------|  
|[Метод IJsDebugFrame::Evaluate](../../winscript/reference/ijsdebugframe-evaluate-method.md)|Вычисление выражения в контексте данного кадра стека.|  
|[Метод IJsDebugFrame::GetDebugProperty](../../winscript/reference/ijsdebugframe-getdebugproperty-method.md)|Возвращает обозреватель свойств для этого кадра стека.|  
|[Метод IJsDebugFrame::GetDocumentPositionWithId](../../winscript/reference/ijsdebugframe-getdocumentpositionwithid-method.md)|Возвращает текущую позицию этого кадра стека в документе уровня пользователя.|  
|[Метод IJsDebugFrame::GetDocumentPositionWithName](../../winscript/reference/ijsdebugframe-getdocumentpositionwithname-method.md)|Возвращает текущую позицию этого кадра стека в документе уровня пользователя.|  
|[Метод IJsDebugFrame::GetName](../../winscript/reference/ijsdebugframe-getname-method.md)|Получает понятное имя кадра стека.|  
|[Метод IJsDebugFrame::GetReturnAddress](../../winscript/reference/ijsdebugframe-getreturnaddress-method.md)|Возвращает обратный адрес, помещенный в начале (см. GetStackRange) кадра.|  
|[Метод IJsDebugFrame::GetStackRange](../../winscript/reference/ijsdebugframe-getstackrange-method.md)|Возвращает диапазон абсолютных адресов кадра стека логических JavaScript.|  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** jscript9diag.h  
  
## <a name="see-also"></a>См. также  
 [Справочник по интерфейсам скриптов Windows](../../winscript/reference/windows-script-interfaces-reference.md)