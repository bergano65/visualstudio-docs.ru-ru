---
title: 'Пошаговое руководство: Импорт пользовательской главной страницы и страницы сайта с изображением | Документация Майкрософт'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, importing items
- importing items [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: ea327f48bb1a1b04aa4b20601b8bdb3f7dfbb847
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "42634684"
---
# <a name="walkthrough-import-a-custom-master-page-and-site-page-with-an-image"></a>Пошаговое руководство: Импорт пользовательской главной страницы и страницы сайта с изображением
  В этом пошаговом руководстве показано, как импортировать настраиваемую эталонную страницу и страницу сайта с изображением в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] проекта SharePoint.  
  
 В пошаговом руководстве показано, как выполнять следующие задачи:  
  
-   Создайте пользовательскую главную страницу и страницу сайта, используя образ в SharePoint Designer.  
  
-   Экспорт пользовательской главной страницы, изображения и страницы сайта в решение SharePoint (*.wsp*) файла.  
  
-   Импорт и развертывание *.wsp* файл в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] проекта SharePoint с помощью проекта Импорт пакета решения SharePoint.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Предварительные требования  
 Необходимо иметь следующие компоненты для выполнения этого пошагового руководства:  
  
-   Поддерживаемые выпуски [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] и SharePoint.  
  
-   Visual Studio.  
  
-   SharePoint Designer 2010.  
  
## <a name="create-items-in-sharepoint-designer"></a>Создание элементов в SharePoint Designer
 В этом примере показано, как создать три элемента в SharePoint Designer для экспорта: пользовательскую главную страницу, страницу сайта, который ссылается на пользовательскую главную страницу и файл изображения для отображения на странице сайта. Изображение будет добавлено в папку /images/ в SharePoint.  
  
#### <a name="to-create-a-custom-master-page-in-sharepoint-designer"></a>Чтобы создать пользовательскую главную страницу в SharePoint Designer
  
1.  В SharePoint Designer в области навигации выберите **главные страницы** объект сайта.  
  
2.  На **главные страницы** ленте, выберите **пустая Эталонная страница**.  
  
3.  Выберите новую эталонную страницу, а затем на **главные страницы** ленте, выберите **изменить файл**.  
  
4.  В нижней части SharePoint Designer, выберите **кода** вкладки.  
  
5.  Замените существующую разметку следующей разметкой.  
  
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
  
6.  Сохраните страницу, выберите **главные страницы** вкладку и переименуйте эталонную страницу **mybasic1.master**.  
  
## <a name="add-an-image-to-the-content-database-in-sharepoint-designer"></a>Добавление изображения в базу данных содержимого в SharePoint Designer
 Теперь можно добавить изображения, отображаемого на странице сайта. Образ развертывается в базу данных содержимого SharePoint.  
  
#### <a name="to-add-an-image-to-the-content-database-in-sharepoint-designer"></a>Чтобы добавить изображение в базу данных содержимого в SharePoint Designer
  
1.  В области навигации выберите **все файлы** объект сайта, а затем в представлении в виде дерева выберите **образы** папки.  
  
2.  На **все файлы** ленте, выберите **импортировать файлы**, выберите файл по своему усмотрению, а затем выберите **ОК** кнопки. В этом примере этот файл имеет имя **myimg1.png**.  
  
     При необходимости можно создать вложенную папку для упорядочивания изображений.  
  
3.  Закрыть **импорта** диалоговое окно.  
  
## <a name="create-a-site-page"></a>Создание страницы сайта
 Эта основная страница использует пользовательскую главную страницу и отображает изображение, добавленного на предыдущем шаге.  
  
#### <a name="to-create-a-site-page"></a>Создание страницы сайта  
  
1.  В области навигации выберите **страницы сайта** объекта.  
  
2.  На **страниц** ленте, выберите **страницы** "Кнопка", выберите **ASPX** странице типа, а затем назовите новый файл **mycontentpage1.aspx**.  
  
     При необходимости можно создать вложенную папку для упрощения организации на страницах сайта.  
  
3.  В списке страниц сайта выберите **MyContentPage1.aspx** чтобы открыть страницу ее свойств и нажмите в нижней части страницы, **файла изменения** ссылку.  
  
     Если появится сообщение и говорит, что эта страница не содержит области, которые можно редактировать в безопасном режиме с спрашивается, хотите ли вы открыть эту страницу в расширенном режиме, выберите **Да** кнопки.  
  
