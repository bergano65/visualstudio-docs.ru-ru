---
title: "IActiveScriptSiteDebug::GetApplication | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptSiteDebug.GetApplication
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptSiteDebug::GetApplication"
ms.assetid: 4400f1b1-3108-4a71-b1f1-43586fe1227c
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptSiteDebug::GetApplication
Возвращает объект приложения отладки, связанный с этим сайтом скрипта.  
  
## Синтаксис  
  
```  
HRESULT GetApplication(  
   IDebugApplication**  ppda  
);  
```  
  
#### Параметры  
 `ppda`  
 \[out\] указатель на объект, связанный с сайтом приложения для отладки скрипта.  
  
## Возвращаемое значение  
 Метод возвращает `HRESULT`.  Допустимые значения включают, но не ограничиваются см. в следующей таблице.  
  
|Значение|Описание|  
|--------------|--------------|  
|`S_OK`|Метод успешно выполнен.|  
|`E_NOTIMPL`|Основное приложение не поддерживает отладку.|  
  
## Заметки  
 Метод `GetApplication` предоставляет способ для промежуточного узла указывать объект приложения, к которому принадлежит каждый скрипт.  Обработчики скриптов должны пытаться вызывать этот метод, чтобы получить их, содержащий приложение и курорт к `IProcessDebugManager::GetDefaultApplication` если это произойдет сбой.  
  
## См. также  
 [Интерфейс IActiveScriptSiteDebug](../../winscript/reference/iactivescriptsitedebug-interface.md)   
 [IProcessDebugManager::GetDefaultApplication](../../winscript/reference/iprocessdebugmanager-getdefaultapplication.md)