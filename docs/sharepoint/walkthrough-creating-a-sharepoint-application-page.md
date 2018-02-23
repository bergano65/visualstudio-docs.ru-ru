---
title: "Пошаговое руководство: Создание страницы приложения SharePoint | Документы Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- application pages [SharePoint development in Visual Studio], developing
- application pages [SharePoint development in Visual Studio], creating
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: 33c718707ce284179b69e33677d5b29f0d4433c7
ms.sourcegitcommit: 36ab8429333b31f03992a9fe8fc669db8e09c968
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2018
---
# <a name="walkthrough-creating-a-sharepoint-application-page"></a>Пошаговое руководство. Создание страницы приложения SharePoint
 
Страница приложения — это разновидность страницы ASP.NET. Страницы приложения содержат содержимое, объединенное с главной страницей SharePoint. Дополнительные сведения см. в разделе [Создание страниц приложений для SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).

В этом пошаговом руководстве показано, как создать страницу приложения, а затем выполните отладку с помощью локального сайта SharePoint. На этой странице отображаются все элементы, каждый пользователь создал или изменил во всех узлах фермы серверов.

В данном пошаговом руководстве рассмотрены следующие задачи:

- Создание проекта SharePoint.
- Добавление страницы приложения в проект SharePoint.
- Добавление элементов управления ASP.NET на страницу приложения.
- Добавление кода программной части элементов управления ASP.NET.
- Тестирование страницы приложения.

