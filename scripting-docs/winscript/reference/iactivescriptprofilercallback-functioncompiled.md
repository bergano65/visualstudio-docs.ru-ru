---
title: IActiveScriptProfilerCallback::FunctionCompiled | Документы Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 797476d4892224ad0b27c9caf579c0704693c835
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24645914"
---
# <a name="iactivescriptprofilercallbackfunctioncompiled"></a>IActiveScriptProfilerCallback::FunctionCompiled
Уведомляет профилировщик, что объект, который модуль создания скриптов обнаружил функцию при компиляции сценария.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT FunctionCompiled(  
    [in] PROFILER_TOKEN functionId,  
    [in] PROFILER_TOKEN scriptId,  
    [in] [string] const WCHAR *pwszFunctionName,  
    [in] [string] const WCHAR *pwszFunctionNameHint,  
    [in] IUnknown *pIDebugDocumentContext);  
```  
  
#### <a name="parameters"></a>Параметры  
 `functionId`  
 [in] Уникальный идентификатор функции. Этот идентификатор назначается обработчиком сценариев.  
  
 `scriptId`  
 [in] Уникальный идентификатор скрипт, функция.  
  
 `pwszFunctionName`  
 [in] Имя функции или значение null для анонимной функции.  
  
 `pwszFunctionNameHint`  
 [in] Выводимый имя функции или значение null, если обработчик скриптов не выводит любое имя.  
  
 `pIDebugDocumentContext`  
 [in] При наличии указатель `IUnknown` интерфейс, профилировщик должен запрашивать [интерфейс IDebugDocumentContext](../../winscript/reference/idebugdocumentcontext-interface.md) указателя. В противном случае — значение NULL.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращаемое значение этого метода обрабатывается обработчиком сценариев.  
  
## <a name="remarks"></a>Примечания  
 Обработчик скриптов может предоставить контекст документа только в том случае, если это поддерживается приложением.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IActiveScriptProfilerCallback](../../winscript/reference/iactivescriptprofilercallback-interface.md)