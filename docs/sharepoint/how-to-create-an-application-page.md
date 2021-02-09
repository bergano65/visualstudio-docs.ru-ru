---
title: Как создать страницу приложения | Документация Майкрософт
description: Создание веб-страницы ASP.NET (также известной как страница приложения) в Visual Studio для одного или нескольких сайтов SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application pages [SharePoint development in Visual Studio], adding
- application pages [SharePoint development in Visual Studio], creating
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 74e7aab4cbc012afbf045672dbf4af248ada4c61
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99925623"
---
# <a name="how-to-create-an-application-page"></a>Практическое руководство. Создание страницы приложения
  Можно создать веб-страницу ASP.NET для одного или нескольких сайтов SharePoint. В SharePoint эти страницы называются страницами приложения. В отличие от страницы сайта, страница приложения содержит код, который выполняется за страницей. Дополнительные сведения см. в разделе [Создание страниц приложений для SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).

### <a name="to-create-an-application-page"></a>Создание страницы приложения

1. Откройте или создайте проект SharePoint в Visual Studio.

     Дополнительные сведения см. в разделе [проект SharePoint и шаблоны элементов проектов](../sharepoint/sharepoint-project-and-project-item-templates.md).

2. В области **Обозреватель решений** выберите узел проекта.

3. В строке меню выберите **Проект** > **Добавить новый элемент**.

4. В диалоговом окне **Добавление нового элемента** разверните узел **SharePoint** и выберите элемент **2010** .

5. В списке шаблонов SharePoint выберите **страница приложение**.

6. В поле **имя** укажите имя страницы приложения, а затем нажмите кнопку **Добавить** .

     Visual Studio добавляет в проект несколько папок и файлов. Дополнительные сведения об этих файлах см. в разделе [Создание страниц приложений для SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).

     В представлении **исходного кода** конструктора Visual Web Developer отображается файл подкачки ASP.NET. Страницу можно спроектировать, добавив элементы управления из **панели элементов** и поместив их на заполнители содержимого. Дополнительные сведения см. в разделе [представление исходного кода, конструктор веб-страниц](/previous-versions/aspnet/ms178154\(v\=vs.100\)).

7. Если требуется обработку событий элемента управления, добавьте код в файл кода для страницы приложения.

     Файл кода отображается, если развернуть узел для файла подкачки ASP.NET и имеет расширение *CS* или *VB* в зависимости от языка проекта. Полный пример создания страницы приложения см. в разделе [Пошаговое руководство. Создание страницы приложения SharePoint](../sharepoint/walkthrough-creating-a-sharepoint-application-page.md).

## <a name="see-also"></a>См. также раздел
- [Создание страниц приложений для SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)
- [Пошаговое руководство: Создание страницы приложения SharePoint](../sharepoint/walkthrough-creating-a-sharepoint-application-page.md)
