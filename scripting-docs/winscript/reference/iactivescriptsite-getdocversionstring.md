---
title: "IActiveScriptSite::GetDocVersionString | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptSite.GetDocVersionString
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptSite_GetDocVersionString"
ms.assetid: ab3f892d-06d3-4cb5-9ea5-20c4a1e518cd
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptSite::GetDocVersionString
Получает основное приложение\- указанная строка, однозначно определяющее версию текущего документа.  Если связанный документ был изменен вне области скрипта Windows \(как в случае страницы HTML редактируемой в данный момент с блокнотом\), то обработчик скриптов может сохранить и сохранение состоянием принуждая recompile в следующий раз при загрузке скрипт.  
  
## Синтаксис  
  
```  
HRESULT GetDocVersionString(  
    BSTR *pbstrVersionString  // address of document version string  
);  
```  
  
#### Параметры  
 `pstrVersionString`  
 \[out\] адрес основного приложение\- указанной строки версии документа.  
  
## Возвращаемое значение  
 Возвращает `S_ОК`, если успешно или `E_NOTIMPL`, если этот метод не поддерживается.  
  
## Заметки  
 Если `E_NOTIMPL` возвращается, то обработчик скриптов предположим, что скрипт в синхронизации с документом.  
  
## См. также  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)