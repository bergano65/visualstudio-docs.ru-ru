---
title: 'Пошаговое руководство: Добавление страницы приложения в рабочий процесс | Документы Microsoft'
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
- SharePoint development in Visual Studio, adding applications page to workflow
- application page [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 97c720ded65e46e85f8d9f20f9f509b31f2cebbb
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-add-an-application-page-to-a-workflow"></a>Пошаговое руководство. Добавление страницы приложения в рабочий процесс
  В этом пошаговом руководстве демонстрируется добавление страницы приложения, отображаются данные, извлекаемые из рабочего процесса в проект рабочего процесса. Она построена на проект, описанный в разделе [Пошаговое руководство: Создание рабочего процесса с формами связывания и запуска](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md).  
  
 В этом пошаговом руководстве описаны следующие задачи.  
  
-   Добавление ASPX-страницы приложения в проект рабочего процесса SharePoint.  
  
-   Получение данных из проекта рабочего процесса и работе с ней.  
  
-   Отображение данных в таблице на странице приложения.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Предварительные требования  
 Ниже приведены компоненты, необходимые для выполнения данного пошагового руководства.  
  
-   Поддерживаемые выпуски [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] и SharePoint. Дополнительные сведения см. в разделе [требования к разработке решений SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Visual Studio.  
  
-   Необходимо также выполнить для завершения проекта в разделе [Пошаговое руководство: Создание рабочего процесса с формами связывания и запуска](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md).  
  
## <a name="amending-the-workflow-code"></a>Изменение кода рабочего процесса  
 Сначала добавьте строку кода в рабочий процесс, присваивается значение столбца результатом объем отчет по расходам. Это значение используется далее в расчет суммарных отчет о расходах.  
  
#### <a name="to-set-the-value-of-the-outcome-column-in-the-workflow"></a>Требуется задать значение в столбце Outcome в рабочем процессе  
  
1.  Загрузите проект из раздела [Пошаговое руководство: Создание рабочего процесса с формами связывания и запуска](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md) в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Откройте код Workflow1.cs или Workflow1.vb (в зависимости от используемого языка программирования).  
  
3.  В нижней части `createTask1_MethodInvoking` метод, добавьте следующий код:  
  
    ```vb  
    createTask1_TaskProperties1.ExtendedProperties("Outcome") =   
      workflowProperties.InitiationData  
    ```  
  
    ```csharp  
    createTask1_TaskProperties1.ExtendedProperties["Outcome"] =   
      workflowProperties.InitiationData;  
    ```  
  
## <a name="creating-an-application-page"></a>Создание страницы приложения  
 Затем добавьте в проект форму ASPX. В ней будут отображаться данные, полученные из проекта рабочего процесса отчета о расходах. Чтобы сделать это, вы добавите страницу приложения. Страницы приложения использует одну главную страницу, как другие страницы SharePoint, это означает, что оно будет похоже на другие страницы на сайте SharePoint.  
  
#### <a name="to-add-an-application-page-to-the-project"></a>Добавление страницы приложения в проект  
  
1.  Выберите проект ExpenseReport, а затем в строке меню выберите **проекта**, **Добавление нового элемента**.  
  
2.  В **шаблоны** области, выберите **страницы приложения** шаблона, используйте имя по умолчанию для элемента проекта (**ApplicaitonPage1.aspx**) и выберите **Добавить** кнопки.  
  
3.  В [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] ApplicationPage1.aspx, замените `PlaceHolderMain` раздел со следующими:  
  
    ```  
    <asp:Content ID="Main" ContentPlaceHolderID="PlaceHolderMain" runat="server">  
        <asp:Label ID="Label1" runat="server" Font-Bold="True"   
            Text="Expenses that exceeded allotted amount" Font-Size="Medium"></asp:Label>  
        <br />  
        <asp:Table ID="Table1" runat="server">  
        </asp:Table>  
    </asp:Content>  
    ```  
  
     Этот код добавляет таблицу на страницу с заголовком.  
  
4.  Добавьте заголовок страницы приложения, заменив `PlaceHolderPageTitleInTitleArea` раздел со следующими:  
  
    ```  
    <asp:Content ID="PageTitleInTitleArea" ContentPlaceHolderID="PlaceHolderPageTitleInTitleArea" runat="server" >  
        Expense Report Summary  
    </asp:Content>  
    ```  
  
## <a name="coding-the-application-page"></a>Программирование страницы приложения  
 Добавьте в код приложения сводки страница отчета по расходам. При открытии страницы, код просматривает список задач в SharePoint для расходов, превысивших выделенный предельная сумма расходов. В отчете указывается сумма затрат по каждому пункту.  
  
#### <a name="to-code-the-application-page"></a>В код страницы приложения  
  
1.  Выберите **ApplicationPage1.aspx** узел, а затем в строке меню выберите **представление**, **кода** чтобы открыть код страницы приложения.  
  
2.  Замените **с помощью** или **импорта** инструкции (в зависимости от используемого языка программирования) в верхней части класса на следующее:  
  
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
  
3.  Добавьте следующий код в метод `Page_Load`:  
  
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
    >  Обязательно замените "TestServer" в коде на допустимое имя сервера с SharePoint.  
  
## <a name="testing-the-application-page"></a>Тестирование страницы приложения  
 Далее необходимо определите ли страницы приложения правильно отображает данные о затратах.  
  
#### <a name="to-test-the-application-page"></a>Тестирование страницы приложения  
  
1.  Нажмите клавишу F5 для запуска проекта и его развертывания в SharePoint.  
  
2.  Выберите **Главная** , а затем кнопку **Общие документы** ссылку на панели быстрого запуска, чтобы отобразить список Общие документы на сайте SharePoint.  
  
3.  Чтобы представить отчеты о расходах для этого примера, загрузить несколько новых документов в список документов, выбрав **документов** ссылку **LibraryTools** вкладки в верхней части страницы и затем выбрать  **Отправка документа** кнопка на ленте.  
  
4.  Загрузив несколько документов, создать экземпляр рабочего процесса, выбрав **библиотеки** ссылку **LibraryTools** вкладки в верхней части страницы и затем выбрав **параметры библиотеки**кнопка на ленте.  
  
5.  В **параметры библиотеки документов** выберите **параметры рабочего процесса** ссылку в **разрешения и управление** раздела.  
  
6.  В **параметры рабочего процесса** выберите **Добавление рабочего процесса** ссылку.  
  
7.  В **Добавление рабочего процесса** выберите **ExpenseReport — Workflow1** рабочего процесса, введите имя рабочего процесса, таких как **ExpenseTest**, а затем выберите **Далее** кнопки.  
  
     Откроется форма сопоставления рабочего процесса. Используйте для отчета лимит суммы затрат.  
  
8.  В форме ассоциации введите **1000** в **лимит автоматического утверждения** , а затем нажмите **сопоставить рабочий процесс** кнопки.  
  
9. Выберите **домашней** кнопку, чтобы вернуться на домашнюю страницу SharePoint.  
  
10. Выберите **Общие документы** ссылку на панели быстрого запуска.  
  
11. Выберите один из отправленных документов, чтобы отобразить стрелку раскрывающегося списка, выберите его, а затем выберите **рабочих процессов** элемента.  
  
12. Выберите изображение рядом с рабочим процессом ExpenseTest, чтобы открыть форму запуска рабочего процесса.  
  
13. В **Общая сумма затрат** текстовом поле введите значение, которое больше 1000 и выберите **запустить рабочий процесс** кнопки.  
  
     При в отчете превышает заданный сумму расходов выделенных, задача добавляется в список задач. Столбец с именем **ExpenseTest** со значением **завершено** также добавляется в элемент отчета о расходах в списке общих документов.  
  
14. Повторите шаги с 11 – 13 для других документов в списке общих документов. (Точное количество документов не имеет значения.)  
  
15. Отобразить страницу приложения сводки отчета по расходам, открыв в веб-браузере следующий URL-адрес: **http://***имя_системы***/_layouts/ExpenseReport/ApplicationPage1.aspx**.  
  
     Страница сводки отчета по расходам перечислены все отчеты о расходах, превышен лимит, объем превышения и общая сумма по всем отчетам.  
  
## <a name="next-steps"></a>Следующие шаги  
 Дополнительные сведения о страницах приложений SharePoint см. в разделе [Создание страниц приложений для SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).  
  
 Дополнительные сведения о том, как создать содержимое страницы SharePoint с помощью Visual Web Designer в Visual Studio в следующих разделах:  
  
-   [Создание веб-частей для SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md).  
  
-   [Создание многократно используемых элементов управления для веб-частей или страниц приложений](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md).  
  
## <a name="see-also"></a>См. также  
 [Пошаговое руководство: Создание рабочего процесса с формами связывания и запуска](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)   
 [Как: Создание страницы приложения](../sharepoint/how-to-create-an-application-page.md)   
 [Создание страниц приложений для SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)   
 [Разработка решений SharePoint](../sharepoint/developing-sharepoint-solutions.md)  
  
  