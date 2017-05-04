---
title: "IObjectIdentity::IsEqualObject | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IObjectIdentity.IsEqualObject
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IsEqualObject — метод"
ms.assetid: 78c5c5c2-d299-4036-986c-7c1d87cbe7cd
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IObjectIdentity::IsEqualObject
Определяет, является ли объект равен текущему объекту.  
  
## Синтаксис  
  
```  
HRESULT IsEqualObject(  
  IUnknown*  punk  
);  
```  
  
#### Параметры  
 `punk`  
 \[in\] адрес объекта, который требуется сравнить с текущим объектом.  
  
## Возвращаемое значение  
 Метод возвращает `HRESULT`.  Допустимые значения включают, но не ограничиваются см. в следующей таблице.  
  
|Значение|Описание|  
|--------------|--------------|  
|`S_OK`|Объекты равны.|  
|`S_FALSE`|Объекты не равны.|  
  
## Заметки  
 Реализация метода `IsEqualObject` должна возвращать `S_ОК`, только если объекты совпадают.  
  
## См. также  
 [Интерфейс IObjectIdentity](../../winscript/reference/iobjectidentity-interface.md)