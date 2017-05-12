---
title: "IDebugHelper::CreatePropertyBrowser | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugHelper.CreatePropertyBrowser
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugHelper::CreatePropertyBrowser"
ms.assetid: 2fa819cf-c7f7-4bd7-b018-ea33b804ba8f
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugHelper::CreatePropertyBrowser
Возвращает обозреватель свойств, который создает программу\-оболочку ВЕРСИЙ.  
  
## Синтаксис  
  
```  
HRESULT CreatePropertyBrowser(  
   VARIANT*                  pvar,  
   LPCOLESTR                 bstrName,  
   IDebugApplicationThread*  pdat,  
   IDebugProperty**          ppdob  
);  
```  
  
#### Параметры  
 `pvar`  
 \[in\] версия корня для просмотра.  
  
 `bstrName`  
 \[in\] имя, задаваемое корень.  
  
 `pdat`  
 \[in\] поток в которых для запроса свойства.  Если этот параметр имеет значение null, выстраивать не выполняется.  
  
 `ppdob`  
 \[out\] обозреватель свойств.  
  
## Возвращаемое значение  
 Метод возвращает `HRESULT`.  Допустимые значения включают, но не ограничиваются см. в следующей таблице.  
  
|Значение|Описание|  
|--------------|--------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## Заметки  
 Этот метод возвращает обозреватель свойств, который создает программу\-оболочку ВЕРСИЙ.  
  
## См. также  
 [IDebugHelper::CreatePropertyBrowserEx](../../winscript/reference/idebughelper-createpropertybrowserex.md)   
 [Интерфейс IDebugHelper](../../winscript/reference/idebughelper-interface.md)   
 [Интерфейс IDebugProperty](../../winscript/reference/idebugproperty-interface.md)