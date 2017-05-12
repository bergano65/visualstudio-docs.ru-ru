---
title: "IActiveScript::Close | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScript.Close
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScript_Close"
ms.assetid: cc7dd63b-1d7e-410a-857b-09ea3aade275
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# IActiveScript::Close
Вызывает обработчик скриптов, чтобы прервать любой текущий загруженный скрипт, сохранить его состояние и освобождение все указатели интерфейса его другим объектам, поэтому вставка состояние закрыть.  Приемники событий, немедленно исполненное текста сценария и вызовы макроса, которые уже выполняется завершены перед изменениями состояния \(использованием [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md) отменить выполняющийся поток сценария\).  Этот метод следует вызывать прежде, чем создание основным приложением интерфейс освобождение, чтобы предотвратить ошибки циклических ссылок.  
  
## Синтаксис  
  
```  
HRESULT Close(void);  
```  
  
## Возвращаемое значение  
 Возвращать одно из следующих значений:  
  
|Значение|Значение|  
|--------------|--------------|  
|`S_OK`|Успех.|  
|`E_UNEXPECTED`|Вызов не ожидался \(например, обработчик скриптов уже находился в состоянии закрыть\).|  
|`OLESCRIPT_S_PENDING`|Метод был поставлен в очередь успешно, но состояние не изменилось.  При изменениях состояния, сайт вызываться обратно в методе [IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md).|  
|`S_FALSE`|Метод выполнен успешно, но скрипт уже были закрытьы.|  
  
## См. также  
 [IActiveScript](../../winscript/reference/iactivescript.md)