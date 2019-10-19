---
title: 'IDebugApplication:: Хандлерунтимиррор | Документация Майкрософт'
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
ms.openlocfilehash: 2fd4ba2b811cd6c4e38c10a0c68c5808f2c0870a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574322"
---
# <a name="idebugapplicationhandleruntimeerror"></a>IDebugApplication::HandleRuntimeError
Заставляет текущий поток блокировать и отправлять уведомление об ошибке в интегрированную среду разработки отладчика.  
  
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
 окне Возникшая ошибка.  
  
 `pScriptSite`  
 окне Сайт скрипта потока.  
  
 `pbra`  
 заполняет Действие, выполняемое при возобновлении работы отладчика приложением.  
  
 `perra`  
 заполняет Действие, выполняемое, когда отладчик возобновляет работу приложения при возникновении ошибки.  
  
 `pfCallOnScriptError`  
 заполняет Флаг, который `TRUE`, если обработчик должен вызвать метод `IActiveScriptSite::OnScriptError`.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|значения|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Заметки  
 Языковой механизм вызывает этот метод в контексте потока, который вызывает ошибку во время выполнения. Этот метод заставляет текущий поток блокировать и отправлять уведомление об ошибке в интегрированную среду разработки отладчика. При возобновлении работы приложения интегрированной средой разработки отладчика этот метод возвращает и выполняемое действие.  
  
> [!NOTE]
> Во время сбоя времени выполнения обработчик языка может вызываться потоком для выполнения таких задач, как перечисление кадров стека или вычисление выражений.  
  
## <a name="see-also"></a>См. также  
 @No__t_1 [интерфейса IDebugApplication](../../winscript/reference/idebugapplication-interface.md)  
 @No__t_1 [интерфейса иактивескриптеррордебуг](../../winscript/reference/iactivescripterrordebug-interface.md)  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)    
 @No__t_1 [перечисления BREAKRESUMEACTION](../../winscript/reference/breakresumeaction-enumeration.md)  
 [Перечисление ERRORRESUMEACTION](../../winscript/reference/errorresumeaction-enumeration.md)