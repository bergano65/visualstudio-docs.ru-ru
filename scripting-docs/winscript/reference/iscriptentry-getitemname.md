---
title: "IScriptEntry::GetItemName | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptEntry.GetItemName
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptEntry::GetItemName"
ms.assetid: 8f2562f1-8231-4a39-ad79-074f9ec3d403
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IScriptEntry::GetItemName
Возвращает имя элемента, указывающее объект `IScriptEntry`.  
  
## Синтаксис  
  
```  
HRESULT GetItemName(  
   BSTR               *pbstr  
);  
```  
  
#### Параметры  
 `pbstr`  
 \[out\] адрес буфера, содержащий имя элемента.  Имя элемента используется узелом, чтобы идентифицировать запись.  
  
## Возвращаемое значение  
 Объект `HRESULT`.  Допустимые значения включают, но не ограничиваются см. в следующей таблице.  
  
|Значение|Описание|  
|--------------|--------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## Заметки  
 Для `IScriptScriptlet` возражает будет задано имя элемента с помощью [IActiveScriptAuthor::AddScriptlet](../../winscript/reference/iactivescriptauthor-addscriptlet.md).  Для других интерфейсов, имеет имя элемента с помощью [IScriptEntry::SetItemName](../../winscript/reference/iscriptentry-setitemname.md).  
  
## См. также  
 [Интерфейс IScriptEntry](../../winscript/reference/iscriptentry-interface.md)