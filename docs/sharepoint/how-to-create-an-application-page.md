---
title: 'Практическое: Создание страницы приложения | Документация Майкрософт'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- application pages [SharePoint development in Visual Studio], adding
- application pages [SharePoint development in Visual Studio], creating
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9f390ddf14925b43f1aa1d9e79db05e2aa64f234
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2018
ms.locfileid: "51296207"
---
# <a name="how-to-create-an-application-page"></a>Практическое: Создание страницы приложения
  Можно создать веб-страницу ASP.NET, для одного или нескольких сайтов SharePoint. В SharePoint эти страницы называются страницами приложения. В отличие от страницы сайта приложения содержит код, выполняемый за страницей. Дополнительные сведения см. в разделе [Создание страниц приложений для SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).  
  
### <a name="to-create-an-application-page"></a>Чтобы создать страницу приложения  
  
1.  Откройте или создайте проект SharePoint в Visual Studio.  
  
     Дополнительные сведения см. в разделе [SharePoint проект и проект шаблоны элементов](../sharepoint/sharepoint-project-and-project-item-templates.md).  
  
2.  В области **Обозреватель решений**выберите узел проекта.  
  
3.  В строке меню выберите **Проект** > **Добавить новый элемент**.  
  
4.  В **Добавление нового элемента** диалоговое окно последовательно раскройте элементы **SharePoint** узел, а затем выберите **2010** элемента.  
  
5.  В списке шаблонов SharePoint выберите **страницы приложения**.  
  
6.  В **имя** , укажите имя для страницы приложения и затем выберите **добавить** кнопки.  
  
     Visual Studio добавляет несколько файлов и папок в проект. Дополнительные сведения об этих файлах см. в разделе [Создание страниц приложений для SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).  
  
     В представлении **исходного кода** конструктора Visual Web Developer отображается файл страницы ASP.NET. Вы можете проектировать страницу, добавляя элементы управления из **Панели элементов** и помещая их на местозаполнители содержимого. Дополнительные сведения: [Представление исходного кода, конструктор веб-страниц](/previous-versions/aspnet/ms178154\(v\=vs.100\)).  
  
7.  Если вы хотите обрабатывать события элемента управления, добавьте код в файл кода страницы приложения.  
  
     Файл кода появляется, если развернуть узел файла страницы ASP.NET и имеет *.cs* или *.vb* расширения, в зависимости от языка проекта. End-to-end пример того, как создать страницу приложения, см. в разделе [Пошаговое руководство: Создание страницы приложения SharePoint](../sharepoint/walkthrough-creating-a-sharepoint-application-page.md).  
  
## <a name="see-also"></a>См. также
 [Создание страниц приложений для SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)   
 [Пошаговое руководство: Создание страницы приложения SharePoint](../sharepoint/walkthrough-creating-a-sharepoint-application-page.md)  
  
