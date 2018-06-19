---
title: IDebugExpressionContext2 | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugExpressionContext2
helpviewer_keywords:
- IDebugExpressionContext2 interface
ms.assetid: 577fdaae-4b2d-4112-9839-ab899535fa6f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4da916f67611f594b14a41cbb2838f4565eb7fe3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31115441"
---
# <a name="idebugexpressioncontext2"></a>IDebugExpressionContext2
Этот интерфейс представляет контекст для вычисления выражения  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugExpressionContext2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Модуль отладки (DE) реализует этот интерфейс для представления контекста, в котором можно вычислить выражение.  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 Вызов [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) возвращает этот интерфейс. Этот интерфейс доступен только в том случае, если была приостановлена отлаживаемой программы и кадр стека не доступен.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IDebugExpressionContext2`.  
  
|Метод|Описание|  
|------------|-----------------|  
|[GetName](../../../extensibility/debugger/reference/idebugexpressioncontext2-getname.md)|Извлекает имя контекст оценки.|  
|[ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)|Выполняет синтаксический анализ текстового выражения для оценки.|  
  
## <a name="remarks"></a>Примечания  
 Контекст вычисления может рассматриваться как область для выполнения оценки выражения.  
  
 Если программа остановлена, диспетчера сеанса отладки (SDM) получает кадра стека из DE вызовом [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md). Затем вызывает SDM [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) для получения `IDebugExpressionContext2` интерфейса. После этого идет путем вызова [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) для создания [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md) интерфейс, который представляет проанализированное выражение, готовое к вычислению.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md)   
 [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)