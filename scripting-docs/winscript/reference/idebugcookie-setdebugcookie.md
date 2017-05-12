---
title: "IDebugCookie::SetDebugCookie | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugCookie.SetDebugCookie
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugCookie::SetDebugCookie"
ms.assetid: 9cba3b05-ff81-4fb0-9382-e9338cb9192d
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugCookie::SetDebugCookie
Задает файл cookie приложения отладки.  
  
## Синтаксис  
  
```  
HRESULT SetDebugCookie(  
   DWORD  dwDebugAppCookie  
);  
```  
  
#### Параметры  
 `dwDebugAppCookie`  
 \[in\] файл cookie, который определяет приложение отладки.  
  
## Возвращаемое значение  
 Метод возвращает `HRESULT`.  Допустимые значения включают, но не ограничиваются см. в следующей таблице.  
  
|Значение|Описание|  
|--------------|--------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## Заметки  
 Этот метод устанавливает файл cookie отладки приложения, который позволяет нескольким отладчика для вложение в процесс.  
  
## См. также  
 [Интерфейс IDebugCookie](../../winscript/reference/idebugcookie-interface.md)