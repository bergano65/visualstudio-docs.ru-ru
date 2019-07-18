---
title: Интерфейс IWebAppDiagnosticsSetup | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 71d4501fff04b62abe392c6684a4a0551dea9ee8
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63443663"
---
# <a name="iwebappdiagnosticssetup-interface"></a>IWebAppDiagnosticsSetup — интерфейс
Этот интерфейс реализуется в PDM отладки приложения для создания COM-объекты в отлаживаемом процессе и выполнять диагностику веб. Если PDM отладку приложения реализует объект [IObjectWithSite](http://go.microsoft.com/fwlink/?LinkId=232438), Internet Explorer вызывает программу [SetSite](http://go.microsoft.com/fwlink/?LinkId=232439) на его после его создания и передает ссылку на [IWebBrowser2](http://go.microsoft.com/fwlink/?LinkId=232449). Когда приложение WWA вызывает [SetSite](http://go.microsoft.com/fwlink/?LinkId=232439) и передает в WWA интерфейса IWebApplicationHost. Если [SetSite](http://go.microsoft.com/fwlink/?LinkId=232439) был вызван со значением отличное от NULL, [IWebAppDiagnosticsSetup::DiagnosticsSupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md) возвращает значение true. Если нет, он возвращает значение false, а также вызовы к [IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md) ошибкой.  
  
> [!IMPORTANT]
> `IWebAppDiagnosticsSetup` реализуется PDM v11.0 и более. Обнаружено в activdbg100.h.  
  
## <a name="methods"></a>Методы  
 Этот интерфейс предоставляет следующие методы.  
  
|Метод|Описание|  
|------------|-----------------|  
|[IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md)|Получает текстовые документы, которые скрыты с помощью указанного фильтра.|  
|[IWebAppDiagnosticsSetup::DiagnosticsSupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md)|Определяет, относится ли указанный документ на один из дочерних узлов данного узла.|