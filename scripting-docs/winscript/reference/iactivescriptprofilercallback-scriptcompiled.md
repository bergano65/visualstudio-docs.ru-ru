---
title: IActiveScriptProfilerCallback::ScriptCompiled | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: bf653e5623506a68e6353e3d9f97077592e87941
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2019
ms.locfileid: "54091511"
---
# <a name="iactivescriptprofilercallbackscriptcompiled"></a>IActiveScriptProfilerCallback::ScriptCompiled
Уведомляет профилировщик, что объект, который обработчик скриптов компиляции сценария. Этот метод вызывается для каждого скрипта, который компилируется.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT ScriptCompiled(  
    [in] PROFILER_TOKEN scriptId,  
    [in] PROFILER_SCRIPT_TYPE type,  
    [in] IUnknown *pIDebugDocumentContext);  
```  
  
#### <a name="parameters"></a>Параметры  
 `scriptId`  
 [in] Уникальный идентификатор сценария, который был скомпилирован. Этот идентификатор назначается обработчик скриптов.  
  
 `type`  
 [in] Тип скрипта, который был скомпилирован. Значения определяются в [перечисление PROFILER_SCRIPT_TYPE](../../winscript/reference/profiler-script-type-enumeration.md).  
  
 `pIDebugDocumentContext`  
 [in] Если он доступен, указатель на `IUnknown` интерфейс, профилировщик должен запросить для [интерфейс IDebugDocumentContext](../../winscript/reference/idebugdocumentcontext-interface.md) указатель. В противном случае это будет значение null.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращаемое значение этого метода обрабатывается обработчиком сценариев.  
  
## <a name="remarks"></a>Примечания  
 Обработчик скриптов может предоставить контекст документа только в том случае, если это поддерживается приложением.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IActiveScriptProfilerCallback](../../winscript/reference/iactivescriptprofilercallback-interface.md)