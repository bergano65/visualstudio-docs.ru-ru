---
title: "Практическое руководство. Создание страницы приложения | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "страницы приложений [разработка приложений SharePoint в Visual Studio], добавление"
  - "страницы приложений [разработка приложений SharePoint в Visual Studio], создание"
ms.assetid: 9ad7044a-2fa7-4bba-8f25-b9f2cc1b7c6b
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 15
---
# Практическое руководство. Создание страницы приложения
  Можно создать веб\-страницу ASP.NET для одного или нескольких сайтов SharePoint.  В SharePoint эти страницы называются страницами приложения.  В отличие от страницы сайта страница приложения содержит код, выполняемый за страницей.  Для получения дополнительной информации см. [Создание страниц приложений для SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).  
  
### Создание страницы приложения  
  
1.  Откройте или создайте проект SharePoint в Visual Studio.  
  
     Для получения дополнительной информации см. [Шаблоны проектов и элементов проектов SharePoint](../sharepoint/sharepoint-project-and-project-item-templates.md).  
  
2.  В области **Обозреватель решений** выберите узел проекта.  
  
3.  В строке меню выберите **Проект**, **Добавить новый элемент**.  
  
4.  В диалоговом окне **Добавление нового элемента** разверните узел **SharePoint** и выберите элемент **2010**.  
  
5.  В списке шаблонов SharePoint выберите **Страница приложения**.  
  
6.  В поле **Имя** введите имя для страницы приложения и нажмите кнопку **Добавить**.  
  
     Visual Studio добавляет в проект несколько папок и файлов.  Дополнительные сведения об этих файлах см. в разделе [Создание страниц приложений для SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).  
  
     Файл страницы ASP.NET отображается в представлении **Источник** конструктора Visual Web Developer.  Можно создать страницу, добавив элементы управления с **панели элементов** на местозаполнители содержимого.  Дополнительные сведения см. в разделе [Представление источника, конструктор веб\-страниц](http://msdn.microsoft.com/ru-ru/5911396b-fe51-4150-9ff1-b085f812862f).  
  
7.  Для обработки событий элементов управления необходимо добавить код в файл кода страницы приложения.  
  
     Если развернуть узел файла страницы ASP.NET, отобразится файл кода с расширением CS или VB, в зависимости от языка проекта.  Полный пример создания страницы приложения см. в разделе [Пошаговое руководство. Создание страницы приложения SharePoint](../sharepoint/walkthrough-creating-a-sharepoint-application-page.md).  
  
## См. также  
 [Карта содержимого среды веб\-разработки Visual Studio](http://msdn.microsoft.com/ru-ru/9c31f93b-c8fb-4599-9b14-6194ec8c7539)   
 [Создание страниц приложений для SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)   
 [Пошаговое руководство. Создание страницы приложения SharePoint](../sharepoint/walkthrough-creating-a-sharepoint-application-page.md)  
  
  