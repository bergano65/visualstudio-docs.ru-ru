---
title: "Пошаговое руководство. Импорт пользовательской главной страницы и страницы сайта с изображением | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "импорт элементов [разработка приложений SharePoint в Visual Studio]"
  - "разработка приложений SharePoint в Visual Studio, импорт элементов"
ms.assetid: d1703957-81e2-47e1-b4ca-6a8d550d8da2
caps.latest.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 20
---
# Пошаговое руководство. Импорт пользовательской главной страницы и страницы сайта с изображением
  В этом пошаговом руководстве показано, как импортировать пользовательскую главную страницу и страницу сайта с изображением в проект [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint.  
  
 В пошаговом руководстве показано, как выполнять следующие задачи:  
  
-   создание пользовательских главных страниц и страниц сайта с изображением в SharePoint Designer;  
  
-   экспорт пользовательской главной страницы, изображения и страницы сайта в файл решения SharePoint \(WSP\-файл\);  
  
-   импорт и развертывание WSP\-файла в проект [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint с помощью проекта "Импорт пакета решения SharePoint".  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Обязательные компоненты  
 Для выполнения данного пошагового руководства необходимы следующие компоненты.  
  
-   Поддерживаемые выпуски [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] и SharePoint.  [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)] [Требования по разработке решений SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Visual Studio.  
  
-   SharePoint Designer 2010.  
  
## Создание элементов в SharePoint Designer  
 Этот пример показывает, как создать три элемента для экспорта в SharePoint Designer: пользовательскую главную страницу, страницу сайта, который ссылается на пользовательскую главную страницу, и файл изображения, отображаемый на странице сайта.  Файл изображения добавляется в папку SharePoint "\/images\/".  
  
#### Создание пользовательской главной страницы в SharePoint Designer  
  
1.  В SharePoint Designer в области навигации выберите объект сайта **Главные страницы**.  
  
2.  На ленте **Главные страницы** выберите **Пустая главная страница**.  
  
3.  Выберите новую главную страницу, а затем на ленте **Главные страницы** выберите **Изменить файл**.  
  
4.  В нижней части SharePoint Designer выберите вкладку **Код**.  
  
5.  Замените существующую разметку на следующую.  
  
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
  
6.  Сохраните страницу, откройте вкладку **Главные страницы** и переименуйте главную страницу в качестве **mybasic1.master**.  
  
## Добавление изображения в базу данных контента в SharePoint Designer  
 Теперь можно добавить изображение для отображения на странице сайта.  Изображение разворачивается в базу данных контента SharePoint.  
  
#### Добавление изображения в базу данных контента в SharePoint Designer  
  
1.  В области навигации выберите объект сайта **Все файлы**, а затем, в представлении дерева, выберите папку **изображения**.  
  
2.  На ленте **Все файлы** выберите **Импортировать файлы**, выберите необходимый файл, а затем нажмите кнопку **ОК**.  В этом примере файл называется **myimg1.png**.  
  
     При необходимости можно создать вложенную папку для упорядочивания изображений.  
  
3.  Закройте диалоговое окно **Импорт**.  
  
## Создание страницы сайта  
 Эта основная страница использует пользовательскую главную страницу и отображает изображение, добавленное на предыдущем шаге.  
  
#### Создание страницы сайта  
  
1.  В области навигации выберите объект **Страницы сайта**.  
  
2.  На ленте **страницы** нажмите кнопку **Страница**, выберите тип страницы **ASPX** и назовите новый файл **mycontentpage1.aspx**.  
  
     При необходимости можно создать вложенную папку для упорядочивания страниц сайта.  
  
3.  В списке страниц сайта выберите **MyContentPage1.aspx** для открытия страницы свойств, а затем в нижней части страницы выберите ссылку **Изменить файл**.  
  
     Если появится сообщение, в котором говорится, что эта страница не содержит области, доступные для изменения в безопасном режиме и требуется ли открыть эту страницу в продвинутом режиме, нажмите кнопку **Да**.  
  
4.  В нижней части страницы нажмите кнопку **Код**.  
  
5.  Замените существующую разметку на следующую.  
  
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
  
6.  Сохраните обновленную страницу сайта.  
  
## Экспорт элементов из SharePoint  
 Экспортируйте элементы из SharePoint в файл решения SharePoint \(WSP\-файл\).  
  
#### Экспорт элементов из SharePoint Designer  
  
1.  В конструкторе SharePoint, в области навигации, выберите объект **Сайт команды**, а затем на ленте **Сайт** выберите **Сохранить как шаблон**.  
  
2.  В диалоговом окне **Сохранить как шаблон** введите имя файла и имя шаблона, установите флажок **Включить содержимое**, а затем нажмите кнопку **OK**.  
  
     Содержимое сайта будет сохранено в WSP\-файл.  
  
3.  После экспорта решения выберите ссылку **Коллекция решений** для отображения списка имеющихся файлов решения.  
  
4.  Откройте контекстное меню для нового .wsp\-файла, а затем выберите **Сохранить объект как**, чтобы сохранить его в системе.  
  
## Импорт элементов в Visual Studio  
 Импортируйте .wsp\-файл в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  После импорта можно настраивать содержимое, добавлять новые элементы, а затем выполнять развертывание.  
  
#### Импорт элементов из WSP\-файла в Visual Studio  
  
1.  Создайте в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] проект **Импорт пакета решения SharePoint 2010**.  
  
2.  На странице **Выберите элементы для импорта** в разделе **Модуль** в колонке **Тип** выберите флажок только для импортируемых файлов, указанных в следующей таблице.  
  
    |Имя файла|Описание|  
    |---------------|--------------|  
    |\_catalogsmasterpage\_|Пользовательская главная страница.|  
    |images\_|Файл изображения в файловой системе SharePoint.|  
    |SitePages\_|Страница сайта.|  
  
3.  Нажмите кнопку **Готово**, чтобы импортировать выбранные элементы.  
  
4.  В **Обозревателе решений** выберите узел \_catalogsmasterpage\_ и установите для свойства **Устранение конфликтов развертывания** значение **Автоматически**.  
  
     Это помогает убедиться, что любые конфликты развертывания будут устранены автоматически.  
  
5.  Если имя новой главной страницы совпадает с именем существующей страницы, убедитесь, что существующая страница не помечена в SharePoint Designer как главная страница по умолчанию или как пользовательская главная страница.  
  
     Если существующая главная страница помечена как главная страница по умолчанию или как пользовательская главная страница пользователя, возникнет ошибка развертывания, указывающая, что главная страница не может быть удалена.  Чтобы избежать этой проблемы, выполните следующие действия:  
  
    -   если существующая главная страница помечена как главная страница по умолчанию, временно сделайте другую главную страницу главной страницей по умолчанию.  После развертывания файлов в SharePoint установите новую главную страницу в качестве главной страницей по умолчанию;  
  
    -   если существующая главная страница помечена как пользовательская главная страница, временно сделайте другую главную страницу пользовательской главной страницей.  После развертывания файлов в SharePoint установите новую главную страницу в качестве пользовательской главной страницы.  
  
6.  В строке меню последовательно выберите **Сборка** и **Развернуть решение**.  
  
7.  Откройте сайт SharePoint для просмотра развернутых элементов.  
  
 Альтернативный способ импорта файлов в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] и развертывания их в SharePoint состоит в добавлении файлов в модули [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)] [Практическое руководство. Импорт главной страницы или темы](../sharepoint/how-to-import-a-master-page-or-theme.md) и [Использование модулей для включения файлов в решение](../sharepoint/using-modules-to-include-files-in-the-solution.md).  
  
## См. также  
 [Импорт элементов из существующего сайта SharePoint](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)   
 [Разработка решений SharePoint](../sharepoint/developing-sharepoint-solutions.md)   
 [Создание многократно используемых пользовательских элементов управления для веб-частей или страниц приложений](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)  
  
  