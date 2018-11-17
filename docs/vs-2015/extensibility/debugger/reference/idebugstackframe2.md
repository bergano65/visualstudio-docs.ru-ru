---
title: IDebugStackFrame2 | Документация Майкрософт
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
- IDebugStackFrame2
helpviewer_keywords:
- IDebugStackFrame2 interface
ms.assetid: bd212a6a-dcc6-4756-a77a-e8dfda38b104
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: bc6a6ea1b1d864c3f14158b9687181e6bdb6bc4a
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51816675"
---
# <a name="idebugstackframe2"></a>IDebugStackFrame2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Этот интерфейс представляет одним кадром стека в стеке вызова в конкретном потоке.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugStackFrame2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Модуль отладки (DE) реализует этот интерфейс для представления кадр стека.  
  
## <a name="notes-for-callers"></a>Заметки о вызывающих объектов  
 Вызовите [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) извлекаемого [IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md) интерфейс. Вызовите [Далее](../../../extensibility/debugger/reference/ienumdebugframeinfo2-next.md) извлекаемого [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) структуру, содержащую `IDebugStackFrame2` интерфейс.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IDebugStackFrame2`.  
  
|Метод|Описание:|  
|------------|-----------------|  
|[GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)|Возвращает контекст кода для этого кадра стека.|  
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)|Получает контекст документа для этого кадра стека.|  
|[GetName](../../../extensibility/debugger/reference/idebugstackframe2-getname.md)|Возвращает имя кадра стека.|  
|[GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)|Возвращает описание кадра стека.|  
|[GetPhysicalStackRange](../../../extensibility/debugger/reference/idebugstackframe2-getphysicalstackrange.md)|Получает представление зависит от компьютера диапазона физических адресов, связанных с кадром стека.|  
|[GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md)|Получает контекст вычисления для выполнения вычисления выражения в контексте текущего кадра стека и потока.|  
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugstackframe2-getlanguageinfo.md)|Возвращает язык, связанный с кадром стека.|  
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md)|Возвращает описание свойства, связанные с кадром стека.|  
|[EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)|Создает перечислитель для стека свойства рамки.|  
|[GetThread](../../../extensibility/debugger/reference/idebugstackframe2-getthread.md)|Получает поток, связанный с кадром стека.|  
  
## <a name="remarks"></a>Примечания  
 Этот интерфейс получается, только если отлаживаемая программа остановлена в точке останова (либо из-за заданное пользователем точки останова или исключение). Из этого интерфейса можно получить контексте выражения будут оцениваться выражения, список регистров могут быть возвращены или можно получить и изучить стек вызовов.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Базовые интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)

