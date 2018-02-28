---
title: "IActiveScript::InterruptScriptThread | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IActiveScript.InterruptScriptThread
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_InterruptScriptThread
ms.assetid: 2304d035-6d39-4811-acd3-8a9640fdbef6
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ad717ee950dda4f0f0d7a14292f0f5f150ab4973
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptinterruptscriptthread"></a>IActiveScript::InterruptScriptThread
Прерывает выполнение выполняющийся поток скрипта (приемник событий, немедленное выполнение или вызов макроса). Этот метод можно использовать для завершения сценария (например, из бесконечного цикла). Может вызываться из потоков, отличной от base не входили в системе счисления с основанием выноски объектов узла или [iactivescriptsite —](../../winscript/reference/iactivescriptsite.md) метод.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT InterruptScriptThread(  
    SCRIPTTHREADID   stidThread,  // identifier of thread  
    const EXCEPINFO *pexcepinfo,  // receives error information  
    DWORD dwFlags  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `stidThread`  
 [in] Идентификатор потока для прерывания или один из следующих значений идентификаторов специальных потоков:  
  
|Значение|Значение|  
|-----------|-------------|  
|SCRIPTTHREADID_ALL|Все потоки. Прерывание применяется ко всем методам скрипт, выполняющиеся в настоящее время. Обратите внимание, что если вызывающий объект запрашивает отключен скрипт, далее сценариев событие вызывает код скрипта для повторного запуска путем вызова [IActiveScript::SetScriptState](../../winscript/reference/iactivescript-setscriptstate.md) метод с SCRIPTSTATE_DISCONNECTED или Установить флаг SCRIPTSTATE_INITIALIZED.|  
|SCRIPTTHREADID_BASE|Базовый поток; то есть был создан поток, в котором модуль создания скриптов.|  
|SCRIPTTHREADID_CURRENT|Текущий выполняемый поток.|  
  
 `pexcepinfo`  
 [in] Адрес `EXCEPINFO` структуру, содержащую сведения об ошибке, которая должна быть зарегистрирована в скрипте прерванных.  
  
 `dwFlags`  
 [in] Параметр флаги, связанные с прерывания. Допустимо одно из следующих значений.  
  
|Значение|Значение|  
|-----------|-------------|  
|SCRIPTINTERRUPT_DEBUG|Если поддерживается, введите отладчика обработчика скриптов в текущей точке выполнения скрипта.|  
|SCRIPTINTERRUPT_RAISEEXCEPTION|Если поддерживается языком обработчика скриптов, пусть скрипт обрабатывает исключение. В противном случае метод сценария прерывается и код ошибки возвращается в вызывающий объект; то есть средство событий источника или макрос вызова.|  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает одно из следующих значений:  
  
|Возвращаемое значение|Значение|  
|------------------|-------------|  
|`S_OK`|Выполнено.|  
|`E_INVALIDARG`|Недопустимый аргумент.|  
|`E_POINTER`|Указан недопустимый указатель.|  
|`E_UNEXPECTED`|Вызов не ожидалось (например, обработчик сценариев еще не загрузки или инициализации).|  
  
## <a name="see-also"></a>См. также  
 [IActiveScript](../../winscript/reference/iactivescript.md)