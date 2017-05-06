---
title: "Практическое руководство. Создание веб-части SharePoint"
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
  - "веб-части [разработка приложений SharePoint в Visual Studio], добавление"
  - "веб-части [разработка приложений SharePoint в Visual Studio], создание"
ms.assetid: 0d037522-c25e-4c24-93b7-518db0f791b7
caps.latest.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 20
---
# Практическое руководство. Создание веб-части SharePoint
  Можно создавать и настраивать веб\-части путем добавления элемента **Веб\-часть** в любой проект SharePoint и изменения файла кода веб\-части либо с помощью конструктора.  Для получения дополнительной информации см. [Практическое руководство. Создание веб-части SharePoint с помощью конструктора](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md).  
  
### Создание веб\-части SharePoint  
  
1.  создайте или откройте проект SharePoint.  
  
     Для получения дополнительной информации см. [Шаблоны проектов и элементов проектов SharePoint](../sharepoint/sharepoint-project-and-project-item-templates.md).  
  
2.  Выберите узел проекта SharePoint в **обозревателе решений**, затем выберите **Добавить новый элемент** в меню **Проект**.  
  
3.  В диалоговом окне **Добавление нового элемента** разверните узел **SharePoint** и выберите узел **2010**.  
  
4.  В списке шаблонов SharePoint выберите **Веб\-часть**.  
  
5.  В поле **Имя** введите имя для веб\-части и нажмите кнопку **Добавить**.  
  
     Веб\-часть отобразится в **обозревателе решений**.  Дополнительные сведения о файлах, которые содержит веб\-часть, см. в разделе [Создание веб-частей для SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md).  
  
6.  В **Обозревателе решений** откройте файл кода только что созданной веб\-части.  
  
     Например, если веб\-часть называется WebPart1, откройте WebPart1.vb \(в Visual Basic\) или WebPart1.cs \(в C\#\).  
  
7.  В файле кода добавьте элементы управления в метод <xref:System.Web.UI.Control.CreateChildControls%2A>.  
  
     Пример см. в разделе [Пошаговое руководство. Создание веб-части для SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md).  
  
## См. также  
 [Создание веб-частей для SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)   
 [Практическое руководство. Создание веб-части SharePoint с помощью конструктора](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)   
 [Пошаговое руководство. Создание веб-части для SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)   
 [Пошаговое руководство. Создание веб-части для SharePoint с помощью конструктора](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)  
  
  