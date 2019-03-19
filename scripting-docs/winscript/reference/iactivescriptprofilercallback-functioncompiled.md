---
title: IActiveScriptProfilerCallback::FunctionCompiled | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptProfilerCallback.FunctionCompiled
apilocation:
- scrobj.dll
ms.assetid: a7e9ef17-3891-4731-9d08-c37bc489be61
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1a039f7a682babebdccad276adce55e69bb8e0bc
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58153725"
---
# <a name="iactivescriptprofilercallbackfunctioncompiled"></a>IActiveScriptProfilerCallback::FunctionCompiled
Уведомляет профилировщик, что объект, который обработчик скриптов обнаружил функцию, при компиляции сценария.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT FunctionCompiled(  
    [in] PROFILER_TOKEN functionId,  
    [in] PROFILER_TOKEN scriptId,  
    [in] [string] const WCHAR *pwszFunctionName,  
    [in] [string] const WCHAR *pwszFunctionNameHint,  
    [in] IUnknown *pIDebugDocumentContext);  
```  
  
#### <a name="parameters"></a>Параметры  
 `functionId`  
 [in] Уникальный идентификатор функции. Этот идентификатор назначается обработчик скриптов.  
  
 `scriptId`  
 [in] Уникальный идентификатор сценария, который входит функция.  
  
 `pwszFunctionName`  
 [in] Имя функции или значение null для анонимной функции.  
  
 `pwszFunctionNameHint`  
 [in] Выводимые имя функции или значение null, если обработчик скриптов не подразумевает любое имя.  
  
 `pIDebugDocumentContext`  
 [in] Если он доступен, указатель на `IUnknown` интерфейс, профилировщик должен запросить для [интерфейс IDebugDocumentContext](../../winscript/reference/idebugdocumentcontext-interface.md) указатель. В противном случае — значение NULL.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращаемое значение этого метода обрабатывается обработчиком сценариев.  
  
## <a name="remarks"></a>Примечания  
 Обработчик скриптов может предоставить контекст документа только в том случае, если это поддерживается приложением.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IActiveScriptProfilerCallback](../../winscript/reference/iactivescriptprofilercallback-interface.md)