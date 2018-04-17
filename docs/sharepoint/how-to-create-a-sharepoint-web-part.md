---
title: 'Как: Создание веб-части SharePoint | Документы Microsoft'
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
- Web Parts [SharePoint development in Visual Studio], adding
- Web Parts [SharePoint development in Visual Studio], creating
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 708a1b1a0b64dbed5c02e6fcaf7da9e8892f5664
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-create-a-sharepoint-web-part"></a>Практическое руководство. Создание веб-части SharePoint
  Можно создать и настроить веб-части путем добавления **веб-часть** в любой проект SharePoint и последующего изменения файла кода веб-части либо с помощью конструктора. Дополнительные сведения см. в разделе [как: Создание веб-части SharePoint с помощью конструктора](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md).  
  
### <a name="to-create-a-sharepoint-web-part"></a>Для создания веб-части SharePoint  
  
1.  Создайте или откройте проект SharePoint.  
  
     Дополнительные сведения см. в разделе [проект SharePoint и шаблоны элементов проекта](../sharepoint/sharepoint-project-and-project-item-templates.md).  
  
2.  Выберите узел проекта SharePoint в **обозревателе решений** и выберите **проекта**, **Добавление нового элемента**.  
  
3.  В **Добавление нового элемента** диалогового окна разверните **SharePoint** узел и выберите **2010** узла.  
  
4.  В списке шаблонов SharePoint выберите **веб-часть**.  
  
5.  В **имя** укажите имя веб-части и выберите **добавить** кнопки.  
  
     Веб-часть появляется в **обозревателе решений**. Дополнительные сведения о файлах, которые веб-часть включает см. в разделе [Создание веб-частей для SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md).  
  
6.  В **обозревателе решений**, откройте файл кода для веб-части, которую вы только что создали.  
  
     Например, если веб-часть называется WebPart1, откройте WebPart1.vb (в Visual Basic) или WebPart1.cs (в C#).  
  
7.  В файле кода добавьте элементы управления в метод <xref:System.Web.UI.Control.CreateChildControls%2A>.  
  
     Пример см. в разделе [Пошаговое руководство: Создание веб-части для SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md).  
  
## <a name="see-also"></a>См. также  
 [Создание веб-частей для SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)   
 [Как: Создание веб-части SharePoint с помощью конструктора](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)   
 [Пошаговое руководство: Создание веб-части для SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)   
 [Пошаговое руководство. Создание веб-части для SharePoint с помощью конструктора](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)  
  
  