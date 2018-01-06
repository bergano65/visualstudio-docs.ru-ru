---
title: "Как: Создание страницы приложения | Документы Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- application pages [SharePoint development in Visual Studio], adding
- application pages [SharePoint development in Visual Studio], creating
ms.assetid: 9ad7044a-2fa7-4bba-8f25-b9f2cc1b7c6b
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 75c896f101f1eb0a11884b492ba559045a1dd180
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-an-application-page"></a>Практическое руководство. Создание страницы приложения
  Можно создать веб-страницу ASP.NET для одного или нескольких сайтов SharePoint. В SharePoint эти страницы называются страницы приложения. В отличие от страницы сайта приложения содержит код, выполняемый за страницей. Дополнительные сведения см. в разделе [Создание страниц приложений для SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).  
  
### <a name="to-create-an-application-page"></a>Создание страницы приложения  
  
1.  Откройте или создайте проект SharePoint в Visual Studio.  
  
     Дополнительные сведения см. в разделе [проект SharePoint и шаблоны элементов проекта](../sharepoint/sharepoint-project-and-project-item-templates.md).  
  
2.  В области **Обозреватель решений**выберите узел проекта.  
  
3.  В строке меню выберите **проекта**, **Добавление нового элемента**.  
  
4.  В **Добавление нового элемента** диалогового окна разверните **SharePoint** узел и выберите **2010** элемента.  
  
5.  В списке шаблонов SharePoint выберите **страницы приложения**.  
  
6.  В **имя** укажите имя для страницы приложения и выберите **добавить** кнопки.  
  
     Visual Studio добавляет несколько файлов и папок в проект. Дополнительные сведения об этих файлах см. в разделе [Создание страниц приложений для SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).  
  
     В **источника** появится представление конструктора Visual Web Developer, файла страницы ASP.NET. Проектировать страницу можно путем добавления элементов управления из **элементов** и их размещения на местозаполнители содержимого. Дополнительные сведения см. в разделе [представления источника, разработчик веб-страницы](http://msdn.microsoft.com/en-us/5911396b-fe51-4150-9ff1-b085f812862f).  
  
7.  Если вы хотите обрабатывать события элемента управления, добавьте код в файл кода для страницы приложения.  
  
     Файл кода появляется, если развернуть узел файла страницы ASP.NET и имеет расширение CS или VB в зависимости от языка проекта. Пример конца в конец Создание страницы приложения в разделе [Пошаговое руководство: Создание страницы приложения SharePoint](../sharepoint/walkthrough-creating-a-sharepoint-application-page.md).  
  
## <a name="see-also"></a>См. также  
 [Создание страниц приложений для SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)   
 [Пошаговое руководство. Создание страницы приложения SharePoint](../sharepoint/walkthrough-creating-a-sharepoint-application-page.md)  
  
  