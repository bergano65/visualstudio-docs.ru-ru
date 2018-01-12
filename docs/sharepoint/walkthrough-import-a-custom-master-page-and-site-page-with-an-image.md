---
title: "Пошаговое руководство: Импорт пользовательской главной страницы и страницы с изображением сайта | Документы Microsoft"
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
helpviewer_keywords:
- SharePoint development in Visual Studio, importing items
- importing items [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 544c3c727046fdcabcde90f221f4b630c11cf29f
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/10/2018
---
# <a name="walkthrough-import-a-custom-master-page-and-site-page-with-an-image"></a>Пошаговое руководство. Импорт пользовательской главной страницы и страницы сайта с изображением
  В этом пошаговом руководстве показано, как импортировать пользовательскую главную страницу и страницу сайта с изображением в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] проект SharePoint.  
  
 В пошаговом руководстве показано, как выполнять следующие задачи:  
  
-   Создайте пользовательскую главную страницу и страницу сайта с изображением в SharePoint Designer.  
  
-   Экспорт пользовательской главной страницы, изображения и страницы сайта в SharePoint файл решения (WSP-файл).  
  
-   Импорт и развертывание WSP-файла в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] проект SharePoint с помощью проекта Импорт пакета решения SharePoint.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Предварительные требования  
 Необходимо иметь следующие компоненты для выполнения данного пошагового руководства.  
  
