---
title: "Пошаговое руководство. Добавление страницы приложения в рабочий процесс | Microsoft Docs"
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
  - "страница приложения [разработка приложений SharePoint в Visual Studio]"
  - "разработка приложений SharePoint в Visual Studio, добавление страницы приложений в рабочий процесс"
ms.assetid: e4845d07-917b-45cb-a569-4ecdd602fbd9
caps.latest.revision: 28
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 27
---
# Пошаговое руководство. Добавление страницы приложения в рабочий процесс
  В этом пошаговом руководстве показано, как добавить страницу приложения, в которой отображаются данные, извлекаемые в рабочий процесс из проекта рабочего процесса.  В нем используется проект, описанный в разделе [Пошаговое руководство. Создание рабочего процесса с формами связывания и запуска](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md).  
  
 В этом пошаговом руководстве показано выполнение следующих задач.  
  
-   Добавление ASPX\-страницы приложения в проект рабочего процесса SharePoint.  
  
-   Получение и обработка данных из проекта рабочего процесса.  
  
-   Отображение данных в таблице на странице приложения.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Обязательные компоненты  
 Ниже приведены компоненты, необходимые для выполнения данного пошагового руководства.  
  
-   Поддерживаемые выпуски [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] и SharePoint.  Для получения дополнительной информации см. [Требования по разработке решений SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Visual Studio.  
  
-   Также необходимо создать проект, описанный в разделе [Пошаговое руководство. Создание рабочего процесса с формами связывания и запуска](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md).  
  
## Изменение кода рабочего процесса  
 Сначала добавьте в код рабочего процесса строку, задающую в столбце Outcome сумму, указанную в отчете о затратах.  Это значение будет использоваться в дальнейшем для вычисления итоговой суммы по отчету.  
  
#### Указание значения в столбце Outcome в рабочем процессе  
  
1.  Загрузите проект, созданный согласно инструкциям в разделе [Пошаговое руководство. Создание рабочего процесса с формами связывания и запуска](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md), в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Откройте файле с кодом Workflow1.cs или Workflow1.vb \(в зависимости от используемого языка программирования\).  
  
3.  В конце метода `createTask1_MethodInvoking` добавьте следующий код.  
  
    ```vb  
    createTask1_TaskProperties1.ExtendedProperties("Outcome") =   
      workflowProperties.InitiationData  
    ```  
  
    ```csharp  
    createTask1_TaskProperties1.ExtendedProperties["Outcome"] =   
      workflowProperties.InitiationData;  
    ```  
  
## Создание страницы приложения  
 Теперь добавьте в проект ASPX\-форму.  В ней будут отображаться данные, полученные из проекта рабочего процесса отчета о затратах.  Для этого необходимо добавить страницу приложения.  В странице приложения используется та же главная страница, что и в других страницах SharePoint, а значит она будет похожа на другие страницы сайта SharePoint.  
  
#### Добавление страницы приложения в проект  
  
1.  Выберите проект ExpenseReport, а затем в строке меню выберите **Проект**, **Добавить новый элемент**.  
  
2.  В области **Шаблоны** выберите шаблон **Страница приложения**, используйте имя элемента проекта по умолчанию \(**ApplicaitonPage1.aspx**\), и выберите кнопку **Добавить**.  
  
3.  В [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] файла ApplicationPage1.aspx замените раздел `PlaceHolderMain` следующим кодом.  
  
    ```  
    <asp:Content ID="Main" ContentPlaceHolderID="PlaceHolderMain" runat="server">  
        <asp:Label ID="Label1" runat="server" Font-Bold="True"   
            Text="Expenses that exceeded allotted amount" Font-Size="Medium"></asp:Label>  
        <br />  
        <asp:Table ID="Table1" runat="server">  
        </asp:Table>  
    </asp:Content>  
    ```  
  
     Этот код добавляет на страницу таблицу с заголовком.  
  
4.  Добавьте заголовок страницы приложения, заменив раздел `PlaceHolderPageTitleInTitleArea` следующим кодом.  
  
    ```  
    <asp:Content ID="PageTitleInTitleArea" ContentPlaceHolderID="PlaceHolderPageTitleInTitleArea" runat="server" >  
        Expense Report Summary  
    </asp:Content>  
    ```  
  
## Программирование страницы приложения  
 Теперь добавьте код на страницу приложения сводки по отчету о затратах.  Код реализует следующее поведение: когда пользователь открывает страницу, в списке задач SharePoint проверяется наличие сумм затрат, превышающих заданный лимит.  В отчете указывается сумма затрат по каждому пункту.  
  
#### Программирование страницы приложения  
  
1.  Выберите узел **ApplicationPage1.aspx**, а затем в меню выберите **Вид**, **Код**, чтобы открыть код страницы приложения.  
  
2.  Замените операторы **using** или **Import** \(в зависимости от используемого языка программирования\) в начале кода класса следующими строками:  
  
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
  
3.  Добавьте следующий код в метод `Page_Load`.  
  
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
    >  Обязательно замените «TestServer» в коде на допустимое имя сервера с SharePoint.  
  
## Тестирование страницы приложения  
 Теперь проверьте, правильно ли отображаются данные о затратах на странице приложения.  
  
#### Тестирование страницы приложения  
  
1.  Нажмите клавишу F5 для запуска проекта и его развертывания в SharePoint.  
  
2.  Нажмите кнопку **Домой**, затем воспользуйтесь ссылкой **Общие документы** на панели быстрого запуска, чтобы открыть список "Общие документы" на сайте SharePoint.  
  
3.  Чтобы представить отчеты о расходах для этого примера, необходимо загрузить несколько новых документов в список "Документы". Для этого нужно щелкнуть ссылку **Документы** на вкладке **Инструменты библиотеки** в верхней части страницы и нажать кнопку **Отправить документ** на ленте.  
  
4.  Загрузив несколько документов, создайте экземпляр рабочего процесса, щелкнув ссылку **Библиотека** на вкладке **LibraryTools** в верхней части страницы, а затем нажав кнопку **Параметры библиотеки** на ленте.  
  
5.  На странице **Параметры библиотеки документов** выберите ссылку **Параметры рабочих процессов** в разделе **Разрешения и управление**.  
  
6.  На странице **Параметры рабочих процессов** выберите ссылку **Добавить рабочий процесс**.  
  
7.  На странице **Добавление рабочего процесса** выберите рабочий процесс **ExpenseReport — Workflow1**, введите имя рабочего процесса \(например, ExpenseTest\) и нажмите кнопку **Далее**.  
  
     Откроется форма связывания рабочего процесса.  Укажите в ней лимит суммы затрат.  
  
8.  В форме ассоциации введите **1000** в поле **Лимит автоматического утверждения**, а затем нажмите кнопку **Сопоставить рабочий процесс**.  
  
9. Нажмите кнопку **Домой**, чтобы вернуться на домашнюю страницу SharePoint.  
  
10. На панели быстрого запуска щелкните ссылку **Общие документы**.  
  
11. Выберите один из отправленных документов и появится раскрывающаяся стрелка, выберите ее, а затем выберите элемент **Рабочие процессы**.  
  
12. Выберите изображение рядом с рабочим процессом ExpenseTest, чтобы открыть форму запуска рабочего процесса.  
  
13. В текстовом поле **Общая сумма затрат** укажите сумму, превышающую 1000, и нажмите кнопку **Запустить рабочий процесс**.  
  
     Если сумма затрат в отчете превышает заданный лимит, в список задач добавляется задача.  Кроме того, в отчет о затратах в списке "Общие документы" добавляется столбец с именем **ExpenseTest** и значением **Выполнен**.  
  
14. Повторите действия 11—13 для других документов в списке "Общие документы". \(Точное количество документов не имеет значения.\)  
  
15. Откройте страницу приложения сводки по отчету о затратах, указав в адресной строке веб\-браузера следующий URL\-адрес: **http:\/\/***SystemName***\/\_layouts\/ExpenseReport\/ApplicationPage1.aspx**.  
  
     На странице сводки по отчету о затратах приводятся все отчеты, в которых превышен лимит затрат, указывается сумма превышения для каждого отчета и общая сумма по всем отчетам.  
  
## Следующие действия  
 Дополнительные сведения о страницах приложений SharePoint см. в разделе [Создание страниц приложений для SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).  
  
 Дополнительные сведения о разработке страниц SharePoint с помощью Visual Web Designer в Visual Studio см. в следующих разделах.  
  
-   [Создание веб-частей для SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md).  
  
-   [Создание многократно используемых пользовательских элементов управления для веб-частей или страниц приложений](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md).  
  
## См. также  
 [Пошаговое руководство. Создание рабочего процесса с формами связывания и запуска](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)   
 [Практическое руководство. Создание страницы приложения](../sharepoint/how-to-create-an-application-page.md)   
 [Создание страниц приложений для SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)   
 [Разработка решений SharePoint](../sharepoint/developing-sharepoint-solutions.md)  
  
  