---
title: 'Пошаговое руководство: Создание страницы приложения SharePoint | Документация Майкрософт'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
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
manager: douge
ms.workload:
- office
ms.openlocfilehash: e31b06d642947d88d1076b3ad365e62b663c8d4a
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/29/2018
ms.locfileid: "37119417"
---
# <a name="walkthrough-create-a-sharepoint-application-page"></a>Пошаговое руководство: Создание страницы приложения SharePoint
 
Страница приложения — это разновидность страницы ASP.NET. Страницы приложения содержат содержимое, объединенное с эталонной страницей SharePoint. Дополнительные сведения см. в разделе [Создание страниц приложений для SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).

В этом пошаговом руководстве показано, как создать страницу приложения и выполнить его отладку с помощью локального сайта SharePoint. На этой странице отображаются все элементы, которые каждый пользователь создал или изменил на всех сайтах фермы серверов.

В данном пошаговом руководстве рассмотрены следующие задачи:

- Создание проекта SharePoint.
- Добавление страницы приложения в проект SharePoint.
- Добавление элементов управления ASP.NET на страницу приложения.
- Добавление кода элементы управления ASP.NET.
- Тестирование страницы приложения.

> [!NOTE]
> Отображаемые на компьютере имена или расположения некоторых элементов пользовательского интерфейса Visual Studio могут отличаться от указанных в следующих инструкциях. Это зависит от имеющегося выпуска Visual Studio и используемых параметров. Дополнительные сведения см. в разделе [Персонализация интегрированной среды разработки Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Предварительные требования

- Поддерживаемые версии Windows и SharePoint. Дополнительные сведения см. в разделе [требования по разработке решений SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).

## <a name="create-a-sharepoint-project"></a>Создание проекта SharePoint

Во-первых, создайте **Empty SharePoint Project**. После этого будет добавлен **страницы приложения** в этот проект.

1. Запустите [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. Откройте **новый проект** диалогового окна последовательно раскройте элементы **Office/SharePoint** язык, который вы хотите использовать, а затем выберите в узле **решений SharePoint** узел.

3. В **установленные шаблоны Visual Studio** панели выберите **SharePoint 2010 — пустой проект** шаблона. Назовите проект **MySharePointProject**, а затем выберите **ОК** кнопки.

     **Мастер настройки SharePoint** отображается. Этот мастер позволяет выбрать сайт, который будет использоваться для отладки проекта и уровень доверия решения.

4. Выберите **развернуть как решение фермы** переключатель, а затем выберите **Готово** кнопку, чтобы принять локальный сайт SharePoint по умолчанию.

## <a name="create-an-application-page"></a>Создание страницы приложения

Чтобы создать страницу приложения, добавьте **страницы приложения** элемента в проект.

1. В **обозревателе решений**, выберите **MySharePointProject** проекта.

2. В строке меню выберите **Проект** > **Добавить новый элемент**.

3. В **Добавление нового элемента** диалоговое окно, выберите **страницы приложения (только для решения фермы** шаблона.

4. Присвойте странице имя **SearchItems**, а затем выберите **добавить** кнопки.

     Конструктор Visual Web Developer отображает страницу приложения в **источника** представление, где вы увидите элементы HTML страницы. Конструктор отображает разметку для нескольких <xref:System.Web.UI.WebControls.Content> элементов управления. Каждый элемент управления сопоставляется <xref:System.Web.UI.WebControls.ContentPlaceHolder> элемента управления, который определен в главную страницу приложения по умолчанию.

## <a name="design-the-layout-of-the-application-page"></a>Разработка структуры страницы приложения

Указанный элемент страницы приложения позволяет использовать конструктор для добавления элементов управления ASP.NET на страницу приложения. Этот конструктор является тот же конструктор, используемый в Visual Web Developer. Добавьте метку, список переключателей и таблицу, чтобы **источника** представление кода и затем задать свойства так же, как при разработке любой стандартной страницы ASP.NET.

1. В строке меню выберите **представление** > **элементов**.

2. В стандартном узле **элементов**, выполните одно из следующих действий:

    - Откройте контекстное меню для **метка** выберите **копирования**, откройте контекстное меню для строки под **PlaceHolderMain** содержимого элемента управления в конструкторе, а затем Выберите **вставить**.

    - Перетащите **метка** элемент из **элементов** в тело элемента **PlaceHolderMain** элемент управления содержимым.

3. Повторите предыдущий шаг, чтобы добавить **DropDownList** элемента и **таблицы** элемент **PlaceHolderMain** элемент управления содержимым.

4. В конструкторе измените значение свойства `Text` атрибут для элемента управления метка **Показать все элементы**.

5. В конструкторе замените `<asp:DropDownList>` элемент следующим кодом XML.

    ```xml
    <asp:DropDownList ID="DropDownList1" runat="server" AutoPostBack="true"
     OnSelectedIndexChanged="DropDownList1_SelectedIndexChanged">
        <asp:ListItem Text="Created by me" Value="Author"></asp:ListItem>
        <asp:ListItem Text="Modified by me" Value="Editor"></asp:ListItem>
    </asp:DropDownList>
    ```

## <a name="handle-the-events-of-controls-on-the-page"></a>Обработка событий элементов управления на странице

Обработка элементов управления на страницу приложения, так же, как и любой страницы ASP.NET. В этой процедуре будет обрабатывать `SelectedIndexChanged` события из раскрывающегося списка.

1. На **представление** меню, выберите **кода**.

     В редакторе кода открывается файл кода страницы приложения.

2. Добавьте следующий метод в класс `SearchItems`. Этот код обрабатывает <xref:System.Web.UI.WebControls.ListControl.SelectedIndexChanged> событие <xref:System.Web.UI.WebControls.DropDownList> путем вызова метода, который вы создадите далее в этом пошаговом руководстве.

     [!code-vb[SP_ApplicationPage#5](../sharepoint/codesnippet/VisualBasic/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.vb#5)]
     [!code-csharp[SP_ApplicationPage#5](../sharepoint/codesnippet/CSharp/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.cs#5)]

3. Добавьте следующие инструкции в начало файла кода страницы приложения.

     [!code-vb[SP_ApplicationPage#1](../sharepoint/codesnippet/VisualBasic/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.vb#1)]
     [!code-csharp[SP_ApplicationPage#1](../sharepoint/codesnippet/CSharp/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.cs#1)]

4. Добавьте следующий метод в класс `SearchItems`. Этот метод перебор всех сайтов на ферме серверов и осуществляет поиск элементов, созданных или измененных текущим пользователем.

     [!code-vb[SP_ApplicationPage#2](../sharepoint/codesnippet/VisualBasic/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.vb#2)]
     [!code-csharp[SP_ApplicationPage#2](../sharepoint/codesnippet/CSharp/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.cs#2)]

5. Добавьте следующий метод в класс `SearchItems`. Этот метод отображает элементы, созданных или измененных текущим пользователем в таблице.

     [!code-vb[SP_ApplicationPage#3](../sharepoint/codesnippet/VisualBasic/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.vb#3)]
     [!code-csharp[SP_ApplicationPage#3](../sharepoint/codesnippet/CSharp/sp_applicationpage/layouts/sp_applicationpage/SearchItems.aspx.cs#3)]

## <a name="test-the-application-page"></a>Тестирование страницы приложения

При запуске проекта открывается сайт SharePoint, и откроется страница приложения.

1. В **обозревателе решений**, откройте контекстное меню для страницы приложения и нажмите кнопку **назначить автозапускаемым элементом**.

2. Нажмите клавишу **F5**.

     Откроется сайт SharePoint.

3. На странице приложения выберите **изменено мной** параметр.

     Обновляет страницы приложения на ней отображаются все элементы, которые были изменены на всех сайтах фермы серверов.

4. На странице приложения выберите **созданные мной** в списке.

     Обновляет страницы приложения на ней отображаются все элементы, созданные на всех сайтах фермы серверов.

## <a name="next-steps"></a>Следующие шаги

Дополнительные сведения о страницах приложений SharePoint, см. в разделе [Создание страниц приложений для SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).

Дополнительные сведения о разработке содержимого страниц SharePoint с помощью Visual Web Designer в следующих разделах:

- [Создание веб-частей для SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md).

- [Создание многократно используемых элементов управления для веб-частей или страниц приложений](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md).

## <a name="see-also"></a>См. также

[Практическое: Создание страницы приложения](../sharepoint/how-to-create-an-application-page.md)  
[Тип страниц приложений _layouts](http://go.microsoft.com/fwlink/?LinkID=169274)
