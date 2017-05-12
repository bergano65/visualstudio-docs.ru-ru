---
title: "Пошаговое руководство. Создание страницы приложения SharePoint"
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
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "страницы приложений [разработка приложений SharePoint в Visual Studio], разработка"
  - "страницы приложений [разработка приложений SharePoint в Visual Studio], создание"
ms.assetid: 5b6dd941-5c59-4a89-89d0-8e973a00ae9e
caps.latest.revision: 42
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 41
---
# Пошаговое руководство. Создание страницы приложения SharePoint
  Страница приложения — это разновидность страницы ASP.NET.  На страницах приложения находится содержимое, объединенное с эталонной страницей SharePoint.  Для получения дополнительной информации см. [Создание страниц приложений для SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).  
  
 В этом пошаговом руководстве показано, как создать страницу приложения и выполнить отладку этой страницы с помощью локального сайта SharePoint.  На этой странице показаны все элементы, созданные или измененные пользователем на всех сайтах фермы серверов.  
  
 В данном пошаговом руководстве рассмотрены следующие задачи:  
  
-   Создание проекта SharePoint.  
  
-   Добавление страницы приложения в проект SharePoint.  
  
-   Добавление элементов управления ASP.NET на страницу приложения.  
  
-   Добавление кода, лежащего в основе элементов управления ASP.NET.  
  
-   Тестирование страницы приложения.  
  
