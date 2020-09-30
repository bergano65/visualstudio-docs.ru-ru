---
title: Создание пользовательского элемента управления для страницы приложения SharePoint или веб-части
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- user controls [SharePoint development in Visual Studio], creating
- user controls [SharePoint development in Visual Studio], adding
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b9c8a99562d937d7b10c3539888c2dd62eb1d1da
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/30/2020
ms.locfileid: "91584104"
---
# <a name="how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part"></a>Практическое руководство. Создание пользовательского элемента управления для страницы приложения или веб-части SharePoint
  Можно создавать пользовательские элементы управления, которые предоставляют пользовательские функции для решения SharePoint, и эти функции можно повторно использовать в проекте. Можно включить пользовательские элементы управления в веб-часть или страницу приложения, добавить другие элементы управления ASP.NET и SharePoint и определить свойства и методы для элемента управления. Дополнительные сведения о пользовательских элементах управления см. в разделе [Создание многократно используемых элементов управления для веб-частей или страниц приложений](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md) , а также [пользовательских элементов управления и серверных элементов управления в SharePoint](https://blogs.msdn.microsoft.com/kaevans/2011/04/28/user-controls-and-server-controls-in-sharepoint/).

### <a name="to-create-a-user-control-for-sharepoint"></a>Создание пользовательского элемента управления для SharePoint

1. Откройте или создайте проект SharePoint в Visual Studio.

     См. раздел [шаблоны проектов и элементов проектов SharePoint](../sharepoint/sharepoint-project-and-project-item-templates.md).

2. В области **Обозреватель решений**выберите узел проекта.

3. В строке меню выберите **проект**  >  **Добавить новый элемент**.

     Откроется диалоговое окно **Добавление нового элемента**.

4. В области **установленные** выберите узел **Office/SharePoint** .

5. В списке шаблонов SharePoint выберите **Пользовательский элемент управления (только для решения фермы)**.

    > [!NOTE]
    > Пользовательские элементы управления работают только в решениях фермы.

6. В поле **имя** укажите имя пользовательского элемента управления, а затем нажмите кнопку **Добавить** .

     Visual Studio добавляет в проект несколько папок и файлов. Дополнительные сведения об этих файлах см. в разделе [Создание многократно используемых элементов управления для веб-частей или страниц приложений](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md).

     По умолчанию файл пользовательского элемента управления отображается в представлении **исходного кода** конструктора Visual Web Developer. В этом представлении можно редактировать XML-разметку элемента управления. Можно переключиться в режим **конструктора** , если требуется визуально спроектировать элемент управления, перетаскивая элементы управления из **панели элементов**. См. раздел [Конструктор веб-страниц](/previous-versions/aspnet/ms178149\(v\=vs.100\)).

7. Если требуется обрабатывать события, происходящие в элементе управления, добавьте код в файл кода пользовательского элемента управления.

     Этот файл отображается в **Обозреватель решений** в файле пользовательского элемента управления и имеет расширение *CS* или *VB* в зависимости от языка проекта.

## <a name="see-also"></a>См. также
- [Создание многократно используемых элементов управления для веб-частей или страниц приложений](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)
- [Создание страниц приложений для SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)
- [Создание веб-частей для SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)
