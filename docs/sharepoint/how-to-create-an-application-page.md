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
ms.openlocfilehash: eefbb12584cdff2bb32b9d4406c916969ec435c4
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/29/2018
ms.locfileid: "37119377"
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
  
     В **источника** отображается представление конструктора Visual Web Developer, файле страницы ASP.NET. Проектировать страницу можно, добавив элементы управления из **элементов** и их размещения на место заполнителей содержимого. Дополнительные сведения см. в разделе [представление источника, конструктор веб-страницы](http://msdn.microsoft.com/en-us/5911396b-fe51-4150-9ff1-b085f812862f).  
  
7.  Если вы хотите обрабатывать события элемента управления, добавьте код в файл кода страницы приложения.  
  
     Файл кода появляется, если развернуть узел файла страницы ASP.NET и имеет *.cs* или *.vb* расширения, в зависимости от языка проекта. End-to-end пример того, как создать страницу приложения, см. в разделе [Пошаговое руководство: Создание страницы приложения SharePoint](../sharepoint/walkthrough-creating-a-sharepoint-application-page.md).  
  
## <a name="see-also"></a>См. также
 [Создание страниц приложений для SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)   
 [Пошаговое руководство: Создание страницы приложения SharePoint](../sharepoint/walkthrough-creating-a-sharepoint-application-page.md)  
  
