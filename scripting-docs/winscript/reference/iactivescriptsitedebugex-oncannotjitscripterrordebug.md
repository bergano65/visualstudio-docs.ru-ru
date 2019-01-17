---
title: IActiveScriptSiteDebugEx::OnCanNotJITScriptErrorDebug | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 70dd250359d52ae0929fb5fb2c60087f66af2160
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2019
ms.locfileid: "54095125"
---
# <a name="iactivescriptsitedebugexoncannotjitscripterrordebug"></a>IActiveScriptSiteDebugEx::OnCanNotJITScriptErrorDebug
Информирует приложение о ошибки времени выполнения скрипта при процесс отладки Manager не удается найти в отладчик сценариев Just In Time.  
  
 Чтобы реализовать отладчика в главном приложении, необходимо обработать [IActiveScriptSiteDebug::OnScriptErrorDebug](../../winscript/reference/iactivescriptsitedebug-onscripterrordebug.md). На основании действий пользователя, узел можно подключить отладчик и возвращаемое, или запуск отладчика в OnScriptErrorDebug `pfEnterDebugger` параметра. Также следует реализовать этот интерфейс, чтобы получать уведомления об ошибке времени выполнения, даже при наличии не внешние отладчики, которые могут обрабатываться диспетчер отладки процессов.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT OnCanNotJITScriptErrorDebug(  
   IActiveScriptErrorDebug*  pErrorDebug  
   BOOL *pfCallOnScriptErrorWhenContinuing  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pErrorDebug`  
 [in] Произошла ошибка во время выполнения.  
  
 `pfCallOnScriptErrorWhenContinuingt`  
 [out] Следует ли вызывать [IActiveScriptSiteDebug::OnScriptErrorDebug](../../winscript/reference/iactivescriptsitedebug-onscripterrordebug.md) Если пользователь решил продолжить без отладки.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Метод возвращает `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание:|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 Также следует реализовать этот интерфейс, чтобы получать уведомления.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IActiveScriptSiteDebugEx](../../winscript/reference/iactivescriptsitedebugex-interface.md)