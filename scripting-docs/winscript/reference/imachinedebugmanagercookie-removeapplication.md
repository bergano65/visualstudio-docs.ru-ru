---
title: "IMachineDebugManagerCookie::RemoveApplication | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IMachineDebugManagerCookie.RemoveApplication
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IMachineDebugManagerCookie::RemoveApplication"
ms.assetid: af8f4a52-ec5e-48fa-87de-234d5e6528d0
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IMachineDebugManagerCookie::RemoveApplication
Удаляет приложение из выполняющегося списка приложения.  
  
## Синтаксис  
  
```  
HRESULT RemoveApplication(  
   DWORD  dwDebugAppCookie,  
   DWORD  dwAppCookie  
);  
```  
  
#### Параметры  
 `dwDebugAppCookie`  
 \[in\] файл cookie, который определяет приложение отладки.  
  
 `dwAppCookie`  
 \[in\] файл cookie, когда приложение было добавитьо к списку приложения.  
  
## Возвращаемое значение  
 Метод возвращает `HRESULT`.  Допустимые значения включают, но не ограничиваются см. в следующей таблице.  
  
|Значение|Описание|  
|--------------|--------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## Заметки  
 Этот метод вызывается в процессе отладки диспетчер при `IProcessDebugManager::RemoveApplication` Позвонитьо.  
  
## См. также  
 [IMachineDebugManagerCookie::AddApplication](../../winscript/reference/imachinedebugmanagercookie-addapplication.md)   
 [Интерфейс IMachineDebugManagerCookie](../../winscript/reference/imachinedebugmanagercookie-interface.md)   
 [IProcessDebugManager::RemoveApplication](../../winscript/reference/iprocessdebugmanager-removeapplication.md)