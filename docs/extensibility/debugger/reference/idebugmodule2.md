---
title: IDebugModule2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugModule2
helpviewer_keywords:
- IDebugModule2 interface
ms.assetid: 24c2a126-f4ab-4891-8509-8ef99b994c08
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4ea20dac16cdffbac24cbca68c1a337a250ea8cc
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54922773"
---
# <a name="idebugmodule2"></a>IDebugModule2
Этот интерфейс представляет модуль, то есть исполняемый модуль программы, например библиотеку DLL.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugModule2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Модуль отладки (DE) реализует этот интерфейс для представления модуля и предоставляют доступ к информации об этом модуле.  
  
## <a name="notes-for-callers"></a>Заметки о вызывающих объектов  
 Вызов [GetModule](../../../extensibility/debugger/reference/idebugmoduleloadevent2-getmodule.md) возвращает этот интерфейс. Отправляет DE [IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md) интерфейс для сеанса отладки manager (SDM) с помощью [событий](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) метод.  
  
 Этот интерфейс также могут быть возвращены в [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) структуры (которого возвращается путем вызова [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)).  
  
 [Далее](../../../extensibility/debugger/reference/ienumdebugmodules2-next.md) также возвращает этот интерфейс ([EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md) возвращает [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md) интерфейс).  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IDebugModule2`.  
  
|Метод|Описание:|  
|------------|-----------------|  
|[GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)|Получает [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) , описывающий этот модуль.|  
|[ReloadSymbols_Deprecated](../../../extensibility/debugger/reference/idebugmodule2-reloadsymbols-deprecated.md)|УСТАРЕВШИЕ. НЕ ИСПОЛЬЗУЙТЕ. Повторно загружает символы для этого модуля.|  
  
## <a name="remarks"></a>Примечания  
 Сведения о модуле, которые могут отображаться в **модули** окно интегрированной среды разработки.  
  
## <a name="requirements"></a>Требования  
 Header: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)   
 [GetModule](../../../extensibility/debugger/reference/idebugmoduleloadevent2-getmodule.md)   
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)   
 [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)