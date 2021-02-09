---
title: Пошаговое руководство. Добавление страницы приложения в рабочий процесс | Документация Майкрософт
description: В этом пошаговом руководстве добавьте страницу приложения в решение рабочего процесса SharePoint. Измените код рабочего процесса. Создание, код и тестирование страницы приложения.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, adding applications page to workflow
- application page [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: d07b5272a31a0c649e12f353aefaa7c63c335eb5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99882665"
---
# <a name="walkthrough-add-an-application-page-to-a-workflow"></a>Пошаговое руководство: Добавление страницы приложения в рабочий процесс
  В этом пошаговом руководстве показано, как добавить страницу приложения, которая отображает данные, полученные из рабочего процесса, в проект рабочего процесса. Он основан на проекте, описанном в разделе [Пошаговое руководство. Создание рабочего процесса с формами ассоциаций и инициации](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md).

 В этом пошаговом руководстве описаны следующие задачи.

- Добавление страницы приложения ASPX в проект рабочего процесса SharePoint.

- Получение данных из проекта рабочего процесса и управление им.

- Отображение данных в таблице на странице приложения.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Предварительные требования
 Для выполнения этого пошагового руководства требуются следующие компоненты:

- Поддерживаемые выпуски [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] и SharePoint.

- приведенному.

- Кроме того, необходимо выполнить проект, [описанный в разделе Пошаговое руководство. Создание рабочего процесса с формами ассоциаций и инициации](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md).

## <a name="amend-the-workflow-code"></a>Уточнение кода рабочего процесса
 Сначала добавьте строку кода в рабочий процесс, чтобы присвоить столбцу результата значение, равное сумме отчета о расходах. Это значение будет использоваться позже в вычислении сводки отчета о затратах.

#### <a name="to-set-the-value-of-the-outcome-column-in-the-workflow"></a>Задание значения для столбца результатов в рабочем процессе

1. Загрузите завершенный проект из раздела [Пошаговое руководство. Создание рабочего процесса с формами ассоциаций и инициации](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md) в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

2. Откройте код для *Workflow1.CS* или *Workflow1. vb* (в зависимости от языка программирования).

3. В конце `createTask1_MethodInvoking` метода добавьте следующий код:

    ```vb
    createTask1_TaskProperties1.ExtendedProperties("Outcome") =
      workflowProperties.InitiationData
    ```

    ```csharp
    createTask1_TaskProperties1.ExtendedProperties["Outcome"] =
      workflowProperties.InitiationData;
    ```

## <a name="create-an-application-page"></a>Страница «Создание приложения»
 Затем добавьте в проект форму ASPX. В этой форме отображаются данные, полученные из проекта рабочего процесса отчета о затратах. Для этого будет добавлена страница приложения. Страница приложения использует ту же главную страницу, что и другие страницы SharePoint, то есть она будет похожа на другие страницы сайта SharePoint.

#### <a name="to-add-an-application-page-to-the-project"></a>Добавление страницы приложения в проект

1. Выберите проект експенсерепорт, а затем в строке меню выберите **проект**  >  **Добавить новый элемент**.

2. В области **шаблоны** выберите шаблон **страницы приложения** , используйте имя по умолчанию для элемента проекта (**ApplicationPage1. aspx**) и нажмите кнопку **Добавить** .

3. В файле [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] ApplicationPage1. aspx замените `PlaceHolderMain` раздел следующим:

    ```aspx-csharp
    <asp:Content ID="Main" ContentPlaceHolderID="PlaceHolderMain" runat="server">
        <asp:Label ID="Label1" runat="server" Font-Bold="True"
            Text="Expenses that exceeded allotted amount" Font-Size="Medium"></asp:Label>
        <br />
        <asp:Table ID="Table1" runat="server">
        </asp:Table>
    </asp:Content>
    ```

     Этот код добавляет таблицу на страницу вместе с заголовком.

4. Добавьте заголовок на страницу приложения, заменив `PlaceHolderPageTitleInTitleArea` раздел следующим образом:

    ```aspx-csharp
    <asp:Content ID="PageTitleInTitleArea" ContentPlaceHolderID="PlaceHolderPageTitleInTitleArea" runat="server" >
        Expense Report Summary
    </asp:Content>
    ```

## <a name="code-the-application-page"></a>Код страницы приложения
 Затем добавьте код на страницу приложения сводка по отчету о затратах. При открытии страницы код просматривает список задач в SharePoint на предмет расходов, превышающих выделенную предельную сумму расходов. В отчете перечислены все элементы вместе с суммой расходов.

#### <a name="to-code-the-application-page"></a>Код страницы приложения

1. Выберите узел **ApplicationPage1. aspx** , а затем в строке меню выберите **Просмотреть**  >  **код** , чтобы отобразить код, лежащий на странице приложения.

2. Замените операторы **using** или **Import** (в зависимости от используемого языка программирования) в верхней части класса следующим:

    ```vb
    Imports System
    Imports Microsoft.SharePoint
    Imports Microsoft.SharePoint.WebControls
    Imports System.Collections
    Imports System.Data
    Imports System.Web.UI
    Imports System.Web.UI.WebControls
    Imports System.Web.UI.WebControls.WebParts
    Imports System.Drawing
    Imports Microsoft.SharePoint.Navigation
    ```

    ```csharp
    using System;
    using Microsoft.SharePoint;
    using Microsoft.SharePoint.WebControls;
    using System.Collections;
    using System.Data;
    using System.Web.UI;
    using System.Web.UI.WebControls;
    using System.Web.UI.WebControls.WebParts;
    using System.Drawing;
    using Microsoft.SharePoint.Navigation;
    ```

3. Добавьте следующий код в метод `Page_Load`:

    ```vb
    Try
        ' Reference the Tasks list on the SharePoint site.
        ' Replace "TestServer" with a valid SharePoint server name.
        Dim site As SPSite = New SPSite("http://TestServer")
        Dim list As SPList = site.AllWebs(0).Lists("Tasks")
        ' string text = "";
        Dim sum As Integer = 0
        Table1.Rows.Clear()
        ' Add table headers.
        Dim hr As TableHeaderRow = New TableHeaderRow
        hr.BackColor = Color.LightBlue
        Dim hc1 As TableHeaderCell = New TableHeaderCell
        Dim hc2 As TableHeaderCell = New TableHeaderCell
        hc1.Text = "Expense Report Name"
        hc2.Text = "Amount Exceeded"
        hr.Cells.Add(hc1)
        hr.Cells.Add(hc2)
        ' Add the TableHeaderRow as the first item
        ' in the Rows collection of the table.
        Table1.Rows.AddAt(0, hr)
        ' Iterate through the tasks in the Task list and collect those
        ' that have values in the "Related Content" and "Outcome" fields
        ' - the fields written to when expense approval is required.
        For Each item As SPListItem In list.Items
            Dim s_relContent As String = ""
            Dim s_outcome As String = ""
            Try
                ' Task has the fields - treat as expense report.
                s_relContent = item.GetFormattedValue("Related Content")
                s_outcome = item.GetFormattedValue("Outcome")
            Catch erx As System.Exception
                ' Task does not have fields - skip it.
                Continue For
            End Try
            ' Convert amount to an int and keep a running total.
            If (Not String.IsNullOrEmpty(s_relContent) And Not
              String.IsNullOrEmpty(s_outcome)) Then
                sum = (sum + Convert.ToInt32(s_outcome))
                Dim relContent As TableCell = New TableCell
                relContent.Text = s_relContent
                Dim outcome As TableCell = New TableCell
                outcome.Text = ("$" + s_outcome)
                Dim dataRow2 As TableRow = New TableRow
                dataRow2.Cells.Add(relContent)
                dataRow2.Cells.Add(outcome)
                Table1.Rows.Add(dataRow2)
            End If
        Next
        ' Report the sum of the reports in the table footer.
        Dim tfr As TableFooterRow = New TableFooterRow
        tfr.BackColor = Color.LightGreen
        ' Create a TableCell object to contain the
        ' text for the footer.
        Dim ftc1 As TableCell = New TableCell
        Dim ftc2 As TableCell = New TableCell
        ftc1.Text = "TOTAL: "
        ftc2.Text = ("$" + Convert.ToString(sum))
        ' Add the TableCell object to the Cells
        ' collection of the TableFooterRow.
        tfr.Cells.Add(ftc1)
        tfr.Cells.Add(ftc2)
        ' Add the TableFooterRow to the Rows
        ' collection of the table.
        Table1.Rows.Add(tfr)
    Catch errx As Exception
        System.Diagnostics.Debug.WriteLine(("Error: " + errx.ToString))
    End Try
    ```

    ```csharp
    try
    {
        // Reference the Tasks list on the SharePoint site.
        // Replace "TestServer" with a valid SharePoint server name.
        SPSite site = new SPSite("http://TestServer");
        SPList list = site.AllWebs[0].Lists["Tasks"];

        // string text = "";
        int sum = 0;

        Table1.Rows.Clear();

        // Add table headers.
        TableHeaderRow hr = new TableHeaderRow();
        hr.BackColor = Color.LightBlue;
        TableHeaderCell hc1 = new TableHeaderCell();
        TableHeaderCell hc2 = new TableHeaderCell();
        hc1.Text = "Expense Report Name";
        hc2.Text = "Amount Exceeded";
        hr.Cells.Add(hc1);
        hr.Cells.Add(hc2);
        // Add the TableHeaderRow as the first item
        // in the Rows collection of the table.
        Table1.Rows.AddAt(0, hr);

        // Iterate through the tasks in the Task list and collect those
        // that have values in the "Related Content" and "Outcome"
        // fields - the fields written to when expense approval is
        // required.
        foreach (SPListItem item in list.Items)
        {
            string s_relContent = "";
            string s_outcome = "";

            try
            {
                // Task has the fields - treat as expense report.
                s_relContent = item.GetFormattedValue("Related
                  Content");
                s_outcome = item.GetFormattedValue("Outcome");
            }
            catch
            {
                // Task does not have fields - skip it.
                continue;
            }

            if (!String.IsNullOrEmpty(s_relContent) &&
              !String.IsNullOrEmpty(s_outcome))
            {
                // Convert amount to an int and keep a running total.
                sum += Convert.ToInt32(s_outcome);
                TableCell relContent = new TableCell();
                relContent.Text = s_relContent;
                TableCell outcome = new TableCell();
                outcome.Text = "$" + s_outcome;
                TableRow dataRow2 = new TableRow();
                dataRow2.Cells.Add(relContent);
                dataRow2.Cells.Add(outcome);
                Table1.Rows.Add(dataRow2);
            }
        }

        // Report the sum of the reports in the table footer.
           TableFooterRow tfr = new TableFooterRow();
        tfr.BackColor = Color.LightGreen;

        // Create a TableCell object to contain the
        // text for the footer.
        TableCell ftc1 = new TableCell();
        TableCell ftc2 = new TableCell();
        ftc1.Text = "TOTAL: ";
        ftc2.Text = "$" + Convert.ToString(sum);

        // Add the TableCell object to the Cells
        // collection of the TableFooterRow.
        tfr.Cells.Add(ftc1);
        tfr.Cells.Add(ftc2);

        // Add the TableFooterRow to the Rows
        // collection of the table.
        Table1.Rows.Add(tfr);
    }

    catch (Exception errx)
    {
        System.Diagnostics.Debug.WriteLine("Error: " + errx.ToString());
    }
    ```

    > [!WARNING]
    > Обязательно замените "TestServer" в коде на допустимое имя сервера с SharePoint.

## <a name="test-the-application-page"></a>Тестирование страницы приложения
 Затем определите, правильно ли отображаются данные о расходах на странице приложения.

#### <a name="to-test-the-application-page"></a>Тестирование страницы приложения

1. Нажмите клавишу **F5** , чтобы запустить и развернуть проект в SharePoint.

2. Нажмите кнопку **Главная** , а затем на панели быстрого запуска выберите ссылку **Общие документы** , чтобы отобразить список Общие документы на сайте SharePoint.

3. Чтобы представить отчеты о расходах для этого примера, отправьте некоторые новые документы в список документы, щелкнув ссылку **документы** на вкладке **либраритулс** в верхней части страницы, а затем нажав кнопку **Отправить документ** на ленте инструментов.

4. После отправки некоторых документов создайте экземпляр рабочего процесса, щелкнув ссылку на **библиотеку** на вкладке **либраритулс** в верхней части страницы, а затем нажав кнопку **Параметры библиотеки** на ленте инструментов.

5. На странице **Параметры библиотеки документов** выберите ссылку **Параметры рабочего процесса** в разделе **разрешения и управление** .

6. На странице **Параметры рабочего процесса** выберите ссылку **Добавить рабочий процесс** .

7. На странице **Добавление рабочего процесса** выберите рабочий процесс **експенсерепорт-Workflow1** , введите имя рабочего процесса, например **експенсетест**, а затем нажмите кнопку **Далее** .

    Откроется форма ассоциации рабочего процесса. Используйте его для сообщения о предельной сумме расходов.

8. В форме Ассоциация введите **1000** в поле **лимит автоматического утверждения** , а затем нажмите кнопку **связать рабочий процесс** .

9. Нажмите кнопку **Главная** , чтобы вернуться на домашнюю страницу SharePoint.

10. На панели быстрого запуска щелкните ссылку **Общие документы** .

11. Выберите один из отправленных документов, чтобы отобразить стрелку раскрывающегося списка, выберите ее, а затем выберите элемент **рабочие процессы** .

12. Выберите изображение рядом с рабочим процессом ExpenseTest, чтобы открыть форму запуска рабочего процесса.

13. В текстовом поле **сумма расходов** введите значение больше 1000, а затем нажмите кнопку **запустить рабочий процесс** .

     Если отчет о расходах превышает выделенный объем, в список задач добавляется задача. Столбец с именем **експенсетест** и значением **Completed** также добавляется к элементу отчета о расходах в списке Общие документы.

14. Повторите шаги 11-13 с другими документами в списке "Общие документы". (Точное число документов не имеет значения.)

15. Отобразите страницу приложения сводки отчета о расходах, открыв следующий URL-адрес в браузере: **http://**<em>SystemName</em>**/_layouts/ExpenseReport/ApplicationPage1.aspx**.

     На странице Сводка по отчетам о расходах перечислены все отчеты о расходах, превышающие выделенный объем, объем, на который они превышаются, и общая сумма всех отчетов.

## <a name="next-steps"></a>Дальнейшие действия
 Дополнительные сведения о страницах приложений SharePoint см. в разделе [Создание страниц приложений для SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).

 Дополнительные сведения о проектировании содержимого страниц SharePoint с помощью Visual Web Designer в Visual Studio см. в следующих статьях:

- [Создание веб-частей для SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md).

- [Создание многократно используемых элементов управления для веб-частей или страниц приложений](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md).

## <a name="see-also"></a>См. также раздел

- [Пошаговое руководство: Создание рабочего процесса с формами связывания и запуска](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)
- [Практическое руководство. Создание страницы приложения](../sharepoint/how-to-create-an-application-page.md)
- [Создание страниц приложений для SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)
- [Разработка решений SharePoint](../sharepoint/developing-sharepoint-solutions.md)