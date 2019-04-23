---
title: Пошаговое руководство. Создание рабочего процесса с формами связывания и запуска | Документация Майкрософт
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, workflows
- SharePoint development in Visual Studio, workflow association forms
- workflows [SharePoint development in Visual Studio]
- association forms [SharePoint development in Visual Studio]
- initiation forms [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, workflow initiation forms
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 43ee8d26338b6d15530c51191c3368d3fc556d2c
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60081740"
---
# <a name="walkthrough-create-a-workflow-with-association-and-initiation-forms"></a>Пошаговое руководство. Создание рабочего процесса с формами связывания и запуска
  В этом пошаговом руководстве показано, как создать базовый последовательный рабочий процесс, в котором используются формы ассоциации и инициации. Это формы ASPX, которые позволят параметров добавляться в рабочий процесс, когда он сначала связан администратором SharePoint (форма сопоставления) и когда рабочий процесс запускается пользователем (форма запуска).

 В этом пошаговом руководстве рассматривается сценарий, в котором пользователь хочет создать рабочий процесс утверждения для отчетов о расходах, предъявляются следующие требования:

- Если рабочий процесс связан со списком, администратор увидит форму ассоциации, где они ввести денежный лимит для отчетов о расходах.

- Сотрудники отправить свои отчеты о расходах в список общих документов, запуск рабочего процесса, а затем введите общую сумму затрат в форма запуска рабочего процесса.

- Если общего отчета о расходах сотрудника превышает предел ежедневного администратора, задача создается для руководителя для утверждения отчета о расходах. Тем не менее если общее число отчетов о расходах сотрудника превышает лимит, в список журнала рабочего процесса записывается сообщение утверждено автоматически.

  В данном пошаговом руководстве рассмотрены следующие задачи:

- Создание проекта последовательного рабочего процесса определения списка SharePoint в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

- Создание расписания рабочего процесса.

- Обработка событий действий рабочего процесса.

- Создание формы ассоциации и инициации рабочего процесса.

- Сопоставление рабочего процесса.

- Запуск рабочего процесса вручную.

> [!NOTE]
>  Несмотря на то, что в этом пошаговом руководстве используется проект последовательного рабочего процесса, процесс одинаков для рабочих процессов конечного автомата состояния.
>
>  Кроме того, на компьютере могут отображаться другие имена или расположения для некоторых [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] элементы пользовательского интерфейса в следующих инструкциях. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Имеющегося выпуска и параметры, которые используются определить эти элементы. Дополнительные сведения см. в разделе [Персонализация интегрированной среды разработки Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Предварительные требования
 Ниже приведены компоненты, необходимые для выполнения данного пошагового руководства.

- Поддерживаемые выпуски [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] и SharePoint.

- Visual Studio.

## <a name="create-a-sharepoint-sequential-workflow-project"></a>Создание проекта последовательного рабочего процесса SharePoint
 Во-первых, создайте проект последовательного рабочего процесса в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Последовательный рабочий процесс представляет собой ряд шагов, выполняемых в порядке до завершения последнего действия. В этой процедуре вы создадите последовательный рабочий процесс, который применяется к списку Shared Documents в SharePoint. Мастер рабочего процесса позволяет связать рабочий процесс с сайта или определения списка и позволяет определить начала рабочего процесса.

#### <a name="to-create-a-sharepoint-sequential-workflow-project"></a>Создание проекта последовательного рабочего процесса SharePoint

1. В строке меню выберите **файл** > **New** > **проекта** для отображения **новый проект** диалоговое окно.

2. Разверните **SharePoint** расположенный в области **Visual C#** или **Visual Basic**, а затем выберите **2010** узла.

3. В **шаблоны** панели выберите **проект SharePoint 2010** шаблона проекта.

4. В **имя** введите **ExpenseReport** и выберите **ОК** кнопки.

     **Мастер настройки SharePoint** отображается.

5. В **Укажите сайт и уровень безопасности для отладки** выберите **развернуть как решение фермы** переключатель, а затем выберите **Готово** кнопку, чтобы принять доверие уровень и сайт по умолчанию.

     Этот шаг также задает уровень доверия для решения, как решение фермы, который является единственным доступным параметром для проектов рабочих процессов.

6. В области **Обозреватель решений**выберите узел проекта.

7. В строке меню выберите **Проект** > **Добавить новый элемент**.

8. В группе **Visual C#** или **Visual Basic**, разверните **SharePoint** узел, а затем выберите **2010** узла.

9. В **шаблоны** панели выберите **последовательного рабочего процесса (только для решения фермы)** шаблона и нажмите кнопку **добавить** кнопки.

     **Мастер настройки SharePoint** отображается.

10. В **укажите имя рабочего процесса для отладки** странице, примите имя по умолчанию (**ExpenseReport — Workflow1**). Оставьте значение по умолчанию шаблон рабочего процесса типа (**рабочий процесс списка)**. Нажмите кнопку **Далее**.

11. В **будет ли Visual Studio автоматически связывать рабочий процесс в сеансе отладки?** странице, снимите флажок, который автоматически связывает шаблон рабочего процесса, если он установлен.

     Этот шаг позволяет вручную связать рабочий процесс со списком Общие документы позже, отображающий форму сопоставления.

12. Выберите **Готово** кнопки.

## <a name="add-an-association-form-to-the-workflow"></a>Добавление формы связывания в рабочий процесс
 Создайте. Форма связи ASPX, которая появляется, когда администратор SharePoint сначала связываются с документ отчета о расходах.

#### <a name="to-add-an-association-form-to-the-workflow"></a>Чтобы добавить форму сопоставления рабочего процесса

1. Выберите **Workflow1** узел в **обозревателе решений**.

2. В строке меню выберите **проекта** > **Добавление нового элемента** для отображения **Добавление нового элемента** диалоговое окно.

3. В представлении в виде дерева поле диалогового окна разверните **Visual C#** или **Visual Basic** (в зависимости от языка проекта), разверните **SharePoint** узел, а затем выберите **2010** узла.

4. В списке шаблонов выберите **форма сопоставления рабочего процесса** шаблона.

5. В **имя** текста введите **ExpenseReportAssocForm.aspx**.

6. Выберите **добавить** кнопку, чтобы добавить форму в проект.

## <a name="designing-and-coding-the-association-form"></a>Разработка и программирование формы связывания
 В этой процедуре показана реализация функциональных форма сопоставления путем добавления элементов управления и кода.

#### <a name="to-design-and-code-the-association-form"></a>Разработка и программирование формы связывания

1. В форме ассоциации (ExpenseReportAssocForm.aspx) найдите `asp:Content` элемент, имеющий `ID="Main"`.

2. Непосредственно после первой строки этого элемента содержимого, добавьте следующий код, чтобы создать метку и текстовое поле, которое запрашивает лимит утверждения (*AutoApproveLimit*):

    ```aspx-csharp
    <asp:Label ID="lblAutoApproveLimit" Text="Auto Approval Limit:" runat="server" />

    <asp:TextBox ID="AutoApproveLimit" runat="server" />
    <br /><br />
    ```

3. Разверните **ExpenseReportAssocForm.aspx** файл **обозревателе решений** для отображения его зависимыми файлами.

    > [!NOTE]
    >  Если проект находится в [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)], необходимо выбрать **просмотреть все файлы** кнопку, чтобы выполнить этот шаг.

4. Откройте контекстное меню для файла ExpenseReportAssocForm.aspx и выберите **Просмотр кода**.

5. Замените `GetAssociationData` метод с:

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

## <a name="add-an-initiation-form-to-the-workflow"></a>Добавить форму инициации рабочего процесса
 Создайте форму запуска, который отображается, когда пользователи запускают рабочий процесс для отчета о затратах.

#### <a name="to-create-an-initiation-form"></a>Чтобы создать форму инициации

1. Выберите **Workflow1** узел в **обозревателе решений**.

2. В строке меню выберите **проекта** > **Добавление нового элемента** отображения **Добавление нового элемента** диалоговое окно.

3. В представлении в виде дерева поле диалогового окна разверните **Visual C#** или **Visual Basic** (в зависимости от языка проекта), разверните **SharePoint** узел, а затем выберите **2010** узла.

4. В списке шаблонов выберите **форма запуска рабочего процесса** шаблона.

5. В **имя** текста введите **ExpenseReportInitForm.aspx**.

6. Выберите **добавить** кнопку, чтобы добавить форму в проект.

## <a name="designing-and-coding-the-initiation-form"></a>Разработка и программирование формы запуска
 Теперь необходимо реализовать функциональность формы запуска путем добавления элементов управления и кода.

#### <a name="to-code-the-initiation-form"></a>В код формы запуска

1. В форму инициации (ExpenseReportInitForm.aspx), найдите `asp:Content` элемент, содержащий `ID="Main"`.

2. После первой строки этого элемента содержимого, добавьте следующий код, чтобы создать метку и текстовое поле, которое отображает утверждения лимит (*AutoApproveLimit*), введенное в форме ассоциации, а другую метку и текстовое поле, чтобы запрашивались суммы расходов (*ExpenseTotal*):

    ```aspx-csharp
    <asp:Label ID="lblAutoApproveLimit" Text="Auto Approval Limit:" runat="server" />

    <asp:TextBox ID="AutoApproveLimit" ReadOnly="true" runat="server" />
    <br /><br />
    <asp:Label ID="lblExpenseTotal" Text="Expense Total:" runat="server" />

    <asp:TextBox ID="ExpenseTotal" runat="server" />
    <br /><br />
    ```

3. Разверните **ExpenseReportInitForm.aspx** файл **обозревателе решений** для отображения его зависимыми файлами.

4. Откройте контекстное меню для файла ExpenseReportInitForm.aspx и выберите **Просмотр кода**.

5. Замените `Page_Load` метода показано в следующем примере:

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

6. Замените `GetInitiationData` метода показано в следующем примере:

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

## <a name="cutomize-the-workflow"></a>Настройка рабочего процесса
 Теперь необходимо настройте рабочий процесс. Позже нужно связать две формы в рабочий процесс.

#### <a name="to-customize-the-workflow"></a>Чтобы настроить рабочий процесс

1. Отобразить рабочий процесс в конструкторе рабочих процессов, открыв Workflow1 в проекте.

2. В **элементов**, разверните **Windows Workflow v3.0** узла и найдите **IfElse** действия.

3. Добавьте это действие в рабочий процесс, выполнив одно из следующих действий:

    - Откройте контекстное меню для **IfElse** действия, выберите **копирования**, откройте контекстное меню для строки под **onWorkflowActivated1** действие в конструкторе рабочих процессов а затем выберите **вставить**.

    - Перетащите **IfElse** действия из **элементов**и подключите его к строке под **onWorkflowActiviated1** действия в конструкторе рабочих процессов.

4. В области элементов разверните **рабочего процесса SharePoint** узла и найдите **CreateTask** действия.

5. Добавьте это действие в рабочий процесс, выполнив одно из следующих действий:

    - Откройте контекстное меню для **CreateTask** действия, выберите **копирования**, откройте контекстное меню для одного из двух **Перетащите сюда действия** областям  **IfElseActivity1** в конструкторе рабочих процессов, а затем выберите **вставить**.

    - Перетащите **CreateTask** действия из **элементов** на один из двух **Перетащите сюда действия** областям **IfElseActivity1**.

6. В **свойства** окно, введите значение свойства *taskToken* для **CorrelationToken** свойство.

7. Разверните **CorrelationToken** свойство, щелкнув знак «плюс» (![плюс просмотра дерева](../sharepoint/media/plus.gif "плюс просмотра дерева")) рядом с ним.

8. Выберите стрелку раскрывающегося списка на **OwnerActivityName** свойстве и задайте *Workflow1* значение.

9. Выберите **TaskId** свойства, а затем нажмите кнопку с многоточием (![эллипс конструктора ASP.NET Mobile](../sharepoint/media/mwellipsis.gif "эллипс конструктора ASP.NET Mobile")) кнопку, чтобы отобразить **Привязка свойства** диалоговое окно.

10. Выберите **привязка к новому члену** вкладке, выберите **создать поле** переключатель, а затем выберите **ОК** кнопки.

11. Выберите **TaskProperties** свойства, а затем нажмите кнопку с многоточием (![эллипс конструктора ASP.NET Mobile](../sharepoint/media/mwellipsis.gif "эллипс конструктора ASP.NET Mobile")) кнопку, чтобы отобразить  **Привязать свойство** диалоговое окно.

12. Выберите **привязка к новому члену** вкладке, выберите **создать поле** переключатель, а затем выберите **ОК** кнопки.

13. В **элементов**, разверните **рабочего процесса SharePoint** узел и найдите **LogToHistoryListActivity** действия.

14. Добавьте это действие в рабочий процесс, выполнив одно из следующих действий:

    - Откройте контекстное меню для **LogToHistoryListActivity** действия, выберите **копирования**, откройте контекстное меню для других **Перетащите сюда действий** область в пределах **IfElseActivity1** в конструкторе рабочих процессов, а затем выберите **вставить**.

    - Перетащите **LogToHistoryListActivity** действия из **элементов**и поместите его на другой **Перетащите сюда действия** область в пределах **IfElseActivity1** .

## <a name="add-code-to-the-workflow"></a>Добавьте код в рабочий процесс
 Затем добавьте код в рабочий процесс для обеспечения его функциональности.

#### <a name="to-add-code-to-the-workflow"></a>Добавление кода в рабочий процесс

1. Откройте контекстное меню для **createTask1** действия в конструкторе рабочих процессов, а затем выберите **Просмотр кода**.

2. Добавьте следующий метод:

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
    >  В коде, замените `somedomain\\someuser` с именем домена и пользователя, для которого создается задача, например, "`Office\\JoeSch`«. Для тестирования можно легко использовать учетную запись, которую вы разрабатываете с.

3. Ниже `MethodInvoking` метод, добавьте приведенный ниже:

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

4. В конструкторе рабочих процессов, выберите **ifElseBranchActivity1** действия.

5. В **свойства** окно, выберите стрелку раскрывающегося списка **условие** свойства, а затем задайте *условие кода* значение.

6. Разверните **условие** свойство, щелкнув знак «плюс» (![плюс просмотра дерева](../sharepoint/media/plus.gif "плюс просмотра дерева")) рядом с ним, а затем присвойте ему значение *checkApprovalNeeded* .

7. В конструкторе рабочих процессов откройте контекстное меню для **logToHistoryListActivity1** действия, а затем выберите **создать обработчики** для создания пустой метод для `MethodInvoking` событий.

8. Замените `MethodInvoking` код следующим:

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

9. Выберите **F5** ключ для отладки программы.

     Это компилирует приложение, упаковывает его, развертывает его, активация его компонентов, перезапускается [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] пул приложений и затем начинает браузера в расположении, указанный в **URL-адрес сайта** свойство.

## <a name="associating-the-workflow-to-the-documents-list"></a>Сопоставление рабочего процесса в список документов
 Затем откройте форма сопоставления рабочего процесса, сопоставление рабочего процесса с **SharedDocuments** списка на сайте SharePoint.

#### <a name="to-associate-the-workflow"></a>Связывать рабочий процесс

1. Выберите **Общие документы** ссылку на панели быстрого запуска.

2. Выберите **библиотеки** ссылку на **средства библиотеки** вкладку **параметры библиотеки** кнопка на ленте.

3. В **разрешения и управление** выберите **параметры рабочего процесса** ссылку, а затем выберите **Добавить рабочий процесс** ссылку на **рабочихпроцессов** страницы.

4. В верхнем списке на странице параметров рабочего процесса, выберите **ExpenseReport — Workflow1** шаблона.

5. В следующем поле введите **ExpenseReportWorkflow** и выберите **Далее** кнопки.

     Это связывает рабочий процесс с **Общие документы** список и отображается форма сопоставления рабочего процесса.

6. В **лимит автоматического утверждения** текста введите **1200** и выберите **сопоставить рабочий процесс** кнопки.

## <a name="start-the-workflow"></a>Запуск рабочего процесса
 Теперь необходимо связать рабочий процесс для одного из документов в **Общие документы** списка, чтобы открыть форму запуска рабочего процесса.

#### <a name="to-start-the-workflow"></a>Запуск рабочего процесса

1. На странице SharePoint выберите **Главная** кнопки.

2. Выберите **Общие документы** ссылку на панели быстрого запуска для отображения **Общие документы** списка.

3. Выберите **документов** ссылку на **средства библиотеки** вкладке в верхней части страницы, а затем выберите **отправить документ** кнопку на ленте, чтобы отправить новый документ в **Общие документы** списка.

4. В **отправить документ** диалоговое окно, выберите **Обзор** кнопку, щелкните любой файл документа, выберите пункт **откройте** кнопку, а затем выберите **ОК** кнопки.

     Можно изменить параметры для документа в этом диалоговом окне, но оставьте значения по умолчанию, выбрав **Сохранить** кнопки.

5. Выберите отправленный документ, нажмите стрелку раскрывающегося списка, который отображается, а затем выберите **рабочие процессы** элемента.

6. Выберите изображение рядом с ExpenseReportWorkflow.

     Откроется форма запуска рабочего процесса. (Обратите внимание, что значение отображается в **лимит автоматического утверждения** поле только для чтения, так как он был введен в форме ассоциации.)

7. В **Общая сумма затрат** текста введите **1600**, а затем выберите **запуск рабочего процесса** кнопки.

     Откроется **Общие документы** еще раз список. Новый столбец с именем **ExpenseReportWorkflow** со значением **завершено** добавляется к элементу, который только что.

8. Нажмите кнопку со стрелкой раскрывающегося списка рядом с отправленного документа, а затем выберите **рабочие процессы** элемент для отображения на странице состояния рабочего процесса. Выберите **завершено** в разделе **выполненные рабочие процессы**. Задача находится в списке **задачи** раздел.

9. Выберите заголовок задачи, чтобы отобразить сведения о ней.

10. Вернитесь к **SharedDocuments** список и перезапустить рабочий процесс, используя тот же документ или любой другой.

11. Ввести сумму на странице запуска, которое меньше или равно указанную на странице связывания (**1200**).

     В этом случае вместо задачи создается запись в списке журнала. Она отображается в **журнал рабочего процесса** раздел на странице состояния рабочего процесса. Обратите внимание на сообщение в **результат** столбца события в журнале. Он содержит текст, введенный в `logToHistoryListActivity1.MethodInvoking` события, которое содержит сумму, которое было утверждено автоматически.

## <a name="next-steps"></a>Следующие шаги
 Дополнительные сведения о создании шаблонов рабочих процессов в следующих разделах:

- Дополнительные сведения о рабочих процессах SharePoint, см. в разделе [рабочие процессы в Windows SharePoint Services](http://go.microsoft.com/fwlink/?LinkID=166275).

## <a name="see-also"></a>См. также
- [Создание решений рабочих процессов SharePoint](../sharepoint/creating-sharepoint-workflow-solutions.md)
- [Пошаговое руководство: Добавление страницы приложения в рабочий процесс](../sharepoint/walkthrough-add-an-application-page-to-a-workflow.md)
