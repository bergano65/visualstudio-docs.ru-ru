---
title: "IPerPropertyBrowsing2::GetPredefinedStrings | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IPerPropertyBrowsing2.GetPredefinedStrings
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IPerPropertyBrowsing2::GetPredefinedStrings"
ms.assetid: d2fa30f7-a566-4dbd-8b47-ffdc00419771
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IPerPropertyBrowsing2::GetPredefinedStrings
Позволяет вызывающему объекту заполнить список с подсчитанным массив указателей строки, представляющие возможные значения этого свойства.  
  
## Синтаксис  
  
```  
HRESULT GetPredefinedStrings(  
   DISPID  dispid,  
   CALPOLESTR*  pCaStrings,  
   CADWORD*  pCaCookies  
);  
```  
  
#### Параметры  
 `dispid`  
 \[in\] идентификатор пошлите свойства, для которого вызывающий объект запрашивает список строк.  
  
 `pCaStrings`  
 \[out\] указатель на абонент\- выбранной, подсчитанной структуру массива, которая содержит количество элементов и адрес метод\- выбранного массива указателей строки.  Если метод завершается ошибкой, память не выделитьа, а не определены содержимое структуры.  
  
 `pCaCookies`  
 \[out\] указатель на абонент\- выбранной, подсчитанной структуру массива, которая содержит количество элементов массива и адрес метод\- выбранного типа DWORD.  Если метод завершается ошибкой, память не выделитьа, а не определены содержимое структуры.  
  
## Возвращаемое значение  
 Возвращает допустимое `HRESULT`, обычно `S_ОК`.  
  
## См. также  
 [Интерфейс IPerPropertyBrowsing2](../../winscript/reference/iperpropertybrowsing2-interface-1.md)