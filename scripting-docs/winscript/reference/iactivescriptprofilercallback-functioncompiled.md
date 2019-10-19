---
title: 'IActiveScriptProfilerCallback:: Функтионкомпилед | Документация Майкрософт'
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
ms.openlocfilehash: a17ce7548a6524df6911cdf952393020472b88ed
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576476"
---
# <a name="iactivescriptprofilercallbackfunctioncompiled"></a>IActiveScriptProfilerCallback::FunctionCompiled
Уведомляет объект профилировщика о том, что обработчик скриптов обнаружил функцию при компиляции скрипта.  
  
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
 окне Уникальный идентификатор функции. Этот идентификатор назначается обработчиком скриптов.  
  
 `scriptId`  
 окне Уникальный идентификатор скрипта, частью которого является функция.  
  
 `pwszFunctionName`  
 окне Имя функции или значение NULL для анонимной функции.  
  
 `pwszFunctionNameHint`  
 окне Выводимое имя функции или значение null, если обработчик скриптов не выводит никаких имен.  
  
 `pIDebugDocumentContext`  
 окне При наличии указателя на интерфейс `IUnknown`, который профилировщик должен запрашивать для указателя [интерфейса идебугдокументконтекст](../../winscript/reference/idebugdocumentcontext-interface.md) . В противном случае — значение NULL.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращаемое значение этого метода игнорируется обработчиком скриптов.  
  
## <a name="remarks"></a>Заметки  
 Обработчик скриптов может предоставить контекст документа, только если он поддерживается узлом.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IActiveScriptProfilerCallback](../../winscript/reference/iactivescriptprofilercallback-interface.md)