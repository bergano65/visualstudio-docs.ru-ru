---
title: Как выполнить Создание веб-части SharePoint | Документация Майкрософт
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Web Parts [SharePoint development in Visual Studio], adding
- Web Parts [SharePoint development in Visual Studio], creating
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b66cd0b380612502bb982efd464607a4759f9c4b
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/24/2019
ms.locfileid: "54870796"
---
# <a name="how-to-create-a-sharepoint-web-part"></a>Как выполнить Создание веб-части SharePoint
  Можно создать и настроить веб-часть, добавив **веб-часть** элемент в любой проект SharePoint, а затем изменив файл кода для веб-части, или с помощью конструктора. Дополнительные сведения см. в разделе [Как Создание веб-части SharePoint с помощью конструктора](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md).  
  
### <a name="to-create-a-sharepoint-web-part"></a>Для создания веб-части SharePoint
  
1.  Создайте или откройте проект SharePoint.  
  
     Дополнительные сведения см. в разделе [SharePoint проект и проект шаблоны элементов](../sharepoint/sharepoint-project-and-project-item-templates.md).  
  
2.  Выберите узел проекта SharePoint в **обозревателе решений** и выберите **проекта** > **Добавление нового элемента**.  
  
3.  В **Добавление нового элемента** диалоговое окно последовательно раскройте элементы **SharePoint** узел, а затем выберите **2010** узел.  
  
4.  В списке шаблонов SharePoint выберите **веб-часть**.  
  
5.  В **имя** , укажите имя для веб-части и затем выберите **добавить** кнопки.  
  
     Веб-часть появляется в **обозревателе решений**. Дополнительные сведения о файлах, которые включает в себя веб-часть, см. в разделе [Создание веб-частей для SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md).  
  
6.  В **обозревателе решений**, откройте файл кода для веб-части, которую вы только что создали.  
  
     Например, если веб-часть называется *WebPart1*откройте *WebPart1.vb* (в Visual Basic) или *WebPart1.cs* (в C#).  
  
7.  В файле кода добавьте элементы управления в метод <xref:System.Web.UI.Control.CreateChildControls%2A>.  
  
     Например, см. в разделе [Пошаговое руководство: Создание веб-части для SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md).  
  
## <a name="see-also"></a>См. также
 [Создание веб-частей для SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)   
 [Практическое руководство. Создание веб-части SharePoint с помощью конструктора](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)   
 [Пошаговое руководство: Создание веб-части для SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)   
 [Пошаговое руководство: Создание веб-части для SharePoint с помощью конструктора](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)  
