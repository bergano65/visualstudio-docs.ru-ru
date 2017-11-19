---
title: "Пошаговое руководство: Создание рабочего процесса с формами связывания и запуска | Документы Microsoft"
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
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, workflows
- SharePoint development in Visual Studio, workflow association forms
- workflows [SharePoint development in Visual Studio]
- association forms [SharePoint development in Visual Studio]
- initiation forms [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, workflow initiation forms
ms.assetid: c8666d8c-b173-4245-8014-9c1cd6acb071
caps.latest.revision: "38"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: aa95c519ab24ba042b6a1adfa71c64499b18d4c9
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-creating-a-workflow-with-association-and-initiation-forms"></a>Пошаговое руководство. Создание рабочего процесса с формами связывания и запуска
  В этом пошаговом руководстве демонстрируется создание основные последовательный рабочий процесс, в котором используются формы связывания и запуска. Это ASPX-формы, задать параметры для добавления в рабочий процесс, когда сначала связано администратором SharePoint (форма связывания) и рабочий процесс запускается пользователем (формы запуска).  
  
 В этом пошаговом руководстве рассматривается сценарий, где пользователь хочет создать рабочий процесс утверждения для отчетов о расходах, необходимо соблюдать следующие требования:  
  
-   Если рабочий процесс будет связана со списком, администратор предлагается форма связывания, которой требуется ввести денежный лимит для отчетов о расходах.  
  
-   Сотрудники отправить свои отчеты о расходах в списке Общие документы, запустить рабочий процесс, а затем введите общую сумму затрат в форму запуска рабочего процесса.  
  
-   Если общий отчет о расходах сотрудника превышает предел предопределенных администратора, задача создается для руководителем сотрудника утвердить отчет по расходам. Однако если отчет о расходах сотрудника всего не превышала лимит, в список журнала рабочего процесса записывается сообщение об автоматическом утверждении.  
  
 В данном пошаговом руководстве рассмотрены следующие задачи:  
  
-   Создание проекта последовательного рабочего процесса определения списка SharePoint в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
-   Создание расписания рабочего процесса.  
  
-   Обработка событий действий рабочего процесса.  
  
-   Создание формы связывания и запуска рабочего процесса.  
  
-   Сопоставление рабочего процесса.  
  
-   Запуск рабочего процесса вручную.  
  
> [!NOTE]  
>  Хотя в этом пошаговом руководстве используется проект последовательного рабочего процесса, процесс одинаков для конечного автомата.  
>   
>  Кроме того, на компьютере могут отображаться другие имена или расположения некоторых [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] элементы пользовательского интерфейса в следующих инструкциях. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Эти элементы определяются от имеющегося выпуска и параметры, которые можно использовать. Дополнительные сведения см. в разделе [Персонализация интегрированной среды разработки Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Предварительные требования  
 Ниже приведены компоненты, необходимые для выполнения данного пошагового руководства.  
  
-   Поддерживаемые выпуски [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] и SharePoint. Дополнительные сведения см. в разделе [требования к разработке решений SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Visual Studio.  
  
## <a name="creating-a-sharepoint-sequential-workflow-project"></a>Создание проекта последовательного рабочего процесса SharePoint  
 Во-первых, создайте проект последовательного рабочего процесса в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Последовательный рабочий процесс имеет ряд шагов, выполняемых в порядке до завершения последнего действия. В этой процедуре вы создадите последовательный рабочий процесс, который применяется к списку Общие документы в SharePoint. Мастер рабочего процесса позволяет связать рабочий процесс с сайта или определения списка и позволяет определить начала рабочего процесса.  
  
#### <a name="to-create-a-sharepoint-sequential-workflow-project"></a>Чтобы создать проект последовательного рабочего процесса SharePoint  
  
1.  В строке меню выберите **файл**, **New**, **проекта** для отображения **новый проект** диалоговое окно.  
  
2.  Разверните **SharePoint** узел в рамках одного **Visual C#** или **Visual Basic**, а затем выберите **2010** узла.  
  
3.  В **шаблоны** области, выберите **проект SharePoint 2010** шаблона проекта.  
  
4.  В **имя** введите **ExpenseReport** и выберите **ОК** кнопки.  
  
     **Мастер настройки SharePoint** отображается.  
  
5.  В **Укажите сайт и уровень безопасности для отладки** выберите **развернуть как решение фермы** переключатель, а затем выберите **Готово** кнопку, чтобы принять уровень доверия и по умолчанию сайт.  
  
     Этот шаг также задается уровень доверия для решения фермы, это единственно возможный вариант для проектов рабочего процесса.  
  
6.  В области **Обозреватель решений**выберите узел проекта.  
  
7.  В строке меню выберите **проекта**, **Добавление нового элемента**.  
  
8.  В рамках одного **Visual C#** или **Visual Basic**, разверните **SharePoint** узла, а затем выберите **2010** узла.  
  
9. В **шаблоны** области, выберите **последовательный рабочий процесс (только для решения фермы)** шаблона и выберите **добавить** кнопки.  
  
     **Мастер настройки SharePoint** отображается.  
  
10. В **укажите имя рабочего процесса для отладки** примите имя по умолчанию (**ExpenseReport — Workflow1**). Оставьте значение по умолчанию шаблон рабочего процесса типа (**рабочий процесс списка)**. Выберите **Далее** кнопки.  
  
11. В **будет ли Visual Studio автоматически связывать рабочий процесс в сеансе отладки?** страницы, снимите флажок, который автоматически связывает шаблон рабочего процесса, если он установлен.  
  
     Этот шаг позволяет вручную связать рабочий процесс со списком Общие документы позднее, отобразится форма связывания.  
  
12. Выберите **Готово** кнопки.  
  
## <a name="adding-an-association-form-to-the-workflow"></a>Добавление формы связывания в рабочий процесс  
 Создайте. Форма сопоставления ASPX, который появляется, когда администратор SharePoint сначала связываются с документ отчета о расходах.  
  
#### <a name="to-add-an-association-form-to-the-workflow"></a>Добавление формы связывания в рабочий процесс  
  
1.  Выберите **Workflow1** узел в **обозревателе решений**.  
  
2.  В строке меню выберите **проекта**, **Добавление нового элемента** для отображения **Добавление нового элемента** диалоговое окно.  
  
3.  В древовидном представлении диалогового окна разверните **Visual C#** или **Visual Basic** (в зависимости от языка проекта), разверните **SharePoint** узел, а затем выберите **2010** узла.  
  
4.  В списке шаблонов выберите **форма сопоставления рабочего процесса** шаблона.  
  
5.  В **имя** текста введите **ExpenseReportAssocForm.aspx**.  
  
6.  Выберите **добавить** кнопку, чтобы добавить форму в проект.  
  
## <a name="designing-and-coding-the-association-form"></a>Проектирование и программирование формы связывания  
 В этой процедуре показана реализация функциональных возможностей формы путем добавления элементов управления и кода.  
  
#### <a name="to-design-and-code-the-association-form"></a>Разработка и программирование формы связывания  
  
1.  В форме ассоциации (ExpenseReportAssocForm.aspx), найдите `asp:Content` элемент, имеющий `ID="Main"`.  
  
2.  Непосредственно после первой строки этого элемента содержимого, добавьте следующий код, чтобы создать метку и текстовое поле, которое запрашивает лимит утверждения (*AutoApproveLimit*):  
  
    ```  
    <asp:Label ID="lblAutoApproveLimit" Text="Auto Approval Limit:" runat="server" />  
  
    <asp:TextBox ID="AutoApproveLimit" runat="server" />  
    <br /><br />  
    ```  
  
3.  Разверните **ExpenseReportAssocForm.aspx** файла в **обозревателе решений** для отображения его зависимыми файлами.  
  
    > [!NOTE]  
    >  Если проект находится в [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)], необходимо выбрать **просмотреть все файлы** кнопку, чтобы выполнить этот шаг.  
  
4.  Откройте контекстное меню для файла ExpenseReportAssocForm.aspx и выберите **Просмотр кода**.  
  
5.  Замените `GetAssociationData` метод с:  
  
    ```vb  
    Private Function GetAssociationData() As String  
        ' TODO: Return a string that contains the association data that   
        ' will be passed to the workflow. Typically, this is in XML   
        ' format.  
        Return Me.AutoApproveLimit.Text  
    End Function  
    ```  
  
    ```csharp  
    private string GetAssociationData()  
    {  
        // TODO: Return a string that contains the association data that   
        // will be passed to the workflow. Typically, this is in XML   
        // format.  
        return this.AutoApproveLimit.Text;  
    }  
    ```  
  
## <a name="adding-an-initiation-form-to-the-workflow"></a>Добавление формы запуска рабочего процесса  
 Создайте форму запуска, которое появляется при запуске рабочего процесса для отчета о затратах.  
  
#### <a name="to-create-an-initiation-form"></a>Создание формы запуска  
  
1.  Выберите **Workflow1** узел в **обозревателе решений**.  
  
2.  В строке меню выберите **проекта**, **Добавление нового элемента** отображения **Добавление нового элемента** диалоговое окно.  
  
3.  В древовидном представлении диалогового окна разверните **Visual C#** или **Visual Basic** (в зависимости от языка проекта), разверните **SharePoint** узел, а затем выберите **2010** узла.  
  
4.  В списке шаблонов выберите **форма запуска рабочего процесса** шаблона.  
  
5.  В **имя** текста введите **ExpenseReportInitForm.aspx**.  
  
6.  Выберите **добавить** кнопку, чтобы добавить форму в проект.  
  
## <a name="designing-and-coding-the-initiation-form"></a>Проектирование и программирование формы запуска  
 Теперь необходимо реализовать функциональные возможности формы запуска путем добавления элементов управления и кода.  
  
#### <a name="to-code-the-initiation-form"></a>В код формы запуска  
  
1.  Найдите в форму запуска (ExpenseReportInitForm.aspx) `asp:Content` элемент, содержащий `ID="Main"`.  
  
2.  После первой строки этого элемента содержимого, добавьте следующий код, чтобы создать метку и текстовое поле, которое отображает предельная сумма расходов на утверждение (*AutoApproveLimit*), указанный в форме связывания, а другую метку и текстовое поле для запроса общей суммы расходов (*ExpenseTotal*):  
  
    ```  
    <asp:Label ID="lblAutoApproveLimit" Text="Auto Approval Limit:" runat="server" />  
  
    <asp:TextBox ID="AutoApproveLimit" ReadOnly="true" runat="server" />  
    <br /><br />  
    <asp:Label ID="lblExpenseTotal" Text="Expense Total:" runat="server" />  
  
    <asp:TextBox ID="ExpenseTotal" runat="server" />  
    <br /><br />  
    ```  
  
3.  Разверните **ExpenseReportInitForm.aspx** файла в **обозревателе решений** для отображения его зависимыми файлами.  
  
4.  Откройте контекстное меню для файла ExpenseReportInitForm.aspx и выберите **Просмотр кода**.  
  
5.  Замените `Page_Load` метод в следующем примере:  
  
    ```vb  
    Protected Sub Page_Load(ByVal sender As Object, ByVal e As   
      EventArgs) Handles Me.Load  
        InitializeParams()  
        Me.AutoApproveLimit.Text = workflowList.WorkflowAssociations(New   
          Guid(associationGuid)).AssociationData  
        ' Optionally, add code here to pre-populate your form fields.  
    End Sub  
    ```  
  
    ```csharp  
    protected void Page_Load(object sender, EventArgs e)  
    {  
        InitializeParams();  
        this.AutoApproveLimit.Text =   
          workflowList.WorkflowAssociations[new   
          Guid(associationGuid)].AssociationData;  
    }  
    ```  
  
6.  Замените `GetInitiationData` метод в следующем примере:  
  
    ```vb  
    ' This method is called when the user clicks the button to start the workflow.  
    Private Function GetInitiationData() As String  
        Return Me.ExpenseTotal.Text  
        ' TODO: Return a string that contains the initiation data that   
        ' will be passed to the workflow. Typically, this is in XML   
        ' format.  
        Return String.Empty  
    End Function  
    ```  
  
    ```csharp  
    // This method is called when the user clicks the button to start the workflow.          
    private string GetInitiationData()  
    {  
        // TODO: Return a string that contains the initiation data that   
        // will be passed to the workflow. Typically, this is in XML   
        // format.  
        return this.ExpenseTotal.Text;  
    }  
    ```  
  
## <a name="customizing-the-workflow"></a>Настройка рабочего процесса  
 Теперь необходимо настроить рабочий процесс. Позже будет связывать две формы рабочего процесса.  
  
#### <a name="to-customize-the-workflow"></a>Настройка рабочего процесса  
  
1.  Отобразить рабочий процесс в конструкторе рабочих процессов, открыв Workflow1 в проекте.  
  
2.  В **элементов**, разверните **Windows Workflow v3.0** узла и найдите **IfElse** действия.  
  
3.  Добавьте это действие в рабочий процесс, выполнив одно из следующих действий:  
  
    -   Откройте контекстное меню для **IfElse** действия, выберите **копирования**, откройте контекстное меню для строки в группе **onWorkflowActivated1** действия в конструкторе рабочих процессов а затем выберите **вставить**.  
  
    -   Перетащите **IfElse** действия из **элементов**и подключите его к строке под **onWorkflowActiviated1** действия в конструкторе рабочих процессов.  
  
4.  В области элементов разверните **рабочего процесса SharePoint** узла и найдите **CreateTask** действия.  
  
5.  Добавьте это действие в рабочий процесс, выполнив одно из следующих действий:  
  
    -   Откройте контекстное меню для **CreateTask** действия, выберите **копирования**, откройте контекстное меню для одного из двух **перетащите действия сюда** областям  **Действии IfElseActivity1** в конструкторе рабочих процессов, а затем выберите **вставить**.  
  
    -   Перетащите **CreateTask** действия из **элементов** на один из двух **перетащите действия сюда** областям **действии IfElseActivity1**.  
  
6.  В **свойства** окно, введите значение свойства *taskToken* для **CorrelationToken** свойство.  
  
7.  Разверните **CorrelationToken** свойства, нажав знак «плюс» (![плюс просмотра дерева](../sharepoint/media/plus.gif "плюс просмотра дерева")) рядом с ним.  
  
8.  Щелкните стрелку раскрывающегося списка на **OwnerActivityName** свойстве и задайте *Workflow1* значение.  
  
9. Выберите **TaskId** свойства, а затем нажмите кнопку с многоточием (![эллипс конструктора ASP.NET Mobile](../sharepoint/media/mwellipsis.gif "эллипс конструктора ASP.NET Mobile")) кнопку, чтобы отобразить **Привязка свойства** диалоговое окно.  
  
10. Выберите **привязка к новому члену** выберите **создать поле** переключатель, а затем выберите **ОК** кнопки.  
  
11. Выберите **TaskProperties** свойства, а затем нажмите кнопку с многоточием (![эллипс конструктора ASP.NET Mobile](../sharepoint/media/mwellipsis.gif "эллипс конструктора ASP.NET Mobile")) кнопку, чтобы отобразить  **Привязать свойство** диалоговое окно.  
  
12. Выберите **привязка к новому члену** выберите **создать поле** переключатель, а затем выберите **ОК** кнопки.  
  
13. В **элементов**, разверните **рабочего процесса SharePoint** узел и найдите **LogToHistoryListActivity** действия.  
  
14. Добавьте это действие в рабочий процесс, выполнив одно из следующих действий:  
  
    -   Откройте контекстное меню для **LogToHistoryListActivity** действия, выберите **копирования**, откройте контекстное меню для других **перетащите действия сюда** область в пределах **Действии IfElseActivity1** в конструкторе рабочих процессов, а затем выберите **вставить**.  
  
    -   Перетащите **LogToHistoryListActivity** действия из **элементов**и поместите его на другой **перетащите действия сюда** область в пределах **действии IfElseActivity1** .  
  
## <a name="adding-code-to-the-workflow"></a>Добавление кода для рабочего процесса  
 Добавьте код в рабочий процесс, обеспечивающий его функции.  
  
#### <a name="to-add-code-to-the-workflow"></a>Добавление кода в рабочий процесс  
  
1.  Откройте контекстное меню для **createTask1** действия в конструкторе рабочих процессов и выберите **Просмотр кода**.  
  
2.  Добавьте следующий метод:  
  
    ```vb  
    Private Sub createTask1_MethodInvoking(ByVal sender As   
      System.Object, ByVal e As System.EventArgs)  
        createTask1_TaskId1 = Guid.NewGuid  
        createTask1_TaskProperties1.AssignedTo = "somedomain\\someuser"  
        createTask1_TaskProperties1.Description = "Please approve the   
          expense report"  
        createTask1_TaskProperties1.Title = "Expense Report Approval   
          Needed"  
    End Sub   
    ```  
  
    ```csharp  
    private void createTask1_MethodInvoking(object sender, EventArgs e)  
    {  
        createTask1_TaskId1 = Guid.NewGuid();  
        createTask1_TaskProperties1.AssignedTo = "somedomain\\someuser";  
        createTask1_TaskProperties1.Description = "Please approve the   
          expense report";  
        createTask1_TaskProperties1.Title = "Expense Report Approval   
          Needed";  
    }   
    ```  
  
    > [!NOTE]  
    >  В коде, замените `somedomain\\someuser` с именем домена и пользователя, для которого задача будет создан, такие как «`Office\\JoeSch`». Для тестирования проще всего использовать учетную запись, разрабатываемом с.  
  
3.  Ниже `MethodInvoking` метод, добавьте следующий пример:  
  
    ```vb  
    Private Sub checkApprovalNeeded(ByVal sender As Object, ByVal e As   
      ConditionalEventArgs)  
        Dim approval As Boolean = False  
        If (Convert.ToInt32(workflowProperties.InitiationData) >   
          Convert.ToInt32(workflowProperties.AssociationData)) Then  
            approval = True  
        End If  
        e.Result = approval  
    End Sub   
    ```  
  
    ```csharp  
    private void checkApprovalNeeded(object sender, ConditionalEventArgs   
      e)  
    {  
        bool approval = false;  
        if (Convert.ToInt32(workflowProperties.InitiationData) >   
          Convert.ToInt32(workflowProperties.AssociationData))  
        {  
            approval = true;  
        }  
        e.Result = approval;  
    }   
    ```  
  
4.  В конструкторе рабочих процессов, выберите **ifElseBranchActivity1** действия.  
  
5.  В **свойства** окно, щелкните стрелку раскрывающегося списка для **условие** , а затем установите *условие кода* значение.  
  
6.  Разверните **условие** свойства, нажав знак «плюс» (![плюс просмотра дерева](../sharepoint/media/plus.gif "плюс просмотра дерева")) рядом с ним и затем установите для него значение *checkApprovalNeeded* .  
  
7.  В конструкторе рабочих процессов откройте контекстное меню для **logToHistoryListActivity1** действия и выберите **создать обработчики** для создания пустой метод для `MethodInvoking` события.  
  
8.  Замените `MethodInvoking` код следующим:  
  
    ```vb  
    Private Sub logToHistoryListActivity1_MethodInvoking(ByVal sender As   
      System.Object, ByVal e As System.EventArgs)  
        Me.logToHistoryListActivity1.HistoryOutcome = ("Expense was auto   
          approved for " + workflowProperties.InitiationData)  
    End Sub   
    ```  
  
    ```csharp  
    private void logToHistoryListActivity1_MethodInvoking(object sender,   
      EventArgs e)  
    {  
        this.logToHistoryListActivity1.HistoryOutcome = "Expense was   
          auto approved for " + workflowProperties.InitiationData;  
    }   
    ```  
  
9. Нажмите клавишу F5 для отладки программы.  
  
     Это компиляции приложения, пакеты его, развертывает его, активация его компонентов, запускается повторно [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] пул приложений и затем запускается в браузере в расположении, указанный в **URL-адрес сайта** свойство.  
  
## <a name="associating-the-workflow-to-the-documents-list"></a>Сопоставление рабочего процесса в список документов  
 Далее отобразить форму связывания рабочего процесса, связав его с **SharedDocuments** список на сайте SharePoint.  
  
#### <a name="to-associate-the-workflow"></a>Связывать рабочий процесс  
  
1.  Выберите **Общие документы** ссылку на панели быстрого запуска.  
  
2.  Выберите **библиотеки** ссылку **Инструменты библиотеки** и нажмите кнопку **параметры библиотеки** на ленте.  
  
3.  В **разрешения и управление** выберите **параметры рабочего процесса** ссылку и выберите **Добавление рабочего процесса** ссылку **рабочихпроцессов** страницы.  
  
4.  В верхнем списке на странице параметров рабочего процесса, выберите **ExpenseReport — Workflow1** шаблона.  
  
5.  В следующем поле введите **ExpenseReportWorkflow** и выберите **Далее** кнопки.  
  
     Это связывает рабочий процесс с **Общие документы** списка и отображается форма сопоставления рабочего процесса.  
  
6.  В **лимит автоматического утверждения** текста введите **1200** и выберите **сопоставить рабочий процесс** кнопки.  
  
## <a name="starting-the-workflow"></a>Запуск рабочего процесса  
 Теперь необходимо связать рабочий процесс для одного документа в **Общие документы** списка, чтобы открыть форму запуска рабочего процесса.  
  
#### <a name="to-start-the-workflow"></a>Чтобы запустить рабочий процесс  
  
1.  На странице SharePoint выберите **Главная** кнопки.  
  
2.  Выберите **Общие документы** ссылку на панели быстрого запуска для отображения **Общие документы** списка.  
  
3.  Выберите **документов** ссылку **Инструменты библиотеки** в верхней части страницы, а затем выберите **отправить документ** кнопка на ленте, чтобы загрузить новый документ в **Общие документы** списка.  
  
4.  В **отправить документ** диалогового окна выберите **Обзор** , выберите любой файл документа, нажмите **откройте** , а затем кнопку **ОК** кнопки.  
  
     Можно изменять параметры документа в этом диалоговом окне, но оставьте значения по умолчанию, выбрав **Сохранить** кнопки.  
  
5.  Выберите загруженный документ, щелкните стрелку раскрывающегося списка и нажмите кнопку **рабочих процессов** элемента.  
  
6.  Выберите изображение рядом с ExpenseReportWorkflow.  
  
     Откроется форма запуска рабочего процесса. (Обратите внимание, что значение отображается в **лимит автоматического утверждения** поле доступно только для чтения, так как оно введено в форме связывания.)  
  
7.  В **Общая сумма затрат** текста введите **1600**, а затем выберите **запустить рабочий процесс** кнопки.  
  
     При этом отображаются **Общие документы** снова. Новый столбец с именем **ExpenseReportWorkflow** со значением **завершено** добавляется к элементу, просто запустить рабочий процесс.  
  
8.  Нажмите стрелку раскрывающегося списка рядом с отправленным документом и выберите **рабочих процессов** элемент, чтобы открыть страницу состояния рабочего процесса. Выберите **завершено** в разделе **выполненные рабочие процессы**. Задача находится в списке **задачи** раздела.  
  
9. Выберите заголовок задачи, чтобы отобразить сведения о ней.  
  
10. Вернитесь к **SharedDocuments** списка и перезапустите рабочий процесс, используя тот же документ или любой другой.  
  
11. Введите сумму на странице запуска, которое меньше или равно указанную на странице связывания (**1200**).  
  
     В этом случае вместо задачи создается запись в списке журнала. Она отображается в **журнала рабочего процесса** раздел на странице состояния рабочего процесса. Обратите внимание на сообщение в **результат** столбца события в журнале. Он содержит текст, введенный в `logToHistoryListActivity1.MethodInvoking` события, которое содержит сумму, которое было автоматически выполнено.  
  
## <a name="next-steps"></a>Дальнейшие действия  
 Дополнительные сведения о создании шаблонов рабочих процессов в следующих разделах:  
  
-   Дополнительные сведения о рабочих процессах SharePoint см. в разделе [рабочих процессов в Windows SharePoint Services](http://go.microsoft.com/fwlink/?LinkID=166275).  
  
## <a name="see-also"></a>См. также  
 [Создание решений рабочих процессов SharePoint](../sharepoint/creating-sharepoint-workflow-solutions.md)   
 [Пошаговое руководство. Добавление страницы приложения в рабочий процесс](../sharepoint/walkthrough-add-an-application-page-to-a-workflow.md)  
  
  