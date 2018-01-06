---
title: "IDebugStackFrame2 | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugStackFrame2
helpviewer_keywords: IDebugStackFrame2 interface
ms.assetid: bd212a6a-dcc6-4756-a77a-e8dfda38b104
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 457cfc4997ca02ca76b296e3b56fded244629e52
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="idebugstackframe2"></a>IDebugStackFrame2
Этот интерфейс представляет кадр стека одного в стеке вызова в определенном потоке.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugStackFrame2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Модуль отладки (DE) реализует этот интерфейс для представления кадр стека.  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 Вызовите [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) для получения [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md) интерфейса. Вызовите [Далее](../../../extensibility/debugger/reference/ienumdebugframeinfo2-next.md) для получения [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) структуру, содержащую `IDebugStackFrame2` интерфейса.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IDebugStackFrame2`.  
  
|Метод|Описание:|  
|------------|-----------------|  
|[GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)|Возвращает контекст кода для этого кадра стека.|  
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)|Возвращает контекст документа для этого кадра стека.|  
|[GetName](../../../extensibility/debugger/reference/idebugstackframe2-getname.md)|Возвращает имя кадра стека.|  
|[GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)|Возвращает описание кадра стека.|  
|[GetPhysicalStackRange](../../../extensibility/debugger/reference/idebugstackframe2-getphysicalstackrange.md)|Возвращает представление зависит от компьютера диапазона физических адресов, связанных с кадром стека.|  
|[GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md)|Получает контекст вычисления для выполнения вычисление выражений в контексте текущего кадра стека и поток.|  
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugstackframe2-getlanguageinfo.md)|Возвращает язык, связанный с кадром стека.|  
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md)|Возвращает описание свойства, связанные с кадра стека.|  
|[EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)|Создает перечислитель для стека свойства рамки.|  
|[GetThread](../../../extensibility/debugger/reference/idebugstackframe2-getthread.md)|Получает поток, связанный с кадра стека.|  
  
## <a name="remarks"></a>Примечания  
 Этот интерфейс получен только в том случае, если отлаживаемая программа была остановлена в точке останова (либо причиной заданное пользователем точки останова или исключение). Из этого интерфейса можно получить контекст выражения для вычисления выражений, можно вернуть список регистров, или можно получить и просмотреть стек вызовов.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Базовые интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)