---
title: Практическое руководство. Создание страницы приложения | Документация Майкрософт
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application pages [SharePoint development in Visual Studio], adding
- application pages [SharePoint development in Visual Studio], creating
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 16c772ac411669cde082475840197ec2f12c9fb2
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56646542"
---
# <a name="how-to-create-an-application-page"></a>Практическое руководство. Создание страницы приложения
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
- [Создание страниц приложений для SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)
- [Пошаговое руководство: Создание страницы приложения SharePoint](../sharepoint/walkthrough-creating-a-sharepoint-application-page.md)
