---
title: Исключения политики жизненного цикла Visual Studio | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c238489d-6181-42c6-aa60-f75d0889dc68
caps.latest.revision: 3
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.openlocfilehash: 3094e18798fa987390fce3ee64d0a6da2fe0a9ba
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49196122"
---
# <a name="visual-studio-lifecycle-policy-exceptions"></a>Исключения политики жизненного цикла Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio включает в себя ряд компиляторов, языков, сред и других ресурсов, благодаря которым становится возможной разработка решений для многих платформ Майкрософт. Для удобства пользователей Visual Studio может устанавливать определенные пакеты SDK и другие компоненты Майкрософт, предназначенные для поддержки этих платформ и работы с ними. Поддержка и лицензирование этих компонентов может осуществляться в соответствии с их собственными условиями и политиками.  
  
## <a name="external-components-that-follow-a-lifecycle-policy-other-than-the-visual-studio-policy"></a>Внешние компоненты, в отношении которых действуют политики жизненного цикла, отличные от политики Visual Studio  
 В таблице ниже перечислены компоненты платформы Майкрософт, которые могут входить в состав Visual Studio (в зависимости от конкретного выпуска Visual Studio) и которые подлежат собственным политикам и срокам обслуживания.  
  
|СЕМЕЙСТВО ПРОДУКТОВ|ВНЕШНЕЕ ИМЯ|  
|--------------------|-------------------|  
|[.NET 3.5](http://support.microsoft.com/lifecycle/search/default.aspx?sort=PN&alpha=net%20framework%203.5&Filter=FilterNO)|.NET 3.5 SDK<br /><br /> Windows Identity Foundation|  
|[.NET 4.5](http://support.microsoft.com/lifecycle/search/default.aspx?sort=PN&alpha=net%20framework%204.5&Filter=FilterNO)|.NET 4.5 SDK|  
|[.NET 4.5.1](http://support.microsoft.com/lifecycle/search/default.aspx?sort=PN&alpha=.NET%20Framework%204.5.1&Filter=FilterNO)|Пакет MT .NET 4.5.1 (классический)<br /><br /> Пакет многоплатформенного нацеливания .NET 4.5.1 (Магазин)<br /><br /> .NET 4.5.1 OOB MSU<br /><br /> Распространяемый пакет .NET 4.5.1<br /><br /> Распространяемые языковые пакеты .NET 4.5.1<br /><br /> .NET 4.5.1 SDK|  
|[Веб-решения ASP.NET](http://go.microsoft.com/fwlink/?LinkId=328918)|ASP.NET MVC 4<br /><br /> ASP.NET MVC 5<br /><br /> ASP.NET Web API<br /><br /> ASP.NET Web API 2<br /><br /> Веб-страницы ASP.NET 2<br /><br /> Веб-страницы ASP.NET 3|  
|[Entity Framework 6](http://go.microsoft.com/fwlink/?LinkId=328950)|Entity Framework 6|  
|[Exchange 2013](http://go.microsoft.com/fwlink/?LinkId=328950)|Веб-службы Exchange|  
|[Microsoft OWIN](http://go.microsoft.com/fwlink/?LinkId=328951)|Microsoft OWIN|  
|[Microsoft Web Developer Tools 2013](http://go.microsoft.com/fwlink/?LinkId=328952)|Веб-инструменты Майкрософт для разработчиков 2013|  
|Обновления для этих компонентов распространяются с помощью NuGet и не следуют стандартным политикам жизненного цикла Майкрософт.  Дополнительные сведения см. в разделе [http://docs.nuget.org/](http://docs.nuget.org/).|Веб-обработчик токенов JSON для Microsoft .Net Framework 4.5<br /><br /> NuGet 2.7<br /><br /> SignalR<br /><br /> Web Optimization Framework<br /><br /> WebGrease|  
|[ODataLib](http://go.microsoft.com/fwlink/?LinkId=328954)|ODataLib|  
|[Office 2013](http://support.microsoft.com/lifecycle/?p1=16674)|Open XML SDK|  
|[Политика веб-служб](http://support.microsoft.com/gp/OSSLpolicy)|Microsoft Ads SDK|  
|[SharePoint 2013](http://support.microsoft.com/lifecycle/search/default.aspx?sort=PN&alpha=sharepoint%20server%202013&Filter=FilterNO)|Клиентский компонент SharePoint<br /><br /> SharePoint Foundation 2013<br /><br /> Расширения Windows Identity Foundation|  
|[Silverlight 5](http://support.microsoft.com/lifecycle/?p1=16278)<br /><br /> <br />> См. также: [http://support.microsoft.com/gp/lifean45](http://support.microsoft.com/gp/lifean45)|Среда выполнения Silverlight 5<br /><br /> Пакет SDK для Silverlight 5|  
|[SQL Server 2008 R2](http://support.microsoft.com/lifecycle/search/default.aspx?sort=PN&alpha=SQL%20Server%202008%20R2&Filter=FilterNO)|Типы CLR системы SQL (SQL Server 2008 R2)|  
|[SQL Server 2012](http://support.microsoft.com/lifecycle/search/default.aspx?sort=PN&alpha=SQL%20Server%202012&Filter=FilterNO)|DACFx (DACFramework)<br /><br /> SMO (SharedManagementObjects)<br /><br /> Служебные программы командной строки SQL<br /><br /> Языковая служба SQL — IntelliSense (TSQLLanguageService)<br /><br /> SQL LocalDB<br /><br /> Собственный клиент SQL (Sqlncli)<br /><br /> SQL Server Express 2012 с пакетом обновления 1 (SP1)<br /><br /> Типы CLR системы SQL (SQL Server 2012)<br /><br /> SQLDOM|  
|[SQL Server 2014](https://support.microsoft.com/en-us/lifecycle/search?sort=PN&alpha=SQL%20Server%202014&Filter=FilterNO)|DACFx (DACFramework)<br /><br /> SMO (SharedManagementObjects)<br /><br /> Служебные программы командной строки SQL<br /><br /> Языковая служба SQL — IntelliSense (TSQLLanguageService)<br /><br /> SQL LocalDB<br /><br /> Собственный клиент SQL (Sqlncli)<br /><br /> SQL Server Express 2014<br /><br /> Типы CLR системы SQL (SQL Server 2014)<br /><br /> SQLDOM|  
|[SQL Server Compact Edition 4.0](http://support.microsoft.com/lifecycle/?p1=16106)|SQL Server Compact Edition 4.0|  
|[WCF RIA Services версии 1.0 с пакетом обновления 2](http://go.microsoft.com/fwlink/?LinkId=328955)|Службы WCF RIA 1.0 с пакетом обновления 2 (SP2)|  
|[Windows Server 2008](http://support.microsoft.com/lifecycle/search/default.aspx?sort=PN&alpha=Windows%20Server%202008&Filter=FilterNO)|Веб-службы Windows (WWS) для Windows Server 2008|  
|[Windows 7](http://support.microsoft.com/lifecycle/?c2=14019)|Пакет SDK для Windows 7|  
|[Windows 8](http://support.microsoft.com/lifecycle/?c2=16796)|Пакет SDK для Windows 8|  
|[Windows 8.1](http://support.microsoft.com/lifecycle/search/default.aspx?sort=PN&alpha=windows%208.1&Filter=FilterNO)|Пакет SDK для Windows 8.1<br /><br /> Библиотека Windows для JavaScript (WinJS)|  
|[Microsoft Azure](http://support.microsoft.com/gp/azure-cloud-lifecycle-faq)<br /><br /> <br />> См. также: [Online политика жизненного цикла](http://support.microsoft.com/gp/OSSLpolicy)|Пакет SDK для мобильных служб Microsoft Azure<br /><br /> Инструменты мобильных служб Microsoft Azure|