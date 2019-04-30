---
title: IActiveScriptSiteDebugEx::OnCanNotJITScriptErrorDebug | Документация Майкрософт
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
ms.openlocfilehash: 4c643478da37b5a66c22b201ef8f8248df02e4ec
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62992341"
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
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 Также следует реализовать этот интерфейс, чтобы получать уведомления.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IActiveScriptSiteDebugEx](../../winscript/reference/iactivescriptsitedebugex-interface.md)