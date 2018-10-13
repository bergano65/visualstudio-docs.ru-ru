---
title: IDebugExpressionContext2 | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
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
ms.openlocfilehash: b58a8b2987b8ad90cad0fa3655ee9fed751f1877
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49181796"
---
# <a name="idebugexpressioncontext2"></a>IDebugExpressionContext2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

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

