---
title: IActiveScript::InterruptScriptThread | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.InterruptScriptThread
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_InterruptScriptThread
ms.assetid: 2304d035-6d39-4811-acd3-8a9640fdbef6
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d20847245e25ec6227bb043df3190a6db5f095d5
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2019
ms.locfileid: "54088937"
---
# <a name="iactivescriptinterruptscriptthread"></a>IActiveScript::InterruptScriptThread
Прерывает выполнение выполняющийся поток скрипта (приемник событий, немедленное выполнение или вызов макроса). Этот метод может использоваться для прерывания сценария (например, из бесконечного цикла). Он может вызываться из потоков не основной не входили в выноске отличные от базовых объектов узла или [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) метод.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT InterruptScriptThread(  
    SCRIPTTHREADID   stidThread,  // identifier of thread  
    const EXCEPINFO *pexcepinfo,  // receives error information  
    DWORD dwFlags  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `stidThread`  
 [in] Идентификатор потока для прерывания или один из следующих значений идентификатора специальный поток:  
  
|Значение|Значение|  
|-----------|-------------|  
|SCRIPTTHREADID_ALL|Все потоки. Прерывание применяется ко всем методам скрипта в настоящее время. Обратите внимание, что если вызывающая сторона запросила отключен скрипт, следующего сценария события вызывает код сценария для повторного запуска, вызвав [IActiveScript::SetScriptState](../../winscript/reference/iactivescript-setscriptstate.md) метод с SCRIPTSTATE_DISCONNECTED или Установлен флаг SCRIPTSTATE_INITIALIZED.|  
|SCRIPTTHREADID_BASE|Базовый поток; то есть был создан поток, в котором обработчик скриптов.|  
|SCRIPTTHREADID_CURRENT|Текущим выполняемым потоком.|  
  
 `pexcepinfo`  
 [in] Адрес `EXCEPINFO` структуру, содержащую сведения об ошибке, который должен быть передан в прерванных скрипт.  
  
 `dwFlags`  
 [in] Флаги параметров, связанных с прерывания. Допустимо одно из следующих значений.  
  
|Значение|Значение|  
|-----------|-------------|  
|SCRIPTINTERRUPT_DEBUG|Если поддерживается, введите отладчика обработчика скриптов в текущей точке выполнения скрипта.|  
|SCRIPTINTERRUPT_RAISEEXCEPTION|Если поддерживается язык обработчика скриптов, позвольте сценарию обработки исключения. В противном случае метод сценария прерывается и код ошибки возвращается вызывающему объекту; то есть средство событий макроса или источника вызова.|  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает одно из следующих значений:  
  
|Возвращаемое значение|Значение|  
|------------------|-------------|  
|`S_OK`|Выполнено.|  
|`E_INVALIDARG`|Аргумент был недопустимым.|  
|`E_POINTER`|Указан недопустимый указатель.|  
|`E_UNEXPECTED`|Вызов не ожидался (например, обработчик скриптов еще не была загрузки или инициализации).|  
  
## <a name="see-also"></a>См. также  
 [IActiveScript](../../winscript/reference/iactivescript.md)