---
title: "IDebugHelper::CreatePropertyBrowserEx | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugHelper.CreatePropertyBrowserEx
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugHelper::CreatePropertyBrowserEx"
ms.assetid: 87ad322f-09da-4ce8-bb68-0b0bbeec645b
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugHelper::CreatePropertyBrowserEx
Возвращает обозреватель свойств, который создает программу\-оболочку ВАРИАНТ и для пользовательского преобразования РАЗЛИЧНЫХ значений или VARTYPE печатает к строкам.  
  
## Синтаксис  
  
```  
HRESULT CreatePropertyBrowserEx(  
   VARIANT*                  pvar,  
   LPCOLESTR                 bstrName,  
   IDebugApplicationThread*  pdat,  
   IDebugFormatter*          pdf,  
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
  
 `pdf`  
 \[in\] возразите, который предоставляет настраиваемое форматирование для вариантов.  
  
 `ppdob`  
 \[out\] обозреватель свойств.  
  
## Возвращаемое значение  
 Метод возвращает `HRESULT`.  Допустимые значения включают, но не ограничиваются см. в следующей таблице.  
  
|Значение|Описание|  
|--------------|--------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## Заметки  
 Этот метод возвращает обозреватель свойств, который создает программу\-оболочку ВАРИАНТ и для пользовательского преобразования РАЗЛИЧНЫХ значений или VARTYPE печатает к строкам.  
  
## См. также  
 [IDebugHelper::CreatePropertyBrowser](../../winscript/reference/idebughelper-createpropertybrowser.md)   
 [Интерфейс IDebugHelper](../../winscript/reference/idebughelper-interface.md)   
 [Интерфейс IDebugProperty](../../winscript/reference/idebugproperty-interface.md)