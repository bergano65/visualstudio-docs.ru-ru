---
title: "IActiveScriptSiteWindow | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptSiteWindow — интерфейс"
ms.assetid: 96d5c493-2c0b-47e2-848b-4a8dacdcd65c
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptSiteWindow
Этот интерфейс реализуется узлами, которые поддерживают пользовательский интерфейс на одном объекте, как [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md).  Узлы, не поддерживающие интерфейс пользователя, как серверы, а не реализации бы интерфейс `IActiveScriptSiteWindow`.  Обработчик скриптов обращается к этого интерфейса нужно вызвать метод `QueryInterface` из `IActiveScriptSite`.  
  
## Методы в порядке таблицы Vtable  
  
|Метод|Описание|  
|-----------|--------------|  
|[IActiveScriptSiteWindow::GetWindow](../../winscript/reference/iactivescriptsitewindow-getwindow.md)|Получает дескриптор окна, который может действовать в качестве владельца контекстного меню окна, обработчик скриптов должен отображаться.|  
|[IActiveScriptSiteWindow::EnableModeless](../../winscript/reference/iactivescriptsitewindow-enablemodeless.md)|Вызывает основное приложение включить или отключить свое главное окно, немодальное все диалоговые окна.|  
  
## См. также  
 [Интерфейсы активных скриптов](../../winscript/reference/active-script-interfaces.md)