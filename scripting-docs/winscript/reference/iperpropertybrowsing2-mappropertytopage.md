---
title: "IPerPropertyBrowsing2::MapPropertyToPage | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IPerPropertyBrowsing2.MapPropertyToPage
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IPerPropertyBrowsing2::MapPropertyToPage"
ms.assetid: e6418a8e-500b-42e1-9b5a-52e6f7567f99
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IPerPropertyBrowsing2::MapPropertyToPage
Возвращает идентификатор CLSID страницы свойств, которые можно использовать, чтобы редактировать это свойство.  
  
## Синтаксис  
  
```  
HRESULT MapPropertyToPage(  
   DISPID  dispid,  
   CLSID*  pClsidPropPage  
);  
```  
  
#### Параметры  
 `dispid`  
 \[in\] пошлите идентификатор свойства.  
  
 `pClsidPropPage`  
 \[out\] указатель на идентификатор CLSID, определяющий страницу свойств, связанное со свойством.  Если этот метод завершается ошибкой, \*`pClsidPropPage` установлено в CLSID\_NULL.  
  
## Возвращаемое значение  
 Возвращает допустимое `HRESULT`, обычно `S_ОК`.  
  
## См. также  
 [Интерфейс IPerPropertyBrowsing2](../../winscript/reference/iperpropertybrowsing2-interface-1.md)