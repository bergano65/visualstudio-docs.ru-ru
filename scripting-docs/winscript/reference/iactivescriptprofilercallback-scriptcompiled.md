---
title: 'IActiveScriptProfilerCallback:: Скрипткомпилед | Документация Майкрософт'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptProfilerCallback.ScriptCompiled
apilocation:
- scrobj.dll
ms.assetid: 1bb8e9be-cbb1-4a61-b36c-805127a56ac7
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f7252134fc86bfd63b74a181b18327212a1b2dc1
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571659"
---
# <a name="iactivescriptprofilercallbackscriptcompiled"></a>IActiveScriptProfilerCallback::ScriptCompiled
Уведомляет объект профилировщика о том, что обработчик скриптов выполнил компиляцию скрипта. Этот метод вызывается для каждого компилируемого скрипта.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT ScriptCompiled(  
    [in] PROFILER_TOKEN scriptId,  
    [in] PROFILER_SCRIPT_TYPE type,  
    [in] IUnknown *pIDebugDocumentContext);  
```  
  
#### <a name="parameters"></a>Параметры  
 `scriptId`  
 окне Уникальный идентификатор скомпилированного скрипта. Этот идентификатор назначается обработчиком скриптов.  
  
 `type`  
 окне Тип скомпилированного скрипта. Значения определяются в [перечислении PROFILER_SCRIPT_TYPE](../../winscript/reference/profiler-script-type-enumeration.md).  
  
 `pIDebugDocumentContext`  
 окне При наличии указателя на интерфейс `IUnknown`, который профилировщик должен запрашивать для указателя [интерфейса идебугдокументконтекст](../../winscript/reference/idebugdocumentcontext-interface.md) . В противном случае это значение будет равно null.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращаемое значение этого метода игнорируется обработчиком скриптов.  
  
## <a name="remarks"></a>Заметки  
 Обработчик скриптов может предоставить контекст документа, только если он поддерживается узлом.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IActiveScriptProfilerCallback](../../winscript/reference/iactivescriptprofilercallback-interface.md)