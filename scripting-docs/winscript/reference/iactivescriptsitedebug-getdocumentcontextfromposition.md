---
title: "IActiveScriptSiteDebug::GetDocumentContextFromPosition | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptSiteDebug.GetDocumentContextFromPosition
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptSiteDebug::GetDocumentContextFromPosition"
ms.assetid: ba5f7348-0107-4b12-b949-79a012476cf7
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptSiteDebug::GetDocumentContextFromPosition
Используемый обработчиком языка, чтобы делегировать `IDebugCodeContext::GetSourceContext`.  
  
## Синтаксис  
  
```  
HRESULT GetDocumentContextFromPosition(  
   DWORD_PTR                dwSourceContext,  
   ULONG                    uCharacterOffset,  
   ULONG                    uNumChars,  
   IDebugDocumentContext**  ppsc  
);  
```  
  
#### Параметры  
 `dwSourceContext`  
 \[in\] содержимое источника изменений в `ParseScriptText` или `AddScriptlet`.  
  
 `uCharacterOffset`  
 \[in\] смещение символа относительно начала блока или скрипта скрипта.  
  
 `uNumChars`  
 \[in\] количество знаков в этом контексте.  
  
 `ppsc`  
 \[out\] контекст документа, соответствующий данному диапазону позиции символа.  
  
## Возвращаемое значение  
 Метод возвращает `HRESULT`.  Допустимые значения включают, но не ограничиваются см. в следующей таблице.  
  
|Значение|Описание|  
|--------------|--------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## Заметки  
 Обработчики языка, использующих этот метод, чтобы делегировать `IDebugCodeContext::GetSourceContext`.  
  
## См. также  
 [Интерфейс IActiveScriptSiteDebug](../../winscript/reference/iactivescriptsitedebug-interface.md)