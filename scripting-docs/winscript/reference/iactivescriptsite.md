---
title: "IActiveScriptSite | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptSite — интерфейс"
ms.assetid: 4d604a11-5365-46cf-ab71-39b3dbbe9f22
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptSite
Реализуемый основным приложением, чтобы создать сайт для обработчика скрипта Windows.  Как правило, этот сайт будет связать с контейнером для всех объектов, которые видны к скрипту \(например, элементов управления ActiveX\).  Обычно этот контейнер будет соответствовать просмотра в документ или на странице.  Microsoft Internet Explorer, например, создатьTm мере такой контейнер для каждой страницы, показыванным HTML.  Каждый элемент управления ActiveX \(или другой объект ole\-автоматизации\) на странице и обработчиком сценариев является перечислимой, будет внутри контейнера.  
  
## Методы в порядке таблицы Vtable  
  
|||  
|-|-|  
|Метод|Описание|  
|[IActiveScriptSite::GetLCID](../../winscript/reference/iactivescriptsite-getlcid.md)|Извлекает код языка, который основное приложение использует для отображения элементов интерфейса пользователя.|  
|[IActiveScriptSite::GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md)|Возвращает сведения об элементе, который был добавлен на обработчик через вызов метода [IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md).|  
|[IActiveScriptSite::GetDocVersionString](../../winscript/reference/iactivescriptsite-getdocversionstring.md)|Получает основное приложение\- указанная строка, однозначно определяющее версию текущего документа с точки зрения узла.|  
|[IActiveScriptSite::OnScriptTerminate](../../winscript/reference/iactivescriptsite-onscriptterminate.md)|Если скрипт с именем за выполнение.|  
|[IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md)|Уведомляет основное приложение о том, что обработчик скриптов был изменен состояния.|  
|[IActiveScriptSite::OnScriptError](../../winscript/reference/iactivescriptsite-onscripterror.md)|Уведомляет основное приложение о том, что ошибка произошла во время запуска выполнения обработчика скриптов.|  
|[IActiveScriptSite::OnEnterScript](../../winscript/reference/iactivescriptsite-onenterscript.md)|Уведомляет основное приложение о том, что обработчик скриптов был запущен выполнять код сценария.|  
|[IActiveScriptSite::OnLeaveScript](../../winscript/reference/iactivescriptsite-onleavescript.md)|Уведомляет основное приложение о том, что обработчик скриптов возвращал из выполнять код сценария.|  
  
## См. также  
 [Интерфейсы активных скриптов](../../winscript/reference/active-script-interfaces.md)