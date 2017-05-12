---
title: "IProcessDebugManager::RemoveApplication | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IProcessDebugManager.RemoveApplication
apilocation: pdm.dll
helpviewer_keywords: 
  - "IProcessDebugManager::RemoveApplication"
ms.assetid: 334e869d-81ae-4d30-9e89-89763ad4f184
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IProcessDebugManager::RemoveApplication
Удаляет приложение из выполняющегося списка приложения.  
  
## Синтаксис  
  
```  
HRESULT RemoveApplication(  
   DWORD  dwAppCookie  
);  
```  
  
#### Параметры  
 `dwAppCookie`  
 \[in\] файл cookie, `IProcessDebugManager::AddApplication`, когда приложение было добавитьо к списку приложения.  
  
## Возвращаемое значение  
 Метод возвращает `HRESULT`.  Допустимые значения включают, но не ограничиваются см. в следующей таблице.  
  
|Значение|Описание|  
|--------------|--------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## Заметки  
 Этот метод удаляет приложение из выполняющегося списка приложения.  
  
## См. также  
 [IProcessDebugManager::AddApplication](../../winscript/reference/iprocessdebugmanager-addapplication.md)   
 [Интерфейс IProcessDebugManager](../../winscript/reference/iprocessdebugmanager-interface.md)