---
title: "IWebAppDiagnosticsObjectInitialization — интерфейс | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IWebAppDiagnosticsObjectInitialization — интерфейс"
ms.assetid: 32847838-01d9-4205-a811-3043d8c7a917
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IWebAppDiagnosticsObjectInitialization — интерфейс
Этот интерфейс может быть реализован в классах, которые реализуют [IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md).  [IWebAppDiagnosticsSetup — интерфейс](../../winscript/reference/iwebappdiagnosticssetup-interface.md) реализуется объектом, что средства [Интерфейс IDebugApplication](../../winscript/reference/idebugapplication-interface.md).  В большинстве случаев этот объект PDM.  
  
 После того как объект был создания, [IWebAppDiagnosticsObjectInitialization::Initialize](../../winscript/reference/iwebappdiagnosticsobjectinitialization-initialize.md) Позвонитьо со ссылкой на PDM отладку приложения и параметр `hPassToObject``CreateObjectWithSiteAtWebApp`.  
  
> [!IMPORTANT]
>  `IWebAppDiagnosticsObjectInitialization` находитьо в activdbg100.h.  
  
## Методы  
 Этот интерфейс предоставляет следующие методы.  
  
|Метод|Описание|  
|-----------|--------------|  
|[IWebAppDiagnosticsObjectInitialization::Initialize](../../winscript/reference/iwebappdiagnosticsobjectinitialization-initialize.md)|Инициализирует объект.|