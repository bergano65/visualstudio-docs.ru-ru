---
title: "Интерфейс IDebugSessionProviderEx | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 26c5da2d-8c93-4d2b-94d2-97aaa377dcfe
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# Интерфейс IDebugSessionProviderEx
Основной интерфейс, предоставленный средой разработки отладчика для включения и язык\- хозяина начала отладки.  Он устанавливает сеанс отладки для запущенного приложения.  Этот интерфейс реализуется диспетчером отладка компьютера.  
  
 В дополнение к методам, наследуемым от интерфейса `IUnknown`, интерфейс `IDebugSessionProviderEx` предоставляет следующие методы.  
  
## Методы в порядке таблицы Vtable  
  
|Метод|Описание|  
|-----------|--------------|  
|[IDebugSessionProviderEx:CanJITDebug](../../winscript/reference/idebugsessionproviderex-canjitdebug.md)|Определяет, является ли возможна только в время отладки с указанным приложением.|  
|[IDebugSessionProviderEx:StartDebugSession](../../winscript/reference/idebugsessionproviderex-startdebugsession.md)|Начинает сеанс отладки с указанным приложением.|