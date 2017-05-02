---
title: "IActiveScriptAuthor::AddTypeLib | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptAuthor.AddTypeLib
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptAuthor::AddTypeLib"
ms.assetid: d6696547-3eb5-4f31-9c5c-60aa29b6f083
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IActiveScriptAuthor::AddTypeLib
Добавляет библиотеки типов в пространстве имен для скрипта.  
  
## Синтаксис  
  
```  
HRESULT AddTypeLib(  
   REFGUID   rguidTypeLib,  
   DWORD     dwMajor,  
   DWORD     dwMinor,  
   DWORD     dwFlags  
);  
```  
  
#### Параметры  
 `rguidTypeLib`  
 \[in\] идентификатор CLSID \(идентификатор класса\) библиотеки типов для добавления.  
  
 `dwMajor`  
 \[in\] основной номер версии.  
  
 `dwMinor`  
 \[in\] дополнительный номер версии.  
  
 `dwFlags`  
 \[in\] Не используется.  
  
## Возвращаемое значение  
 Объект `HRESULT`.  Допустимые значения включают, но не ограничиваются см. в следующей таблице.  
  
|Значение|Описание|  
|--------------|--------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## Заметки  
 Этот метод вызывает `LoadTypeLib` чтобы загрузить библиотеку типов.  В случае успешного выполнения этом вызовы метода `IActiveScriptAuthor::AddNamedItem` для добавления сведений о типе.  
  
## См. также  
 [Интерфейс IActiveScriptAuthor](../../winscript/reference/iactivescriptauthor-interface.md)   
 [IActiveScriptAuthor::AddNamedItem](../../winscript/reference/iactivescriptauthor-addnameditem.md)   
 [LoadTypeLib](http://msdn.microsoft.com/ru-ru/155b48e5-5438-409e-9342-630a6a500f60)