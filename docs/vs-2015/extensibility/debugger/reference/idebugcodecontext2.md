---
title: IDebugCodeContext2 | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugCodeContext2
helpviewer_keywords:
- IDebugCodeContext2 interface
ms.assetid: 3670439e-2171-405d-9d77-dedb0f1cba93
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2e06fd709b2d076b6fa8de7f104e907eb1b35a42
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68190956"
---
# <a name="idebugcodecontext2"></a>IDebugCodeContext2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Этот интерфейс представляет начальную точку инструкции кода. В настоящее время для большинства архитектур времени выполнения контекст кода можно рассматривать как адрес в потоке выполнения программы.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugCodeContext2 : IDebugMemoryContext2  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Обработчик отладки реализует этот интерфейс, чтобы связать расположение инструкции кода с позицией документа.  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 Методы для многих интерфейсов возвращают этот интерфейс, обычно [жеткодеконтекст](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md). Он также широко используется с интерфейсом [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md) , а также с информацией о разрешении точки останова.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В дополнение к методам в интерфейсе [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) этот интерфейс реализует следующие методы:  
  
|Метод|Описание|  
|------------|-----------------|  
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md)|Возвращает контекст документа, соответствующий контексту активного кода.|  
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugcodecontext2-getlanguageinfo.md)|Возвращает сведения о языке для данного контекста кода.|  
  
## <a name="remarks"></a>Remarks  
 Основное различие между `IDebugCodeContext2` интерфейсом и интерфейсом [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) заключается в том, что `IDebugCodeContext2` всегда выровняйте инструкции. Это означает, что `IDebugCodeContext2` всегда указывает на начало инструкции, в то время как `IDebugMemoryContext2` может указывать на любой байт памяти в архитектуре времени выполнения. `IDebugCodeContext2` увеличивается на инструкции, а не на базовый размер хранилища (обычно это байт).  
  
## <a name="requirements"></a>Требования  
 Заголовок: мсдбг. h  
  
 Пространство имен: Microsoft. VisualStudio. Debugger. Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также:  
 [жетдисассемблистреам](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)   
 [кансетнекстстатемент](../../../extensibility/debugger/reference/idebugthread2-cansetnextstatement.md)   
 [сетнекстстатемент](../../../extensibility/debugger/reference/idebugthread2-setnextstatement.md)   
 [жеткодеконтекст](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md)   
 [жеткодеконтекст](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)   
 [Очеред](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-next.md)   
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
