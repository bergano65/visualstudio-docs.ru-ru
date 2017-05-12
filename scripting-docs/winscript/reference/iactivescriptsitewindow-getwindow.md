---
title: "IActiveScriptSiteWindow::GetWindow | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptSiteWindow.GetWindow
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptSiteWindow_GetWindow"
ms.assetid: 6284e38c-9dfb-4d69-903d-f243f78c0331
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptSiteWindow::GetWindow
Получает дескриптор для окна, которое может действовать в качестве владельца контекстного меню окна, обработчик скриптов должен отображаться.  
  
## Синтаксис  
  
```  
HRESULT GetWindow(  
    HWND *phwnd  // address of variable for window handle  
);  
```  
  
#### Параметры  
 `phwnd`  
 \[out\] адрес переменной, которая получает дескриптор окна.  
  
## Возвращаемое значение  
 Возвращает `S_ОК`, если успешно или `E_FAIL`, если произошла ошибка.  
  
## Заметки  
 Этот метод сходен с методом `IOleWindow::GetWindow`.  
  
## См. также  
 [IActiveScriptSiteWindow](../../winscript/reference/iactivescriptsitewindow.md)