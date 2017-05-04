---
title: "IPerPropertyBrowsing2::GetDisplayString | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IPerPropertyBrowsing2.GetDisplayString
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IPerPropertyBrowsing2::GetDisplayString"
ms.assetid: 8f75c6a9-86a9-4e2d-8cb4-74e7b1c0a524
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IPerPropertyBrowsing2::GetDisplayString
Получает строку к типам отображения, по существу не может просматриваться возвращаемый текст, описывающий свойство имя и могут отображаться в пользовательском интерфейсе вызывающего объекта.  
  
## Синтаксис  
  
```  
HRESULT GetDisplayString(  
   DISPID  dispid,  
   BSTR*  pBstr  
);  
```  
  
#### Параметры  
 `dispid`  
 \[in\] идентификатор пошлите свойства отображаемое имя которого запрошено.  
  
 `pBstr`  
 \[out\] указатель на `BSTR`, содержащее отображаемое имя для свойства, определенного `dispID`.  
  
## Возвращаемое значение  
 Возвращает допустимое `HRESULT`, обычно `S_ОК`.  
  
## Заметки  
 Возвращаемая строка является недопустимым значением свойства.  Просто отображать строки свойства.  
  
## См. также  
 [Интерфейс IPerPropertyBrowsing2](../../winscript/reference/iperpropertybrowsing2-interface-1.md)