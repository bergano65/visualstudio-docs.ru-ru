---
title: IDebugModule3 | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugModule3
helpviewer_keywords:
- IDebugModule3 interface
ms.assetid: 44f8e96e-9c59-4ffc-9a08-9c908a0e4de7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0b74063aa73db8258b2986ac1310d02e36027bf6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31118457"
---
# <a name="idebugmodule3"></a>IDebugModule3
Этот интерфейс представляет модуль, который поддерживает альтернативные расположения символов и JustMyCode состояний.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugModule3 : IDebugModule2  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Модуль отладки (DE) реализует этот интерфейс для поддержки альтернативного расположения символов и для работы с состояниями JustMyCode (см. [глоссарий отладчик Visual Studio](../../../extensibility/debugger/reference/visual-studio-debugger-glossary.md) для определения «JustMyCode»).  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 Вызов [GetSymbolSearchInfo](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md) возвращает этот интерфейс. Отправляет DE [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md) Диспетчер сеанса отладки (SDM), с помощью интерфейса [события](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) метод. Кроме того, вызов [QueryInterface](/cpp/atl/queryinterface) на [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) интерфейс возвращает этот интерфейс.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В дополнение к методам на [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) интерфейс, этот интерфейс реализует следующие методы:  
  
|Метод|Описание|  
|------------|-----------------|  
|[GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md)|Возвращает список путей поиска символов и результаты поиска каждого пути.|  
|[LoadSymbols](../../../extensibility/debugger/reference/idebugmodule3-loadsymbols.md)|Загружает и инициализирует символов для текущего модуля.|  
|[IsUserCode](../../../extensibility/debugger/reference/idebugmodule3-isusercode.md)|Возвращает флаг, указывающий, представляет ли модуль кода пользователя.|  
|[SetJustMyCodeState](../../../extensibility/debugger/reference/idebugmodule3-setjustmycodestate.md)|Указывает, следует ли учитывать модуль пользовательского кода или нет.|  
  
## <a name="remarks"></a>Примечания  
 Visual Studio не типичного потребителя этого интерфейса.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)   
 [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)   
 [GetSymbolSearchInfo](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md)