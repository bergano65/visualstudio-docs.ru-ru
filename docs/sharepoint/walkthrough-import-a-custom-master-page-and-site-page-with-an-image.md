---
title: Импорт пользовательской главной страницы & страницу сайта с изображением
description: В этом пошаговом руководстве вы импортируете настраиваемую главную страницу SharePoint и страницу сайта с изображением в проект Visual Studio SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, importing items
- importing items [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 503ffc733a408787e7ecf188d893039759819c6d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99952581"
---
# <a name="walkthrough-import-a-custom-master-page-and-site-page-with-an-image"></a>Пошаговое руководство. Импорт настраиваемой главной страницы и страницы сайта с помощью изображения
  В этом пошаговом руководстве показано, как импортировать настраиваемую главную страницу SharePoint и страницу сайта с изображением в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] проект SharePoint.

 В пошаговом руководстве показано, как выполнять следующие задачи:

- Создание настраиваемой главной страницы и страницы сайта с помощью изображения в SharePoint Designer.

- Экспорт пользовательской главной страницы, изображения и страницы сайта в файл решения SharePoint (*. wsp*).

- Импортируйте и разверните *WSP* -файл в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] проект SharePoint с помощью проекта Импорт пакета решения SharePoint.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Предварительные требования
 Для выполнения инструкций этого пошагового руководства необходимы следующие компоненты:

- Поддерживаемые выпуски [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] и SharePoint.

- приведенному.

- SharePoint Designer 2010.

## <a name="create-items-in-sharepoint-designer"></a>Создание элементов в SharePoint Designer
 В этом примере показано, как создать три элемента в SharePoint Designer для экспорта: настраиваемую главную страницу, страницу сайта, ссылающуюся на настраиваемую главную страницу, и файл изображения, который будет отображаться на странице сайта. Образ добавляется в папку/Images/в SharePoint.

#### <a name="to-create-a-custom-master-page-in-sharepoint-designer"></a>Создание пользовательской главной страницы в SharePoint Designer

1. В SharePoint Designer в области навигации выберите объект сайта **главные страницы** .

2. На ленте **главные страницы** выберите **пустая эталонная страница**.

3. Выберите новую главную страницу, а затем на ленте **главные страницы** выберите **изменить файл**.

4. В нижней части SharePoint Designer перейдите на вкладку **код** .

5. Замените существующую разметку следующей разметкой.

    ```aspx-csharp
    <%@ Master Language="C#" %>
    <%@ Register tagprefix="SharePoint" namespace="Microsoft.SharePoint.WebControls" assembly="Microsoft.SharePoint, Version=14.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" %>
    <html dir="ltr">
    <head runat="server">
    <meta http-equiv="Content-Type" content="text/html; charset=utf-8">
    <SharePoint:RobotsMetaTag runat="server" __designer:Preview="" __designer:Values="<P N='InDesign' T='False' /><P N='ID' T='ctl00' /><P N='Page' ID='1' /><P N='TemplateControl' ID='2' /><P N='AppRelativeTemplateSourceDirectory' R='-1' />"></SharePoint:RobotsMetaTag>
    <title>Web Page</title>
    </head>
    <body>
    <form id="form1" runat="server">
    <asp:ContentPlaceHolder id="ContentPlaceHolderMain"
            runat="server">
          </asp:ContentPlaceHolder>
    </form>
    </body>
    </html>
    ```

6. Сохраните страницу, перейдите на вкладку **главные страницы** и переименуйте главную страницу как **mybasic1. master**.

## <a name="add-an-image-to-the-content-database-in-sharepoint-designer"></a>Добавление изображения в базу данных содержимого в SharePoint Designer
 Теперь можно добавить изображение, которое будет отображаться на странице сайта. Образ развертывается в базе данных содержимого SharePoint.

#### <a name="to-add-an-image-to-the-content-database-in-sharepoint-designer"></a>Добавление изображения в базу данных содержимого в SharePoint Designer

1. В области навигации выберите объект сайт **все файлы** , а затем в древовидном представлении выберите папку **изображения** .

2. На ленте **все файлы** выберите **Импорт файлов**, выберите нужный файл, а затем нажмите кнопку **ОК** . В этом примере файл называется **myimg1.png**.

     При необходимости можно создать вложенную папку, помогающую упорядочить изображения.

3. Закройте диалоговое окно **Импорт** .

## <a name="create-a-site-page"></a>Создание страницы сайта
 На этой основной странице сайта используется пользовательская Главная страница и отображается изображение, добавленное на предыдущем шаге.

#### <a name="to-create-a-site-page"></a>Создание страницы сайта

1. В области навигации выберите объект **страницы сайта** .

2. На ленте **страницы** нажмите кнопку **страница** , выберите тип страницы **ASPX** и назовите новый файл **MyContentPage1. aspx**.

     При необходимости можно создать вложенную папку, помогающую упорядочить страницы сайта.

3. В списке страницы сайта выберите **MyContentPage1. aspx** , чтобы открыть страницу свойств, а затем в нижней части страницы щелкните ссылку **изменить файл** .

     Если появится сообщение и говорится, что эта страница не содержит регионы, доступные для изменения в защищенном режиме, и спрашивает, нужно ли открывать эту страницу в расширенном режиме, нажмите кнопку **Да** .

