---
title: Как создать веб-часть SharePoint | Документация Майкрософт
description: Создание и Настройка веб-части с помощью конструктора или Добавление элемента веб-части в любой проект SharePoint и последующее изменение файла кода для веб-части.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Web Parts [SharePoint development in Visual Studio], adding
- Web Parts [SharePoint development in Visual Studio], creating
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: f15cd788d19540bdea416b36ab0f8e8d8aa95e3a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99925594"
---
# <a name="how-to-create-a-sharepoint-web-part"></a>Как создать веб-часть SharePoint
  Вы можете создать и настроить веб-часть, добавив элемент **веб-части** в любой проект SharePoint, а затем отредактировав файл кода для веб-части или с помощью конструктора. Дополнительные сведения см. в разделе [инструкции. Создание веб-части SharePoint с помощью конструктора](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md).

### <a name="to-create-a-sharepoint-web-part"></a>Создание веб-части SharePoint

1. Создайте или откройте проект SharePoint.

     Дополнительные сведения см. в разделе [проект SharePoint и шаблоны элементов проектов](../sharepoint/sharepoint-project-and-project-item-templates.md).

2. Выберите узел проекта SharePoint в **Обозреватель решений** а затем выберите **проект**  >  **Добавить новый элемент**.

3. В диалоговом окне **Добавление нового элемента** разверните узел **SharePoint** и выберите узел **2010** .

4. В списке шаблонов SharePoint выберите **веб-часть**.

5. В поле **имя** укажите имя веб-части, а затем нажмите кнопку **Добавить** .

     Веб-часть отображается в **Обозреватель решений**. Дополнительные сведения о файлах, включаемых в веб-часть, см. в разделе [Создание веб-частей для SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md).

6. В **Обозреватель решений** откройте файл кода для только что созданной веб-части.

     Например, если веб-часть имеет имя *WebPart1*, откройте *WebPart1. vb* (в Visual Basic) или *WebPart1.CS* (в C#).

7. В файле кода добавьте элементы управления в метод <xref:System.Web.UI.Control.CreateChildControls%2A>.

     Пример см. в разделе [Пошаговое руководство. Создание веб-части для SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md).

## <a name="see-also"></a>См. также раздел
- [Создание веб-частей для SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)
- [Практическое руководство. Создание веб-части SharePoint с помощью конструктора](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)
- [Пошаговое руководство: создание веб-части для SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)
- [Пошаговое руководство: создание веб-части для SharePoint с помощью конструктора](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)
