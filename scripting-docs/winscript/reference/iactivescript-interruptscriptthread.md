---
title: 'IActiveScript:: InterruptScriptThread | Документация Майкрософт'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: a436f973df05b945c0939f3a593640f567774277
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577268"
---
# <a name="iactivescriptinterruptscriptthread"></a>IActiveScript::InterruptScriptThread
Прерывает выполнение выполняющегося потока скрипта (приемника событий, немедленное выполнение или вызов макроса). Этот метод можно использовать для завершения сценария, который зависает (например, в бесконечном цикле). Его можно вызывать из небазовых потоков без создания базового вызова для размещения объектов или метода [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) .  
  
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
 окне Идентификатор потока для прерывания или одно из следующих специальных значений идентификатора потока:  
  
|значения|Смысл|  
|-----------|-------------|  
|SCRIPTTHREADID_ALL|Все потоки. Это прерывание применяется ко всем выполняемым в настоящее время методам сценариев. Обратите внимание, что если вызывающий объект не запросил отсоединение скрипта, следующее событие в скрипте вызывает повторное выполнение кода сценария с помощью вызова метода [IActiveScript:: SetScriptState](../../winscript/reference/iactivescript-setscriptstate.md) с флагом SCRIPTSTATE_DISCONNECTED или SCRIPTSTATE_INITIALIZED параметр.|  
|SCRIPTTHREADID_BASE|Базовый поток; то есть поток, в котором был создан экземпляр обработчика сценариев.|  
|SCRIPTTHREADID_CURRENT|Выполняющийся в данный момент поток.|  
  
 `pexcepinfo`  
 окне Адрес структуры `EXCEPINFO`, содержащей сведения об ошибке, которые должны быть переданы в прерванный скрипт.  
  
 `dwFlags`  
 окне Флаги параметров, связанные с прерыванием. Допустимо одно из следующих значений.  
  
|значения|Смысл|  
|-----------|-------------|  
|SCRIPTINTERRUPT_DEBUG|Если поддерживается, введите отладчик обработчика скриптов в текущей точке выполнения скрипта.|  
|SCRIPTINTERRUPT_RAISEEXCEPTION|Если поддерживается языком обработчика скриптов, можно разрешить сценарию обработку исключения. В противном случае метод скрипта прерывается и код ошибки возвращается вызывающему объекту. то есть источник события или средство вызова макроса.|  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает одно из следующих значений:  
  
|Возвращаемое значение|Смысл|  
|------------------|-------------|  
|`S_OK`|Выполнено.|  
|`E_INVALIDARG`|Недопустимый аргумент.|  
|`E_POINTER`|Указан недопустимый указатель.|  
|`E_UNEXPECTED`|Вызов не ожидался (например, обработчик скриптов еще не загружен или не инициализирован).|  
  
## <a name="see-also"></a>См. также  
 [IActiveScript](../../winscript/reference/iactivescript.md)