---
title: "IActiveScriptDebug::EnumCodeContextsOfPosition | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptDebug.EnumCodeContextsOfPosition
apilocation: jscript.dll
helpviewer_keywords: 
  - "IActiveScriptDebug::EnumCodeContextsOfPosition"
ms.assetid: 19f44420-bcc8-4c10-8c38-378d96044117
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptDebug::EnumCodeContextsOfPosition
Общий промежуточным узлом, чтобы делегировать метод `IDebugDocumentContext::EnumCodeContexts`.  
  
## Синтаксис  
  
```  
HRESULT EnumCodeContextsOfPosition(  
   DWORD_PTR                 dwSourceContext,  
   ULONG                     uCharacterOffset,  
   ULONG                     uNumChars,  
   IEnumDebugCodeContexts**  ppescc  
);  
```  
  
#### Параметры  
 `dwSourceContext`  
 \[in\] контекст источника изменений в `IActiveScriptParse::ParseScriptText` или `IActiveScriptParse::AddScriptlet`.  
  
 `uCharacterOffset`  
 \[in\] смещение символа относительно начала текст скрипта.  
  
 `uNumChars`  
 \[in\] количество знаков в этом контексте.  
  
 `ppescc`  
 \[out\] перечислитель контекстов кода в указанном диапазоне.  
  
## Возвращаемое значение  
 Метод возвращает `HRESULT`.  Допустимые значения включают, но не ограничиваются см. в следующей таблице.  
  
|Значение|Описание|  
|--------------|--------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## Заметки  
 Промежуточные узлы использующих этот метод, чтобы делегировать метод `IDebugDocumentContext::EnumCodeContexts`.  
  
## См. также  
 [Интерфейс IActiveScriptDebug](../../winscript/reference/iactivescriptdebug-interface.md)   
 [IDebugDocumentContext::EnumCodeContexts](../../winscript/reference/idebugdocumentcontext-enumcodecontexts.md)