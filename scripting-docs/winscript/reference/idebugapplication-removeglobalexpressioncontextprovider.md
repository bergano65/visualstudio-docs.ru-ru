---
title: "IDebugApplication::RemoveGlobalExpressionContextProvider | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplication.RemoveGlobalExpressionContextProvider
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugApplication::RemoveGlobalExpressionContextProvider"
ms.assetid: ace638a3-ed34-4d20-8404-45c684aaaf1a
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplication::RemoveGlobalExpressionContextProvider
Удаляет глобальный поставщик контекста выражения из этого приложения.  
  
## Синтаксис  
  
```  
HRESULT RemoveGlobalExpressionContextProvider(  
   DWORD_PTR  dwCookie  
);  
```  
  
#### Параметры  
 `dwCookie`  
 \[in\] файл cookie, возвращенных методом `AddGlobalExpressionContextProvider` если глобальный поставщик контекста был добавлен.  
  
## Возвращаемое значение  
 Метод возвращает `HRESULT`.  Допустимые значения включают, но не ограничиваются см. в следующей таблице.  
  
|Значение|Описание|  
|--------------|--------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## Заметки  
 Метод `RemoveGlobalExpressionContextProvider` удаляет глобальный поставщик контекста выражения из этого приложения.  
  
## См. также  
 [IDebugApplication::AddGlobalExpressionContextProvider](../../winscript/reference/idebugapplication-addglobalexpressioncontextprovider.md)   
 [Интерфейс IDebugApplication](../../winscript/reference/idebugapplication-interface.md)