-   Поддерживаемые выпуски [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] и SharePoint. [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)][Требования по разработке решений SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Visual Studio.  
  
-   В SharePoint Designer 2010.  
  
## <a name="create-items-in-sharepoint-designer"></a>Создание элементов в SharePoint Designer  
 В этом примере показано, как создать три элемента в SharePoint Designer для экспорта: пользовательскую эталонную страницу, страницу сайта, который ссылается на пользовательскую главную страницу и файл изображения, отображаемые на странице сайта. Изображение добавляется в папку /images/ в SharePoint.  
  
#### <a name="to-create-a-custom-master-page-in-sharepoint-designer"></a>Чтобы создать пользовательскую эталонную страницу в конструкторе SharePoint  
  
1.  В SharePoint Designer в области навигации выберите **главных страниц** объекта сайта.  
  
2.  На **главных страниц** ленте, выберите **пустой главной страницы**.  
  
3.  Выберите новую эталонную страницу, а затем на **главных страниц** ленте, выберите **изменить файл**.  
  
4.  В нижней части SharePoint Designer, выберите **кода** вкладки.  
  
5.  Замените существующую разметку следующей разметкой.  
  
    ```  
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
  
6.  Сохраните страницу, выберите **главных страниц** и переименуйте эталонную страницу **mybasic1.master**.  
  
## <a name="add-an-image-to-the-content-database-in-sharepoint-designer"></a>Добавить изображение к базе данных содержимого в SharePoint Designer  
 Теперь можно добавить изображения, отображаемого на странице сайта. Изображение разворачивается в базе данных содержимого SharePoint.  
  
#### <a name="to-add-an-image-to-the-content-database-in-sharepoint-designer"></a>Чтобы добавить изображение к базе данных содержимого в SharePoint Designer  
  
1.  В области навигации выберите **все файлы** объект сайта, а затем в представлении дерева выберите **изображения** папки.  
  
2.  На **все файлы** ленте, выберите **импортировать файлы**, выберите файл по своему усмотрению, а затем выберите **ОК** кнопки. В этом примере файл называется **myimg1.png**.  
  
     При необходимости можно создать вложенную папку для упорядочивания изображений.  
  
3.  Закрыть **импорта** диалоговое окно.  
  
## <a name="create-a-site-page"></a>Создание страницы сайта  
 Эта основная страница использует пользовательскую главную страницу и отображает изображение, добавленного на предыдущем шаге.  
  
#### <a name="to-create-a-site-page"></a>Создание страницы сайта  
  
1.  В области навигации выберите **страниц сайта** объекта.  
  
2.  На **страниц** ленте, выберите **страницы** , выберите **ASPX** типа страницы и введите имя нового файла **mycontentpage1.aspx**.  
  
     При необходимости можно создать вложенную папку для упорядочивания страниц сайта.  
  
3.  В списке страниц сайта выберите **MyContentPage1.aspx** для открытия страницы свойств и выберите в нижней части страницы, **редактирование файла** ссылку.  
  
     Если появится сообщение и говорит, что эта страница не содержит какие-либо области, которые можно редактировать в безопасном режиме с вопросом, следует открыть эту страницу в расширенном режиме, выберите **Да** кнопки.  
  
4.  В нижней части страницы, выбрать **кода** кнопки.  
  
5.  Замените существующую разметку следующей разметкой.  
  
    ```  
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
  
6.  Сохраните страницу обновленного узла.  
  
## <a name="export-the-items-from-sharepoint"></a>Экспорт элементов из SharePoint  
 Элементы из SharePoint можно экспортируйте в файл решения (WSP-файл) SharePoint.  
  
#### <a name="to-export-items-from-sharepoint-designer"></a>Для экспорта элементов из SharePoint Designer  
  
1.  В SharePoint Designer в области навигации выберите **узла группы** объекта, а затем на **сайта** ленте, выберите **Сохранить как шаблон**.  
  
2.  В **Сохранить как шаблон** диалоговом окне введите имя файла и выберите имя шаблона **содержимого** флажок и нажмите кнопку **ОК** кнопки.  
  
     Это сохраняет содержимое узла в WSP-файл.  
  
3.  После экспорта решения, выберите **коллекции решений** ссылку для отображения списка имеющихся файлов решения.  
  
4.  Откройте контекстное меню для нового WSP-файла и выберите **сохранить объект как** сохранить его в систему.  
  
## <a name="import-the-items-into-visual-studio"></a>Импорт элементов в Visual Studio  
 Импортируйте WSP-файл в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. После импорта вы можете настраивать содержимое, добавлять новые элементы, а затем выполнять развертывание.  
  
#### <a name="to-import-items-from-the-wsp-file-into-visual-studio"></a>Импорт элементов из WSP-файл в Visual Studio  
  
1.  В [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], создайте **Импорт пакета решения SharePoint 2010** проекта.  
  
2.  На **выберите элементы для импорта** в разделе **модуль** в **тип** столбец, установите флажки для только файлы в следующей таблице для импорта.  
  
    |Имя файла|Описание:|  
    |---------------|-----------------|  
    |_catalogsmasterpage\_|Пользовательская главная страница.|  
    |images_|Файл изображения в файловой системе SharePoint.|  
    |SitePages_|Страница сайта.|  
  
3.  Выберите **Готово** кнопку, чтобы импортировать выбранные элементы.  
  
4.  В **обозревателе решений**, выберите _catalogsmasterpage\_ узла и задать значение его **Устранение конфликта развертывания** свойства **автоматического**.  
  
     Это гарантирует, что автоматически разрешить конфликты развертывания.  
  
5.  Если новой главной страницы имеет имя, совпадающее с именем существующей страницы, убедитесь, что существующей страницы не помечен как Главная страница по умолчанию или пользовательской главной страницы в конструкторе SharePoint.  
  
     Если существующая главная страница помечена как Главная страница по умолчанию или пользовательской главной страницы, вы получите ошибку развертывания о том, что нельзя удалить главную страницу. Чтобы избежать этой проблемы, выполните это:  
  
    -   Если существующая главная страница помечена как Главная страница по умолчанию, временно сделайте другую главную страницу главной страницей по умолчанию. После развертывания файлов в SharePoint, задайте новой главной страницы главной страницей по умолчанию.  
  
    -   Если существующая главная страница помечена как пользовательская главная страница, временно сделайте другую главную страницу пользовательской главной страницей. После развертывания файлов в SharePoint, задайте в качестве пользовательской главной страницы новой главной страницы.  
  
6.  В строке меню выберите **построения**, **развернуть решение**.  
  
7.  Откройте сайт SharePoint для просмотра развернутых элементов.  
  
 Альтернативный способ импорта файлов в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] и развертывания их в SharePoint состоит в добавлении файлов в модули [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)][Как: Импорт главной страницы или темы](../sharepoint/how-to-import-a-master-page-or-theme.md) и [использование модулей для включения файлов в решении](../sharepoint/using-modules-to-include-files-in-the-solution.md).  
  
## <a name="see-also"></a>См. также  
 [Импорт элементов из существующего сайта SharePoint](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)   
 [Разработка решений SharePoint](../sharepoint/developing-sharepoint-solutions.md)   
 [Создание повторно используемых элементов управления для веб-частей или страниц приложений](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)  
  
  