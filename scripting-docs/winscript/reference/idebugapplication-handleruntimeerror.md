---
title: IDebugApplication::HandleRuntimeError | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.HandleRuntimeError
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::HandleRuntimeError
ms.assetid: f8f3bbaf-09e5-4d01-8a35-f380bc7ff8ed
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0a457ba0dcc6fb7f8a95a982b6dabd93f9d0207e
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58150105"
---
# <a name="idebugapplicationhandleruntimeerror"></a>IDebugApplication::HandleRuntimeError
Приводит к блокировке текущего потока и отправляет уведомление об ошибке отладчика интегрированной среды разработки.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT HandleRuntimeError(  
   IActiveScriptErrorDebug*  pErrorDebug,  
   IActiveScriptSite*        pScriptSite,  
   BREAKRESUMEACTION*        pbra,  
   ERRORRESUMEACTION*        perra,  
   BOOL*                     pfCallOnScriptError  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pErrorDebug`  
 [in] Произошла ошибка.  
  
 `pScriptSite`  
 [in] Сайт скрипта потока.  
  
 `pbra`  
 [out] Действие, выполняемое, когда отладчик возобновляет работу приложения.  
  
 `perra`  
 [out] Действие, выполняемое, когда отладчик возобновляет работу приложения, если возникает ошибка.  
  
 `pfCallOnScriptError`  
 [out] Флаг, который является `TRUE` если следует вызывать обработчик `IActiveScriptSite::OnScriptError` метод.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание:|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 Модуль языка вызывает этот метод в контексте потока, который приводит к ошибке времени выполнения. Этот метод приводит к блокировке текущего потока и отправляет уведомление об ошибке, который должны отправляться отладчик интегрированной среды разработки. Когда отладчик интегрированной среды разработки возобновляет работу приложения, этот метод возвращает с действие, которое должно быть выполнено.  
  
> [!NOTE]
>  Во время и в случае сбоя во время выполнения, модуль языка могут быть вызваны поток может выполнять такие задачи, как перечислить кадры стека или вычислять выражения.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDebugApplication](../../winscript/reference/idebugapplication-interface.md)   
 [Интерфейс IActiveScriptErrorDebug](../../winscript/reference/iactivescripterrordebug-interface.md)   
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)   
 [Перечисление BREAKRESUMEACTION](../../winscript/reference/breakresumeaction-enumeration.md)   
 [Перечисление ERRORRESUMEACTION](../../winscript/reference/errorresumeaction-enumeration.md)