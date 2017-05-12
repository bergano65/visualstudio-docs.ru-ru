---
title: "IWebAppDiagnosticsSetup — интерфейс | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IWebAppDiagnosticsSetup — интерфейс"
ms.assetid: ec7359f2-633e-4d59-b64b-9cab0134dfd0
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IWebAppDiagnosticsSetup — интерфейс
Этот интерфейс реализуется PDM создать COM\-объект в процессе отладки приложения, отладки и устранение неполадок через интернет включить.  Если PDM средства [IObjectWithSite](http://go.microsoft.com/fwlink/?LinkId=232438) отладки объекта приложения вызывает [SetSite](http://go.microsoft.com/fwlink/?LinkId=232439) Internet Explorer, то в ней после их создатьы и пройдут в ссылку на [IWebBrowser2](http://go.microsoft.com/fwlink/?LinkId=232449).  Вызовы [SetSite](http://go.microsoft.com/fwlink/?LinkId=232439) приложений WWA и пропуски в WWA взаимодействуют IWebApplicationHost.  Если [SetSite](http://go.microsoft.com/fwlink/?LinkId=232439) вызывается со значением [IWebAppDiagnosticsSetup::DiagnosticsSupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md), отличных от NULL, возвращает значение true.  В противном случае он возвращает значение false и вызовы [IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md) завершаются с ошибкой.  
  
> [!IMPORTANT]
>  `IWebAppDiagnosticsSetup` реализуется PDM v11.0 и большим.  Обнаружен в activdbg100.h.  
  
## Методы  
 Этот интерфейс предоставляет следующие методы.  
  
|Метод|Описание|  
|-----------|--------------|  
|[IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md)|Возвращает текстовые документы, скрыватьы указанным фильтром.|  
|[IWebAppDiagnosticsSetup::DiagnosticsSupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md)|Определяет, принадлежит ли указанный документ на один из дочерних узлов данного узла.|