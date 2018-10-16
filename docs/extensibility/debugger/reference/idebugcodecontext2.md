---
title: IDebugCodeContext2 | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugCodeContext2
helpviewer_keywords:
- IDebugCodeContext2 interface
ms.assetid: 3670439e-2171-405d-9d77-dedb0f1cba93
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5b46ec36a93ac91647a3f17aac28187519ca2447
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31103881"
---
# <a name="idebugcodecontext2"></a>IDebugCodeContext2
Этот интерфейс представляет начальную позицию инструкции кода. Для большинства архитектур во время выполнения в настоящее время контекст кода может рассматриваться как адрес в поток выполнения программы.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugCodeContext2 : IDebugMemoryContext2  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Модуль отладки реализует этот интерфейс для связи позицию инструкции кода место документа.  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 Для многих интерфейсов они возвращают этот интерфейс, чаще всего [GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md). Он также широко используется с [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md) интерфейс также как сведения о точках останова разрешения.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В дополнение к методам на [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) интерфейс, этот интерфейс реализует следующие методы:  
  
|Метод|Описание|  
|------------|-----------------|  
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md)|Возвращает контекст документа, соответствующий контексту активного кода.|  
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugcodecontext2-getlanguageinfo.md)|Возвращает сведения о языке для этого контекста кода.|  
  
## <a name="remarks"></a>Примечания  
 Основное различие между `IDebugCodeContext2` интерфейс и [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) интерфейс является, `IDebugCodeContext2` всегда инструкции по левому краю. Это означает, что `IDebugCodeContext2` всегда указывает на начало инструкцию, тогда как `IDebugMemoryContext2` может указывать любой байт памяти в архитектуре во время выполнения. `IDebugCodeContext2` увеличивается на инструкции, а не размер основное хранилище (обычно байт).  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)   
 [CanSetNextStatement](../../../extensibility/debugger/reference/idebugthread2-cansetnextstatement.md)   
 [SetNextStatement](../../../extensibility/debugger/reference/idebugthread2-setnextstatement.md)   
 [GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md)   
 [GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)   
 [Далее](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-next.md)   
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)