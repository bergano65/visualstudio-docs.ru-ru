---
title: "IScriptEntry::SetItemName | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptEntry.SetItemName
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptEntry::SetItemName"
ms.assetid: 9551a7ec-38f8-466a-9722-09367763f380
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# IScriptEntry::SetItemName
Задает имя элемента, указывающее объект `IScriptEntry`.  
  
## Синтаксис  
  
```  
HRESULT SetItemName(  
   LPCOLESTR          psz  
);  
```  
  
#### Параметры  
 `psz`  
 \[in\] адрес буфера, содержащий имя элемента.  Имя элемента используется узелом, чтобы идентифицировать запись.  
  
## Возвращаемое значение  
 Объект `HRESULT`.  Допустимые значения включают, но не ограничиваются см. в следующей таблице.  
  
|Значение|Описание|  
|--------------|--------------|  
|`S_OK`|Метод успешно выполнен.|  
|`E_FAIL`|Метод выполнен успешно.|  
  
## Заметки  
 Для объектов `IScriptEntry`, этот метод возвращает `S_ОК`.  
  
 Для объектов `IScriptScriptlet` \(которые являются производными от `IScriptEntry`\), этот метод возвращает `E_FAIL`.  Для объектов `IScriptScriptlet`, имя элемента устанавливается [IActiveScriptAuthor::AddScriptlet](../../winscript/reference/iactivescriptauthor-addscriptlet.md) и не может быть изменитьо.  
  
## См. также  
 [Интерфейс IScriptEntry](../../winscript/reference/iscriptentry-interface.md)   
 [IScriptEntry::GetItemName](../../winscript/reference/iscriptentry-getitemname.md)