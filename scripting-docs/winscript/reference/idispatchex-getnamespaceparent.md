---
title: "IDispatchEx::GetNameSpaceParent | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDispatchEx.GetNameSpaceParent
apilocation: scrobj.dll
helpviewer_keywords: 
  - "GetNameSpaceParent — метод"
ms.assetid: 0b077d39-2fd6-4390-8cd5-128d9b8dc90c
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDispatchEx::GetNameSpaceParent
Извлекает интерфейс для пространства имен родительского объекта.  
  
## Синтаксис  
  
```  
HRESULT GetNameSpaceParent(  
   IUnknown **ppunk  
);  
```  
  
#### Параметры  
 `ppunk`  
 Адрес указателя интерфейса `IUnknown`, который возвращает интерфейс родительского узла пространства имен.  
  
## Возвращаемое значение  
 Возвращает `S_ОК`, если успешно или OLE\- указанный код ошибки, в противном случае.  
  
## См. также  
 [Интерфейс IDispatchEx](../../winscript/reference/idispatchex-interface.md)