4. В нижней части страницы нажмите кнопку **Code (код** ).

5. Замените существующую разметку следующей разметкой.

    ```aspx-csharp
    <%@ Import Namespace="Microsoft.SharePoint.ApplicationPages" %>
    <%@ Register Tagprefix="SharePoint" Namespace="Microsoft.SharePoint.WebControls" Assembly="Microsoft.SharePoint, Version=14.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" %>
    <%@ Register Tagprefix="Utilities" Namespace="Microsoft.SharePoint.Utilities" Assembly="Microsoft.SharePoint, Version=14.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" %>
    <%@ Register Tagprefix="asp" Namespace="System.Web.UI" Assembly="System.Web.Extensions, Version=3.5.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" %>
    <%@ Import Namespace="Microsoft.SharePoint" %>
    <%@ Assembly Name="Microsoft.Web.CommandUI, Version=14.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" %>
    <%@ Page Language="C#" Inherits="Microsoft.SharePoint.WebControls.LayoutsPageBase" MasterPageFile="../_catalogs/masterpage/mybasic1.master" meta:progid="SharePoint.WebPartPage.Document" %>

    <asp:Content ID="Main" ContentPlaceHolderID="ContentPlaceHolderMain" runat="server">
    <img alt="My Image" longdesc="My image from images folder" src="../images/myimg1.png" />
    </asp:Content>
    ```

6. Сохраните обновленную страницу сайта.

## <a name="export-the-items-from-sharepoint"></a>Экспорт элементов из SharePoint
 Экспортируйте элементы из SharePoint в файл решения SharePoint (*. wsp*).

#### <a name="to-export-items-from-sharepoint-designer"></a>Экспорт элементов из SharePoint Designer

1. В SharePoint Designer в области навигации выберите объект **сайт группы** , а затем на ленте **сайта** выберите **Сохранить как шаблон**.

2. В диалоговом окне **Сохранить как шаблон** введите имя файла и имя шаблона, установите флажок **включить содержимое** и нажмите кнопку **ОК** .

     Это позволит сохранить содержимое сайта в *WSP* -файле.

3. После экспорта решения щелкните ссылку **Коллекция решений** , чтобы отобразить список доступных файлов решения.

4. Откройте контекстное меню для нового *wspного* файла, а затем выберите **Сохранить объект как** , чтобы сохранить его в системе.

## <a name="import-the-items-into-visual-studio"></a>Импорт элементов в Visual Studio
 Импортируйте *WSP* файл в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . После импорта вы можете настраивать содержимое, добавлять новые элементы, а затем выполнять развертывание.

#### <a name="to-import-items-from-the-wsp-file-into-visual-studio"></a>Импорт элементов из WSP файла в Visual Studio

1. В [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Создайте проект **импорта пакета решения SharePoint 2010** .

2. На странице **Выбор элементов для импорта** в разделе **модуль** в столбце **тип** установите флажки только для файлов, перечисленных в следующей таблице для импорта.

   | Имя файла | Описание |
   |------------------------|-----------------------------------------------|
   | \_каталогсмастерпаже\_ | Настраиваемая Главная страница. |
   | images_ | Файл изображения в файловой системе SharePoint. |
   | SitePages_ | Страница сайта. |

3. Нажмите кнопку **Готово** , чтобы импортировать выбранные элементы.

4. В **Обозреватель решений** выберите \_ \_ узел каталогсмастерпаже и задайте для свойства " **разрешение конфликта развертывания** " значение " **автоматически**".

    Это гарантирует, что конфликты развертывания разрешаются автоматически.

5. Если новая эталонная страница имеет то же имя, что и существующая страница, убедитесь, что существующая страница не помечена как эталонная страница по умолчанию или пользовательская Главная страница в SharePoint Designer.

    Если существующая эталонная страница помечена как эталонная страница по умолчанию или настраиваемая эталонная страница, будет выведено сообщение об ошибке развертывания, в котором говорится, что Главная страница не может быть удалена. Чтобы избежать этой проблемы, сделайте следующее:

   - Если существующая эталонная страница задана как эталонная страница по умолчанию, временно установите другую главную страницу в качестве главной страницы по умолчанию. После развертывания файлов в SharePoint задайте новую главную страницу в качестве главной страницы по умолчанию.

   - Если существующая эталонная страница задана как пользовательская Главная страница, временно установите другую главную страницу в качестве пользовательской главной страницы. После развертывания файлов в SharePoint задайте новую главную страницу в качестве пользовательской главной страницы.

6. В строке меню выберите **Сборка**  >  **Развернуть решение**.

7. Откройте сайт SharePoint, чтобы просмотреть развернутые элементы.

   Альтернативный способ импорта [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] и развертывания файлов в SharePoint — Добавление файлов в модули в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)][Как импортировать главную страницу или тему](../sharepoint/how-to-import-a-master-page-or-theme.md) и [использовать модули для включения файлов в решение](../sharepoint/using-modules-to-include-files-in-the-solution.md).

## <a name="see-also"></a>См. также раздел
- [Импорт элементов с существующего сайта SharePoint](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)
- [Разработка решений SharePoint](../sharepoint/developing-sharepoint-solutions.md)
- [Создание многократно используемых элементов управления для веб-частей или страниц приложений](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)
