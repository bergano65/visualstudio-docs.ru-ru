---
title: IDebugModule2 | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugModule2
helpviewer_keywords:
- IDebugModule2 interface
ms.assetid: 24c2a126-f4ab-4891-8509-8ef99b994c08
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9fc229a353655aeae06460c32b5233888f22dd6e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62555814"
---
# <a name="idebugmodule2"></a>IDebugModule2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

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
  
|Метод|Описание|  
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