> [!NOTE]  
>  Отображаемые на компьютере имена или расположения некоторых элементов пользовательского интерфейса Visual Studio могут отличаться от указанных в следующих инструкциях.  Эти элементы определяются используемой версией Visual Studio и ее параметрами.  Дополнительные сведения см. в разделе [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ru-ru/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Обязательные компоненты  
 Ниже приведены компоненты, необходимые для выполнения данного пошагового руководства.  
  
-   Поддерживаемые версии Windows и SharePoint.  Для получения дополнительной информации см. [Требования по разработке решений SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   [!INCLUDE[vsPro](../sharepoint/includes/vspro-md.md)] или выпуск Visual Studio Ultimate или Visual Studio Premium.  
  
## Создание проекта SharePoint  
 Создайте **пустой проект SharePoint**.  Впоследствии в этот проект нужно будет добавить элемент **страница приложения**.  
  
#### Создание проекта SharePoint  
  
1.  Запустите [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Откройте диалоговое окно **Новый проект**, разверните узел **Office\/SharePoint**, относящийся к необходимому языку, и выберите узел **Решения SharePoint**.  
  
3.  В области **Установленные шаблоны Visual Studio** выберите шаблон **SharePoint 2010 – Пустой проект**.  Назовите проект MySharePointProject и нажмите кнопку **ОК**.  
  
     Появится окно **Мастер настройки SharePoint**.  Этот мастер позволяет выбрать сайт для отладки проекта и уровень доверия решения.  
  
4.  Выберите переключатель **Развернуть как решение фермы** и нажмите кнопку **Готово**, чтобы принять локальный сайт SharePoint по умолчанию.  
  
## Создание страницы приложения  
 Чтобы создать страницу приложения, добавьте в проект элемент **Страница приложения**.  
  
#### Создание страницы приложения  
  
1.  В **Обозревателе решений** выберите проект **MySharePointProject**.  
  
2.  В строке меню выберите **Проект**, **Добавить новый элемент**.  
  
3.  В диалоговом окне **Добавить новый элемент** выберите шаблон **Страница приложения \(только для решений фермы\)**.  
  
4.  Назовите страницу SearchItems и нажмите кнопку **Добавить**.  
  
     Конструктор Visual Web Developer отображает страницу приложения в представлении **Источник**, где можно видеть HTML\-элементы страницы.  Конструктор отображает разметку для нескольких элементов управления <xref:System.Web.UI.WebControls.Content>.  Каждый элемент управления сопоставляется с элементом управления <xref:System.Web.UI.WebControls.ContentPlaceHolder>, определенным на главной странице приложения по умолчанию.  
  
## Разработка структуры страницы приложения  
 Указанный элемент страницы приложения позволяет использовать конструктор для добавления элементов управления ASP.NET на страницу приложения.  Такой же конструктор используется в Visual Web Developer.  Добавьте метку, список переключателей и таблицу в представление кода **Источник**, а затем задайте свойства точно так же, как при разработке любой стандартной страницы ASP.NET.  
  
 Дополнительные сведения об использовании этого конструктора в Visual Web Developer см. в разделе [Карта содержимого среды веб\-разработки Visual Studio](http://msdn.microsoft.com/ru-ru/9c31f93b-c8fb-4599-9b14-6194ec8c7539).  
  
#### Разработка структуры страницы приложения  
  
1.  В меню **Вид** выберите **Область элементов**.  
  
2.  В стандартном узле **Панель элементов** выполните одно из следующих действий:  
  
    -   Откройте контекстное меню для элемента **Метка** выберите **Копировать**, откройте контекстное меню для строки под элементом управления содержимым **PlaceHolderMain** в конструкторе и выберите **Вставить**.  
  
    -   Перетащите элемент **Метка** из **Панели элементов** в тело содержимого элемента управления **PlaceHolderMain**.  
  
3.  Повторяющийся предыдущий шаг, чтобы добавить элемент **DropDownList** и элемент **ТаблицаPlaceHolderMain** в элемент управления содержимым.  
  
4.  В конструкторе измените значение атрибута `Text` элемента управления метками на "Показать все элементы".  
  
5.  В конструкторе замените элемент `<asp:DropDownList>` на следующий XML\-код.  
  
    ```  
    <asp:DropDownList ID="DropDownList1" runat="server" AutoPostBack="true"  
     OnSelectedIndexChanged="DropDownList1_SelectedIndexChanged">  
        <asp:ListItem Text="Created by me" Value="Author"></asp:ListItem>  
        <asp:ListItem Text="Modified by me" Value="Editor"></asp:ListItem>  
    </asp:DropDownList>  
    ```  
  
## Обработка событий элементов управления на странице  
 Обработка элементов управления на странице приложения осуществляется так же, как на любой странице ASP.NET.  В этой процедуре показана обработка события `SelectedIndexChanged` из раскрывающегося списка.  
  
#### Обработка событий элементов управления на странице  
  
1.  В меню **Вид** выберите **Код**.  
  
     В редакторе кода открывается файл кода страницы приложения.  
  
2.  Добавьте следующий метод в класс `SearchItems`.  Этот код позволяет обработать событие <xref:System.Web.UI.WebControls.ListControl.SelectedIndexChanged> из списка <xref:System.Web.UI.WebControls.DropDownList> вызовом метода, создание которого описано далее в этом пошаговом руководстве.  
  
     [!code-csharp[SP_ApplicationPage#5](../snippets/csharp/VS_Snippets_OfficeSP/sp_applicationpage/cs/layouts/sp_applicationpage/SearchItems.aspx.cs#5)]
     [!code-vb[SP_ApplicationPage#5](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_applicationpage/vb/layouts/sp_applicationpage/SearchItems.aspx.vb#5)]  
  
3.  Добавьте следующие операторы в верхнюю часть файла кода страницы приложения.  
  
     [!code-csharp[SP_ApplicationPage#1](../snippets/csharp/VS_Snippets_OfficeSP/sp_applicationpage/cs/layouts/sp_applicationpage/SearchItems.aspx.cs#1)]
     [!code-vb[SP_ApplicationPage#1](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_applicationpage/vb/layouts/sp_applicationpage/SearchItems.aspx.vb#1)]  
  
4.  Добавьте следующий метод в класс `SearchItems`.  Этот метод выполняет перебор всех сайтов на ферме серверов и осуществляет поиск элементов, созданных или измененных текущим пользователем.  
  
     [!code-csharp[SP_ApplicationPage#2](../snippets/csharp/VS_Snippets_OfficeSP/sp_applicationpage/cs/layouts/sp_applicationpage/SearchItems.aspx.cs#2)]
     [!code-vb[SP_ApplicationPage#2](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_applicationpage/vb/layouts/sp_applicationpage/SearchItems.aspx.vb#2)]  
  
5.  Добавьте следующий метод в класс `SearchItems`.  Этот метод отображает элементы, созданные или измененные текущим пользователем в таблице.  
  
     [!code-csharp[SP_ApplicationPage#3](../snippets/csharp/VS_Snippets_OfficeSP/sp_applicationpage/cs/layouts/sp_applicationpage/SearchItems.aspx.cs#3)]
     [!code-vb[SP_ApplicationPage#3](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_applicationpage/vb/layouts/sp_applicationpage/SearchItems.aspx.vb#3)]  
  
## Тестирование страницы приложения  
 При выполнении проекта открывается сайт SharePoint и отображается страница приложения.  
  
#### Тестирование страницы приложения  
  
1.  В **Обозревателе решений** откройте контекстное меню для страницы приложения и выберите **Назначить автозапускаемым проектом**.  
  
2.  Нажмите клавишу F5.  
  
     Откроется сайт SharePoint.  
  
3.  На странице приложения выберите **Измененные мной**.  
  
     После обновления страницы приложения на ней отображаются все элементы, которые были изменены на всех сайтах фермы серверов.  
  
4.  На странице приложения выберите **Созданные мной** в списке.  
  
     После обновления страницы приложения на ней отображаются все элементы, которые были созданы на всех сайтах фермы серверов.  
  
## Следующие действия  
 Дополнительные сведения о страницах приложений SharePoint см. в разделе [Создание страниц приложений для SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).  
  
 Дополнительные сведения о разработке содержимого страниц SharePoint с помощью Visual Web Designer см. в следующих разделах.  
  
-   [Создание веб-частей для SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md).  
  
-   [Создание многократно используемых пользовательских элементов управления для веб-частей или страниц приложений](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md).  
  
## См. также  
 [Практическое руководство. Создание страницы приложения](../sharepoint/how-to-create-an-application-page.md)   
 [Тип страниц приложений \_layouts](http://go.microsoft.com/fwlink/?LinkID=169274)  
  
  