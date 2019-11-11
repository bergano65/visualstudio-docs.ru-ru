---
title: Интерфейс Ивебаппдиагностикссетуп | Документация Майкрософт
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
ms.openlocfilehash: 1e9bb3905da6227b978bc27b96493500f8d6d2ff
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/28/2019
ms.locfileid: "72984539"
---
# <a name="iwebappdiagnosticssetup-interface"></a>IWebAppDiagnosticsSetup — интерфейс
Этот интерфейс реализуется приложением отладки PDM для создания COM-объектов в отлаживаемом процессе и для включения веб-диагностики. Если объект приложения отладки PDM реализует [IObjectWithSite](/windows/win32/api/ocidl/nn-ocidl-iobjectwithsite), Internet Explorer вызывает [SetSite](/windows/win32/api/ocidl/nf-ocidl-iobjectwithsite-setsite) на нем после его создания и передает ссылку на [IWebBrowser2](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752127(v=vs.85)). Приложение ВВА вызывает [SetSite](/windows/win32/api/ocidl/nf-ocidl-iobjectwithsite-setsite) и передает в интерфейс ВВА ивебаппликатионхост. Если [SetSite](/windows/win32/api/ocidl/nf-ocidl-iobjectwithsite-setsite) был вызван со значением, ОТЛИЧНЫМ от NULL, [Ивебаппдиагностикссетуп::D иагностикссуппортед](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md) возвращает значение true. В противном случае возвращается значение false и вызовы [ивебаппдиагностикссетуп:: креатеобжектвисситеатвебапп](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md) завершаются ошибкой.  
  
> [!IMPORTANT]
> `IWebAppDiagnosticsSetup` реализованы с помощью PDM версии 11.0 и выше. Обнаружено в activdbg100.h.  
  
## <a name="methods"></a>Методы  
 Этот интерфейс предоставляет следующие методы.  
  
|Метод|Описание|  
|------------|-----------------|  
|[IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md)|Возвращает текстовые документы, скрытые указанным фильтром.|  
|[IWebAppDiagnosticsSetup::DiagnosticsSupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md)|Определяет, принадлежит ли указанный документ одному из дочерних узлов этого узла.|