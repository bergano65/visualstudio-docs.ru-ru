---
title: Iwebappdiagnosticssetup — интерфейс | Документы Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IWebAppDiagnosticsSetup Interface
ms.assetid: ec7359f2-633e-4d59-b64b-9cab0134dfd0
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6e273f29bee6e4d2aae26c01c477373a735624c8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24734004"
---
# <a name="iwebappdiagnosticssetup-interface"></a>IWebAppDiagnosticsSetup — интерфейс
Этот интерфейс реализуется в PDM отладки приложение для создания COM-объекты в отлаживаемом процессе и включение диагностики в веб. Если PDM отладить приложение реализует объект [IObjectWithSite](http://go.microsoft.com/fwlink/?LinkId=232438), Internet Explorer вызывает [SetSite](http://go.microsoft.com/fwlink/?LinkId=232439) на его после его создания и передает ссылку на [IWebBrowser2](http://go.microsoft.com/fwlink/?LinkId=232449). Когда приложение WWA вызывает [SetSite](http://go.microsoft.com/fwlink/?LinkId=232439) и передает в WWA интерфейса IWebApplicationHost. Если [SetSite](http://go.microsoft.com/fwlink/?LinkId=232439) был вызван со значением НЕНУЛЕВОЙ [IWebAppDiagnosticsSetup::DiagnosticsSupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md) возвращает значение true. Если нет, она возвращает значение false и вызовы [IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md) ошибкой.  
  
> [!IMPORTANT]
>  `IWebAppDiagnosticsSetup`реализуется в PDM v11.0 и более. Обнаружено в activdbg100.h.  
  
## <a name="methods"></a>Методы  
 Этот интерфейс предоставляет следующие методы.  
  
|Метод|Описание|  
|------------|-----------------|  
|[IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md)|Возвращает текстовые документы, которые скрыты с помощью указанного фильтра.|  
|[IWebAppDiagnosticsSetup::DiagnosticsSupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md)|Определяет, относится ли указанный документ на один из дочерних узлов данного узла.|