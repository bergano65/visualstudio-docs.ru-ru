---
title: "Интерфейс IDebugSessionProvider | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugSessionProvider — интерфейс"
ms.assetid: 1b898423-7af9-44f5-8dda-987005309c99
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Интерфейс IDebugSessionProvider
Основной интерфейс, предоставляемых средой разработки отладчика, включенные основное приложение и язык начала отладки.  Он устанавливает сеанс отладки для запущенного приложения.  Этот интерфейс реализуется компьютером диспетчер отладки.  
  
 В дополнение к методам, наследуемым от интерфейса `IUnknown`, интерфейс `IDebugSessionProvider` предоставляет следующие методы.  
  
## Методы в порядке таблицы Vtable  
  
|Метод|Описание|  
|-----------|--------------|  
|[IDebugSessionProvider::StartDebugSession](../../winscript/reference/idebugsessionprovider-startdebugsession.md)|Начинает сеанс отладки с указанным приложением.|