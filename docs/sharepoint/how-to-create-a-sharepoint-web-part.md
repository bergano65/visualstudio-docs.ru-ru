---
title: Как создать веб-часть SharePoint | Документация Майкрософт
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 2a8c02cce2f55374b4d62ba5663e8b3fe85b55b5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "86016441"
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

6. В **Обозреватель решений**откройте файл кода для только что созданной веб-части.

     Например, если веб-часть имеет имя *WebPart1*, откройте *WebPart1. vb* (в Visual Basic) или *WebPart1.CS* (в C#).

7. В файле кода добавьте элементы управления в метод <xref:System.Web.UI.Control.CreateChildControls%2A>.

     Пример см. в разделе [Пошаговое руководство. Создание веб-части для SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md).

## <a name="see-also"></a>См. также раздел
- [Создание веб-частей для SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)
- [Инструкции. Создание веб-части SharePoint с помощью конструктора](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)
- [Пошаговое руководство. Создание веб-части для SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)
- [Пошаговое руководство. Создание веб-части для SharePoint с помощью конструктора](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)
