---
title: "IActiveScriptSiteWindow::EnableModeless | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptSiteWindow.EnableModeless
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptSiteWindow_EnableModeless"
ms.assetid: 83fe4f62-8e97-4f03-bc6f-d90aa888657d
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptSiteWindow::EnableModeless
Вызывает основное приложение включить или отключить свое главное окно, немодальное все диалоговые окна.  
  
## Синтаксис  
  
```  
HRESULT EnableModeless(  
    BOOL fEnable  // enable flag  
);  
```  
  
#### Параметры  
 `fEnable`  
 \[in\] пометьте, если `TRUE`, включает главного окна и диалоговые окна или немодального, если `FALSE`, запрещает их.  
  
## Возвращаемое значение  
 Возвращает `S_ОК`, если успешно или `E_FAIL`, если произошла ошибка.  
  
## Заметки  
 Этот метод аналогичен методу `IOleInPlaceFrame::EnableModeless`.  
  
 Вызовы к этому методу могут быть вложенными.  
  
## См. также  
 [IActiveScriptSiteWindow](../../winscript/reference/iactivescriptsitewindow.md)