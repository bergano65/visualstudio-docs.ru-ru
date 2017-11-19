---
title: "IDebugApplication::HandleRuntimeError | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugApplication.HandleRuntimeError
apilocation: pdm.dll
helpviewer_keywords: IDebugApplication::HandleRuntimeError
ms.assetid: f8f3bbaf-09e5-4d01-8a35-f380bc7ff8ed
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eead4780ff061ff9c7280aeee0936c8f64741981
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationhandleruntimeerror"></a>IDebugApplication::HandleRuntimeError
Приводит к блокировке текущего потока и отправляет уведомление об ошибке в IDE отладчик.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
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
 [in] Возникшей ошибки.  
  
 `pScriptSite`  
 [in] Узел сценария потока.  
  
 `pbra`  
 [out] Действие, выполняемое при отладчик возобновляет работу приложения.  
  
 `perra`  
 [out] Действие, выполняемое при отладчик возобновляет работу приложения, если имеется ошибка.  
  
 `pfCallOnScriptError`  
 [out] Флаг, который является `TRUE` Если обработчик должен вызывать `IActiveScriptSite::OnScriptError` метод.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 Этот метод вызывается обработчик языка в контексте потока, вызвавшего ошибку во время выполнения. Этот метод приводит к блокировке текущего потока и отправляет уведомление об ошибке, отправляемых в IDE отладчик. При возобновлении приложения отладчик интегрированной среды разработки, этот метод возвращает с выполняемое действие.  
  
> [!NOTE]
>  Во время сбоя во время выполнения, обработчик языка могут быть вызваны потока для выполнения таких задач, как перечислить кадры стека или вычисления выражений.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IDebugApplication](../../winscript/reference/idebugapplication-interface.md)   
 [Интерфейс IActiveScriptErrorDebug](../../winscript/reference/iactivescripterrordebug-interface.md)   
 [Iactivescriptsite —](../../winscript/reference/iactivescriptsite.md)   
 [Перечисление BREAKRESUMEACTION](../../winscript/reference/breakresumeaction-enumeration.md)   
 [Перечисление ERRORRESUMEACTION](../../winscript/reference/errorresumeaction-enumeration.md)