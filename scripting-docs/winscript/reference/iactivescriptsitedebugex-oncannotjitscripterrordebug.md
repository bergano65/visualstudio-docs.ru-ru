---
title: "IActiveScriptSiteDebugEx::OnCanNotJITScriptErrorDebug | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptSiteDebugEx.OnCanNotJITScriptErrorDebug
apilocation: scrobj.dll
helpviewer_keywords: IActiveScriptSiteDebugEx::OnCanNotJITScriptErrorDebug
ms.assetid: 83f81476-bf12-47f2-897d-1d37d21137d4
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e428f12b3d199603ac341a5e069fcc5ce5d36f93
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptsitedebugexoncannotjitscripterrordebug"></a>IActiveScriptSiteDebugEx::OnCanNotJITScriptErrorDebug
Сообщает о том, что ведущее приложение о ошибку во время выполнения сценария при процесс отладки Manager не удается найти только раз в отладчик сценариев.  
  
 Чтобы реализовать отладчик на узле, должен обрабатывать [IActiveScriptSiteDebug::OnScriptErrorDebug](../../winscript/reference/iactivescriptsitedebug-onscripterrordebug.md). На основании действий пользователя, узел можно подключить отладчик и вернет, или запуск отладчика в OnScriptErrorDebug `pfEnterDebugger` параметра. Также требуется реализовать этот интерфейс, чтобы получать уведомления об ошибке времени выполнения, даже при наличии не внешних отладчиков, которые могут обрабатываться диспетчером отладки процесса.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
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
 Также требуется реализовать этот интерфейс, чтобы получить уведомление.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IActiveScriptSiteDebugEx](../../winscript/reference/iactivescriptsitedebugex-interface.md)