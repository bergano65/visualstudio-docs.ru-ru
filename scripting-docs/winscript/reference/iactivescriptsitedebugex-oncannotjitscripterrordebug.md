---
title: 'Иактивескриптситедебужекс:: Онканнотжитскриптеррордебуг | Документация Майкрософт'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSiteDebugEx.OnCanNotJITScriptErrorDebug
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSiteDebugEx::OnCanNotJITScriptErrorDebug
ms.assetid: 83f81476-bf12-47f2-897d-1d37d21137d4
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7358d2b372f0801b8c45816e1fc36018b37799b2
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572178"
---
# <a name="iactivescriptsitedebugexoncannotjitscripterrordebug"></a>IActiveScriptSiteDebugEx::OnCanNotJITScriptErrorDebug
Информирует узел об ошибке времени выполнения сценария, когда диспетчер отладки процессов не находит JIT-отладчик скриптов.  
  
 Чтобы реализовать отладчик на узле, необходимо выполнить обработку [IActiveScriptSiteDebug:: онскриптеррордебуг](../../winscript/reference/iactivescriptsitedebug-onscripterrordebug.md). В зависимости от действия пользователя узел может либо присоединить отладчик и вернуть, либо вернуть запуск отладчика в параметре `pfEnterDebugger` Онскриптеррордебуг. Также следует реализовать этот интерфейс для получения уведомления об ошибке времени выполнения, даже если нет внешних отладчиков, которые могут быть интерпретированы диспетчером отладки процессов.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT OnCanNotJITScriptErrorDebug(  
   IActiveScriptErrorDebug*  pErrorDebug  
   BOOL *pfCallOnScriptErrorWhenContinuing  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pErrorDebug`  
 окне Возникшая ошибка времени выполнения.  
  
 `pfCallOnScriptErrorWhenContinuingt`  
 заполняет Следует ли вызывать [IActiveScriptSiteDebug:: онскриптеррордебуг](../../winscript/reference/iactivescriptsitedebug-onscripterrordebug.md) , если пользователь решил продолжить работу без отладки.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|значения|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Заметки  
 Также необходимо реализовать этот интерфейс для получения уведомления.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IActiveScriptSiteDebugEx](../../winscript/reference/iactivescriptsitedebugex-interface.md)