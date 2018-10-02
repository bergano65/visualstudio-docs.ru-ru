---
title: IDebugExpressionContext2 | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugExpressionContext2
helpviewer_keywords:
- IDebugExpressionContext2 interface
ms.assetid: 577fdaae-4b2d-4112-9839-ab899535fa6f
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8e69f15da81d95e92ffd344fc44b7aa1c44ccf8d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47568436"
---
# <a name="idebugexpressioncontext2"></a>IDebugExpressionContext2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [IDebugExpressionContext2](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugexpressioncontext2).  
  
Этот интерфейс представляет контекст для вычисления выражений  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugExpressionContext2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Модуль отладки (DE) реализует этот интерфейс для представления контекста, в котором можно вычислить выражение.  
  
## <a name="notes-for-callers"></a>Заметки о вызывающих объектов  
 Вызов [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) возвращает данный интерфейс. Этот интерфейс доступен только в том случае, когда был приостановлен отлаживаемой программы и доступен кадр стека.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IDebugExpressionContext2`.  
  
|Метод|Описание|  
|------------|-----------------|  
|[GetName](../../../extensibility/debugger/reference/idebugexpressioncontext2-getname.md)|Извлекает имя в контекст оценки.|  
|[ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)|Выполняет синтаксический анализ текстового выражения для оценки.|  
  
## <a name="remarks"></a>Примечания  
 Контекст оценки может рассматриваться в качестве области действия для выполнения вычисления выражений.  
  
 Когда программа остановлена, диспетчер отладки сеансов (SDM) получает кадр стека от DE вызовом [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md). Затем вызывает SDM [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) для получения `IDebugExpressionContext2` интерфейс. Затем следует вызов [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) для создания [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md) интерфейс, который представляет проанализированное выражение, готовое к вычислению.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md)   
 [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)

