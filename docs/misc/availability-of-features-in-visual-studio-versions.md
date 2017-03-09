---
title: "Доступность функций в различных версиях Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Visual Studio, доступность функций"
ms.assetid: cb2728da-7705-4dea-a1c3-12a0388cb652
caps.latest.revision: 18
caps.handback.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Доступность функций в различных версиях Visual Studio
В таблице ниже указано, поддерживается ли конкретная функция в перечисленных версиях Visual Studio Professional.  
  
-   "Да" — данная версия Visual Studio содержит эту функцию.  
  
-   "Надстройка" означает, что версия Visual Studio не содержит эту функцию, но она доступна \(дополнительные сведения можно получить, перейдя по ссылке\).  
  
-   "Нет" — данная версия Visual Studio не содержит эту функцию.  
  
||Visual Studio 2010<br /><br /> и<br /><br /> Пакет SP1 Visual Studio 2010|[!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)]|[!INCLUDE[vs_dev12](../data-tools/includes/vs_dev12_md.md)]|  
|-|---------------------------------------------------------------|-------------------------------------------------------------------|--------------------------------------------------------------|  
|Поддержанные версии платформы .NET Framework|2.0, 3.0, 3.5 с пакетом обновления 1 \(SP1\), 4|2.0, 3.0, 3.5 SP1, 4, 4.5|2.0, 3.0, 3.5 SP1, 4, 4.5, 4.5.1|  
|Локальный веб\-сервер|Да|Да|Да|  
|SQL Server Express|2008|2008|2008|  
|Подключение к версиям SQL Server с помощью обозревателя серверов|2000, 2005, 2008|2000, 2005, 2008|2000, 2005, 2008|  
|ASP.NET Ajax <sup>1</sup>|Да|Да|Да|  
|Контроллер просмотра модели ASP.NET|Да|Да|Да|  
|Платформа динамических данных ASP.NET|Да|Да|Да|  
|MSBuild|Да|Да|Да|  
|ADO.NET Entity Framework|Да|Да|Да|  
|Службы данных ADO.NET|Да|Да|Да|  
|Средства Microsoft Azure|Add|Add||  
|Интеллектуальные устройства|Нет|Нет||  
|Параллельные вычисления|Да <sup>2</sup>|Да|Да|  
|Windows Communication Foundation|Да|Да|Да|  
|Windows Presentation Foundation \(WPF\)|Да|Да|Да|  
|Службы полнофункциональных интернет\-приложений .NET|[Надстройка](http://go.microsoft.com/fwlink/?LinkID=230768)|Да|Да|  
|Silverlight 1|Да|Да|Да|  
|Silverlight 2|Нет|Да|Да|  
|Silverlight 3|Да|Да|Да|  
|Silverlight 4|[Надстройка](http://go.microsoft.com/fwlink/?LinkID=153710)|Да|Да|  
|Silverlight 5|[Надстройка](http://go.microsoft.com/fwlink/?LinkID=215392), только пакет обновления 1 \(SP1\).|Да|Да|  
|IronPython.|[Надстройка](http://go.microsoft.com/fwlink/?LinkID=183863)|[Надстройка](http://go.microsoft.com/fwlink/?LinkID=183863)|[Надстройка](http://go.microsoft.com/fwlink/?LinkID=183863)|  
|IronRuby|[Надстройка](http://go.microsoft.com/fwlink/?LinkID=183864)|[Надстройка](http://go.microsoft.com/fwlink/?LinkID=183864)|[Надстройка](http://go.microsoft.com/fwlink/?LinkID=183864)|  
|Visual Studio Tools for Office|Да <sup>4</sup><br /><br /> \(Office 2007, Office 2010\)|Да <sup>4</sup>\(Office 2010\)|Да <sup>4</sup>\(Office 2013\)|  
|Проекты отчетов|Да|Да|Да|  
|Мастер отчетов|Да|Да|Да|  
|LINQ|Да|Да|Да|  
|Разработка для SharePoint|Да — для SharePoint 2010|Да — для SharePoint 2010|Да — для SharePoint 2013|  
|Поддержка клиентского профиля .NET Framework 4|Да|Нет|Нет|  
  
1.  ASP.NET Ajax:  
  
     Со стороны сервера: элементы управления входят в ASP.NET 3.5 и располагаются в **области инструментов** в Visual Studio.  При использовании более ранней версии платформы ASP.NET, например ASP.NET 2.0, можно загрузить [расширения AJAX ASP.NET](http://go.microsoft.com/fwlink/?LinkID=75360).  
  
     Со стороны клиента: клиентская библиотека ASP.NET Ajax входит в ASP.NET 3.5 с пакетом обновления 1 \(SP1\).  
  
2.  Параллельные вычисления:  
  
     Параллельные расширения содержат библиотеку параллельных задач \(TPL\), параллельный LINQ \(PLINQ\) и структуры данных параллелизма. Эти компоненты входят в состав платформы .NET Framework 4.  Эквивалентные библиотеки для собственной разработки С\+\+ — это среда выполнения с параллелизмом и библиотека агентов, которые входят в состав Visual Studio 2010.  В Visual Studio 2010 также добавлены усовершенствования профилировщика и отладчика.  
  
3.  IronPython и IronRuby:  
  
     На веб\-сайтах CodePlex доступны некоторые версии для IronPython и IronRuby.  Выберите версию, которая подходит для используемой среды.  Минимальным требованием для обоих языков является использование платформы .NET Framework 2.0 с пакетом обновления 1 \(SP1\).  
  
4.  Совместимость Visual Studio Tools for Office \(VSTO\) и функциональные возможности надстроек:  
  
    ||Visual Studio 2010|[!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)]|[!INCLUDE[vs_dev12](../data-tools/includes/vs_dev12_md.md)]|  
    |-|------------------------|-------------------------------------------------------------------|--------------------------------------------------------------|  
    |Уровень документа|Word 2007, Word 2010, Excel 2007, Excel 2010|Word 2010, Excel 2010|Word 2013, Excel 2013|  
    |Уровень приложения|Word 2007, Word 2010, Excel 2007, Excel 2010, InfoPath 2007, InfoPath 2010, Outlook 2007, Outlook 2010, PowerPoint 2007, PowerPoint 2010, Visio 2007, Visio 2010, Project 2007, Project 2010|Word 2010, Excel 2010, InfoPath 2010, Outlook 2010, PowerPoint 2010, Visio 2010, Project 2010|Word 2013, Excel 2013, InfoPath 2013, Outlook 2013, PowerPoint 2013, Visio 2013, Project 2013|