4.  В нижней части страницы, выбрать **кода** кнопки.  
  
5.  Замените существующую разметку следующей разметкой.  
  
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
  
6.  Сохраните страницу обновленного сайта.  
  
## <a name="export-the-items-from-sharepoint"></a>Экспорт элементов из SharePoint
 Экспорт элементов из SharePoint в решение SharePoint (*.wsp*) файла.  
  
#### <a name="to-export-items-from-sharepoint-designer"></a>Для экспорта элементов из SharePoint Designer
  
1.  В SharePoint Designer в области навигации выберите **сайт группы** объекта, а затем на **сайта** ленте, выберите **Сохранить как шаблон**.  
  
2.  В **Сохранить как шаблон** диалогового окна введите имя файла и имя шаблона, выберите **содержимого** , а затем нажать **ОК** кнопки.  
  
     Это сохраняет содержимое узла в *.wsp* файл.  
  
3.  После экспорта решения, выберите **Solution Gallery** ссылку, чтобы отобразить список имеющихся файлов решения.  
  
4.  Откройте контекстное меню для нового *.wsp* файл, а затем выберите **сохранить объект как** сохранить его в систему.  
  
## <a name="import-the-items-into-visual-studio"></a>Импорт элементов в Visual Studio
 Импорт *.wsp* файл в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. После импорта вы можете настраивать содержимое, добавлять новые элементы, а затем выполнять развертывание.  
  
#### <a name="to-import-items-from-the-wsp-file-into-visual-studio"></a>Импорт элементов из WSP-файл в Visual Studio  
  
1.  В [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], создание **Импорт пакета решения SharePoint 2010** проекта.  
  
2.  На **выберите элементы для импорта** раздела **модуль** в **тип** столбца, установите флажки для файлов в следующей таблице для импорта.  
  
    |Имя файла|Описание:|  
    |---------------|-----------------|  
    |\_catalogsmasterpage\_|Пользовательскую главную страницу.|  
    |images_|Файл изображения в файловой системе SharePoint.|  
    |SitePages_|На странице сайта.|  
  
3.  Выберите **Готово** кнопку, чтобы импортировать выбранные элементы.  
  
4.  В **обозревателе решений**, выберите \_catalogsmasterpage\_ узел и установите для параметра его **Устранение конфликта развертывания** свойства **автоматического** .  
  
     Это гарантирует, что любые развертывания конфликты разрешаются автоматически.  
  
5.  Если новой главной страницы имеет имя, совпадающее с именем существующей страницы, убедитесь, что существующие страницы не помечен как Главная страница по умолчанию или пользовательской главной страницы в SharePoint Designer.  
  
     Если существующая главная страница помечена как Главная страница по умолчанию или пользовательской главной страницы, вы получите ошибку развертывания, о том, что нельзя удалить главную страницу. Чтобы избежать этой проблемы, выполните это:  
  
    -   Если существующая главная страница помечена как Главная страница по умолчанию, временно задан другой главной страницы Главная страница по умолчанию. После развертывания файлов в SharePoint, задайте новой главной страницы, главной страницей по умолчанию.  
  
    -   Если существующая главная страница помечена как пользовательской главной страницы, временно задан другой главной страницы пользовательской главной страницы. После развертывания файлов в SharePoint, задайте в качестве пользовательской главной страницы новой главной страницы.  
  
6.  В строке меню выберите **построения** > **развернуть решение**.  
  
7.  Откройте сайт SharePoint, чтобы просмотреть развернутые элементы.  
  
 Альтернативный способ импортировать файлы на [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] и развертывания их в SharePoint является добавление файлов в модули [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)] [Практическое: Импорт главной страницы или темы](../sharepoint/how-to-import-a-master-page-or-theme.md) и [использование модулей для включения файлов в решение](../sharepoint/using-modules-to-include-files-in-the-solution.md).  
  
## <a name="see-also"></a>См. также
 [Импорт элементов из существующего сайта SharePoint](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)   
 [Разработка решений SharePoint](../sharepoint/developing-sharepoint-solutions.md)   
 [Создание многократно используемых элементов управления для веб-частей или страниц приложений](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)  
  
