---
title: "IActiveScriptSiteDebug::OnScriptErrorDebug | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptSiteDebug.OnScriptErrorDebug
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptSiteDebug::OnScriptErrorDebug"
ms.assetid: 87f201da-36eb-49a2-b000-e1e1e8c4cdb7
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptSiteDebug::OnScriptErrorDebug
Обеспечивает промежуточный узел, чтобы указать способ обработки ошибок во время выполнения.  
  
## Синтаксис  
  
```  
HRESULT OnScriptErrorDebug(  
   IActiveScriptErrorDebug*  pErrorDebug,  
   BOOL*                     pfEnterDebugger,  
   BOOL*                     pfCallOnScriptErrorWhenContinuing  
);  
```  
  
#### Параметры  
 `pErrorDebug`  
 \[in\] ошибка, произошедшая во время выполнения  
  
 `pfEnterDebugger`  
 \[out\] показывает пометьте передать ошибку, следует ли отладчику, чтобы сделать JIT\-отладка.  
  
 `pfCallOnScriptErrorWhenContinuing`  
 \[out\] показывает пометьте, следует ли вызывать `IActiveScriptSite::OnScriptError`, когда пользователь решит продолжить без отладки.  
  
## Возвращаемое значение  
 Метод возвращает `HRESULT`.  Допустимые значения включают, но не ограничиваются значению в следующей таблице.  
  
|Значение|Описание|  
|--------------|--------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## Заметки  
 Промежуточный узел может использовать этот метод, чтобы указать способ обработки ошибок во время выполнения.  
  
## См. также  
 [Интерфейс IActiveScriptSiteDebug](../../winscript/reference/iactivescriptsitedebug-interface.md)