> [!NOTE]
> Отображаемые на компьютере имена или расположения некоторых элементов пользовательского интерфейса Visual Studio могут отличаться от указанных в следующих инструкциях. Это зависит от имеющегося выпуска Visual Studio и используемых параметров. Дополнительные сведения см. в разделе [Персонализация интегрированной среды разработки Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Предварительные требования

- Поддерживаемые выпуски Windows и SharePoint. Дополнительные сведения см. в разделе [требования к разработке решений SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).

## <a name="creating-a-sharepoint-project"></a>Создание проекта SharePoint

Сначала создайте **пустой проект SharePoint**. После этого будет добавлен **страницы приложения** этот проект.

1. Запустите [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. Откройте **новый проект** диалогового окна разверните **Office/SharePoint** узле язык, который вы хотите использовать, а затем выберите **решений SharePoint** узла.

3. В **установленные шаблоны Visual Studio** области, выберите **SharePoint 2010 - пустой проект** шаблона. Назовите проект **MySharePointProject**, а затем выберите **ОК** кнопки.

     **Мастер настройки SharePoint** отображается. Этот мастер позволяет выбрать сайт, который будет использоваться для отладки проекта и уровень доверия решения.

4. Выберите **развернуть как решение фермы** переключатель, а затем выберите **Готово** кнопку, чтобы принять локальный сайт SharePoint по умолчанию.

## <a name="creating-an-application-page"></a>Создание страницы приложения

Чтобы создать страницу приложения, добавьте **страницы приложения** в проект.

1. В **обозревателе решений**, выберите **MySharePointProject** проекта.

2. В строке меню выберите **проекта**, **Добавление нового элемента**.

3. В **Добавление нового элемента** диалогового окна выберите **страница приложения (только для решения фермы** шаблона.

4. Назовите страницу **SearchItems**, а затем выберите **добавить** кнопки.

     Конструктор Visual Web Developer отображает страницу приложения в **источника** представление, где можно просмотреть элементы HTML страницы. Конструктор отображает разметку для нескольких <xref:System.Web.UI.WebControls.Content> элементов управления. Каждый элемент управления сопоставляется <xref:System.Web.UI.WebControls.ContentPlaceHolder> элемента управления, который определен в главную страницу приложения по умолчанию.

## <a name="designing-the-layout-of-the-application-page"></a>Разработка макета страницы приложения

Элемент страницы приложения позволяет использовать конструктор для добавления элементов управления ASP.NET на страницу приложения. Этот конструктор является тот же конструктор, используемый в Visual Web Developer. Добавить метку, список переключателей и таблицу, чтобы **источника** представлении конструктора, а затем задайте свойства так же, как при разработке любой стандартной страницы ASP.NET.

1. В строке меню выберите **Вид**, **Панель элементов**.

2. В узле «стандартный» **элементов**, выполните одно из следующих действий:

    - Откройте контекстное меню для **метка** товара, выберите **копирования**, откройте контекстное меню для строки в группе **PlaceHolderMain** содержимого элемента управления в конструкторе, а затем Выберите **вставить**.

    - Перетащите **метка** элемента из **элементов** в тело элемента **PlaceHolderMain** элемент управления содержимым.

3. Повторите предыдущий шаг для добавления **DropDownList** элемента и **таблицы** элемент **PlaceHolderMain** элемент управления содержимым.

4. В конструкторе, измените значение `Text` атрибут для элемента управления метка **Показать все элементы**.

5. В конструкторе, замените `<asp:DropDownList>` элемент следующий XML-код.

    ```xml
    <asp:DropDownList ID="DropDownList1" runat="server" AutoPostBack="true"
     OnSelectedIndexChanged="DropDownList1_SelectedIndexChanged">
        <asp:ListItem Text="Created by me" Value="Author"></asp:ListItem>
        <asp:ListItem Text="Modified by me" Value="Editor"></asp:ListItem>
    </asp:DropDownList>
    ```

## <a name="handling-the-events-of-controls-on-the-page"></a>Обработка событий элементов управления на странице

Обработка элементов управления на страницу приложения так же, как и любой страницы ASP.NET. В этой процедуре будет обрабатывать `SelectedIndexChanged` события из раскрывающегося списка.

1. На **представление** меню, выберите **кода**.

     В редакторе кода открывается файл кода страницы приложения.

2. Добавьте следующий метод в класс `SearchItems`. Этот код обрабатывает <xref:System.Web.UI.WebControls.ListControl.SelectedIndexChanged> событие <xref:System.Web.UI.WebControls.DropDownList> путем вызова метода, который будет создан позднее в этом руководстве.

     [!code-vb[SP_ApplicationPage#5](../sharepoint/codesnippet/VisualBasic/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.vb#5)]
     [!code-csharp[SP_ApplicationPage#5](../sharepoint/codesnippet/CSharp/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.cs#5)]

3. Добавьте следующие инструкции в начало файла кода страницы приложения.

     [!code-vb[SP_ApplicationPage#1](../sharepoint/codesnippet/VisualBasic/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.vb#1)]
     [!code-csharp[SP_ApplicationPage#1](../sharepoint/codesnippet/CSharp/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.cs#1)]

4. Добавьте следующий метод в класс `SearchItems`. Этот метод перебор всех узлов в ферме серверов и осуществляет поиск элементов, созданных или измененных текущим пользователем.

     [!code-vb[SP_ApplicationPage#2](../sharepoint/codesnippet/VisualBasic/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.vb#2)]
     [!code-csharp[SP_ApplicationPage#2](../sharepoint/codesnippet/CSharp/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.cs#2)]

5. Добавьте следующий метод в класс `SearchItems`. Этот метод отображаются элементы, созданные или измененные текущего пользователя в таблице.

     [!code-vb[SP_ApplicationPage#3](../sharepoint/codesnippet/VisualBasic/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.vb#3)]
     [!code-csharp[SP_ApplicationPage#3](../sharepoint/codesnippet/CSharp/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.cs#3)]

## <a name="testing-the-application-page"></a>Тестирование страницы приложения

При запуске проекта открывается сайт SharePoint, и откроется страница приложения.

1. В **обозревателе решений**, откройте контекстное меню для страницы приложения и нажмите кнопку **назначить автозапускаемым элементом**.

2. Нажмите клавишу F5.

     Откроется сайт SharePoint.

3. На странице «приложения» выберите **изменено мной** параметр.

     Страницы приложения обновляется и отображает все элементы, которые изменены на всех сайтах фермы серверов.

4. На странице «приложения» выберите **созданные мной** в списке.

     Страницы приложения обновляется и отображает все элементы, которые созданы на всех сайтах фермы серверов.

## <a name="next-ateps"></a>Далее ateps

Дополнительные сведения о страницах приложений SharePoint см. в разделе [Создание страниц приложений для SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).

Дополнительные сведения о том, как создать содержимое страницы SharePoint с помощью Visual Web Designer в следующих разделах:

- [Создание веб-частей для SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md).

- [Создание многократно используемых элементов управления для веб-частей или страниц приложений](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md).

## <a name="see-also"></a>См. также

[Практическое руководство. Создание страницы приложения](../sharepoint/how-to-create-an-application-page.md)  
[Тип страницы приложения _layouts](http://go.microsoft.com/fwlink/?LinkID=169274)
