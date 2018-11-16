---
title: IDebugCodeContext2 | Документация Майкрософт
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
- IDebugCodeContext2
helpviewer_keywords:
- IDebugCodeContext2 interface
ms.assetid: 3670439e-2171-405d-9d77-dedb0f1cba93
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 83d1e6b5bb9cfdca1fddbec31d46d58940897b9f
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51726630"
---
# <a name="idebugcodecontext2"></a>IDebugCodeContext2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Этот интерфейс представляет начальную позицию инструкции кода. Для большинства архитектур во время выполнения в настоящее время контекст кода может рассматриваться как адрес в поток выполнения программы.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugCodeContext2 : IDebugMemoryContext2  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Модуль отладки реализует этот интерфейс для связи позицию инструкции кода в место документа.  
  
## <a name="notes-for-callers"></a>Заметки о вызывающих объектов  
 Методы на многих интерфейсов возвращают этот интерфейс, чаще всего [GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md). Он также используется широко с [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md) интерфейсе также как сведения о разрешении точки останова.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В дополнение к методам на [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) интерфейс, этот интерфейс реализует следующие методы:  
  
|Метод|Описание:|  
|------------|-----------------|  
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md)|Получает контекст документа, соответствующий контекст active кода.|  
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugcodecontext2-getlanguageinfo.md)|Получает сведения о языке для этого контекста кода.|  
  
## <a name="remarks"></a>Примечания  
 Основное различие между `IDebugCodeContext2` интерфейс и [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) интерфейс является то, что `IDebugCodeContext2` всегда по краю инструкции. Это означает, что `IDebugCodeContext2` всегда указывает на начало инструкции, тогда как `IDebugMemoryContext2` может указывать на любой байт памяти в архитектуре во время выполнения. `IDebugCodeContext2` увеличивается по инструкции, а не по размеру основное хранилище (обычно в байтах).  
  
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

