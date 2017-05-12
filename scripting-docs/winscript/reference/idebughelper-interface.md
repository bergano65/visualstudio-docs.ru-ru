---
title: "Интерфейс IDebugHelper | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugHelper — интерфейс"
ms.assetid: ef5691e0-1d82-42c2-997c-888e31c478dd
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Интерфейс IDebugHelper
Файлы в качестве фабрики для просмотра объектов и простой точки подключения.  Процесс средства отладки диспетчера \(PDM\) этот интерфейс, который использоваться командами сценария.  
  
 В дополнение к методам, наследуемым от интерфейса `IUnknown`, интерфейс `IDebugHelper` предоставляет следующие методы.  
  
## Методы в порядке таблицы Vtable  
  
|Метод|Описание|  
|-----------|--------------|  
|[IDebugHelper::CreatePropertyBrowser](../../winscript/reference/idebughelper-createpropertybrowser.md)|Возвращает обозреватель свойств, который создает программу\-оболочку ВЕРСИЙ.|  
|[IDebugHelper::CreatePropertyBrowserEx](../../winscript/reference/idebughelper-createpropertybrowserex.md)|Возвращает обозреватель свойств, который создает программу\-оболочку ВЕРСИЯМИ, и для пользовательского преобразования РАЗЛИЧНЫХ значений или VARTYPE печатает к строкам.|  
|[IDebugHelper::CreateSimpleConnectionPoint](../../winscript/reference/idebughelper-createsimpleconnectionpoint.md)|Возвращает интерфейс события, который создает программу\-оболочку заданный объект `IDispatch`.|