---
title: "Как: создать пользовательский элемент управления для страницы приложения SharePoint или веб-части | Документы Microsoft"
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
- user controls [SharePoint development in Visual Studio], creating
- user controls [SharePoint development in Visual Studio], adding
ms.assetid: 492ea376-7188-4b5a-a2eb-adc0e3f51484
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 1c6384ce4437290c0baa5ea1438a0751b4ec1fcf
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part"></a>Практическое руководство. Создание пользовательского элемента управления для страницы приложения или веб-части SharePoint
  Можно создавать пользовательские элементы управления, которые предоставляют пользовательские функции для решения SharePoint, и эти функции можно повторно использовать в проекте. Можно включить пользовательские элементы управления в веб-часть или страницу приложения, добавить другие элементы управления ASP.NET и SharePoint и определить свойства и методы для элемента управления. Дополнительные сведения о пользовательских элементах управления см. в разделе [создание для повторного использования элементов управления для веб-частей или страниц приложений](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md) и [пользовательских элементов управления и серверных элементов управления в SharePoint](http://blogs.msdn.com/b/kaevans/archive/2011/04/28/user-controls-and-server-controls-in-sharepoint.aspx).  
  
### <a name="to-create-a-user-control-for-sharepoint"></a>Чтобы создать пользовательский элемент управления для SharePoint  
  
1.  Откройте или создайте проект SharePoint в Visual Studio.  
  
     В разделе [шаблоны элементов проекта SharePoint и проект](../sharepoint/sharepoint-project-and-project-item-templates.md).  
  
2.  В области **Обозреватель решений**выберите узел проекта.  
  
3.  В строке меню выберите **проекта**, **Добавление нового элемента**.  
  
     Откроется диалоговое окно **Добавление нового элемента**.  
  
4.  В **установленные** области, выберите **Office/SharePoint** узла.  
  
5.  В списке шаблонов SharePoint выберите **пользовательский элемент управления (только для решения фермы)**.  
  
    > [!NOTE]  
    >  Пользовательские элементы управления работают только в решениях фермы.  
  
6.  В **имя** укажите имя для пользовательского элемента управления и выберите **добавить** кнопки.  
  
     Visual Studio добавляет несколько файлов и папок в проект. Дополнительные сведения об этих файлах см. в разделе [создание для повторного использования элементов управления для веб-частей или страниц приложений](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md).  
  
     По умолчанию файл пользовательского элемента управления отображается в **источника** представлении конструктора Visual Web Developer. В этом представлении можно редактировать XML-разметку элемента управления. Можно переключиться на **разработки** просмотра, если необходимо визуально разработать элемент управления, перетащив элементы управления из **элементов**. В разделе [режим конструктора, конструктор веб-страниц](http://msdn.microsoft.com/en-us/d8f2270a-357d-40a4-9b39-1a3f2366216d).  
  
7.  Если требуется обрабатывать события, происходящие в элементе управления, добавьте код в файл кода пользовательского элемента управления.  
  
     Этот файл отображается в **обозревателе решений** в файл пользовательского элемента управления и имеет расширение CS или VB в зависимости от языка проекта.  
  
## <a name="see-also"></a>См. также  
 [Создание многократно используемых элементов управления для веб-частей или страниц приложений](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)   
 [Создание страниц приложений для SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)   
 [Создание веб-частей для SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)  
  
  