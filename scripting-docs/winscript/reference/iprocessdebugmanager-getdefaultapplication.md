---
title: "IProcessDebugManager::GetDefaultApplication | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IProcessDebugManager.GetDefaultApplication
apilocation: pdm.dll
helpviewer_keywords: 
  - "IProcessDebugManager::GetDefaultApplication"
ms.assetid: 6c991faa-ea40-4d18-a1b8-6e7d0de6dd43
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IProcessDebugManager::GetDefaultApplication
Возвращает объект по умолчанию приложения для текущего процесса.  
  
## Синтаксис  
  
```  
HRESULT GetDefaultApplication(  
   IDebugApplication**  ppda  
);  
```  
  
#### Параметры  
 `ppda`  
 \[out\] объект приложения отладки для этого приложения.  
  
## Возвращаемое значение  
 Метод возвращает `HRESULT`.  Допустимые значения включают, но не ограничиваются см. в следующей таблице.  
  
|Значение|Описание|  
|--------------|--------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## Заметки  
 Этот метод создает новый объект отладки приложения и добавляет его в список текущих приложения, если требуемый.  
  
 Обработчики языка должны использовать приложение, задаваемый методом `GetDefaultApplication` если они выполняются на узле, который не предоставляет приложение.  
  
## См. также  
 [Интерфейс IProcessDebugManager](../../winscript/reference/iprocessdebugmanager-interface.md)