---
title: "Пошаговое руководство. Вызов кода из VBA в надстройках VSTO"
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
  - "VBA [разработка решений Office в Visual Studio], вызов кода в надстройках уровня приложения"
  - "надстройки уровня приложения [разработка решений Office в Visual Studio], вызов кода из других решений"
  - "видеоинструкции, разработка решений Office в Visual Studio"
  - "вызов кода надстройки"
  - "надстройки [разработка решений Office в Visual Studio], вызов кода из других решений"
  - "взаимодействие [разработка решений Office в Visual Studio]"
  - "вызов кода из VBA"
ms.assetid: 9c04d1df-0d93-473c-85fd-02dc2e956c9e
caps.latest.revision: 48
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 44
---
# Пошаговое руководство. Вызов кода из VBA в надстройках VSTO
  В этом пошаговом руководстве показано, как предоставить объект в надстройке VSTO другим решениям Microsoft Office, включая Visual Basic для приложений \(VBA\) и надстроек VSTO COM.  
  
 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]  
  
 Хотя в этом пошаговом руководстве используется Excel, рассмотренная процедура применима к любому шаблону проекта надстройки VSTO, которые предоставляет Visual Studio.  
  
 В данном пошаговом руководстве рассмотрены следующие задачи:  
  
-   Определение класса, который может быть предоставлен другим решениям Office.  
  
-   Предоставление класса другим решениям Office.  
  
-   Вызов метода класса из кода VBA.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Обязательные компоненты  
 Ниже приведены компоненты, необходимые для выполнения данного пошагового руководства.  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Excel  
  
## Создание проекта надстройки VSTO  
 Первым шагом является создание проекта надстройки VSTO для Excel.  
  
#### Создание нового проекта  
  
1.  Создайте проект надстройки VSTO для Excel с именем **ExcelImportData** с помощью шаблона проекта надстройки VSTO для Excel. Для получения дополнительной информации см. [Практическое руководство. Создание проектов Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] открывает файл кода **ThisAddIn.cs** или **ThisAddIn.vb** и добавляет проект **ExcelImportData** в **обозреватель решений**.  
  
## Определение класса, который можно предоставить другим решениям Office  
 В этом пошаговом руководстве описывается вызов метода `ImportData` класса с именем `AddInUtilities` в надстройке VSTO из кода VBA. Этот метод записывает строку в ячейку A1 активного листа.  
  
 Для предоставления класса `AddInUtilities` другим решениям Office необходимо сделать класс общедоступным и видимым для COM. Необходимо также предоставить интерфейс [IDispatch](http://msdn.microsoft.com/ru-ru/ebbff4bc-36b2-4861-9efa-ffa45e013eb5) в классе. Код в следующей процедуре демонстрирует один из способов выполнения этих требований. Для получения дополнительной информации см. [Вызов кода в надстройках VSTO из других решений Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md).  
  
#### Определение класса, который можно предоставить другим решениям Office  
  
1.  В меню **Проект** выберите пункт **Добавить класс**.  
  
2.  В диалоговом окне **Добавить новый элемент** измените имя нового класса на **AddInUtilities** и нажмите кнопку **Добавить**.  
  
     В редакторе кода откроется файл **AddInUtilities.cs** или **AddInUtilities.vb**.  
  
3.  Добавьте следующие инструкции в начало файла.  
  
     [!code-csharp[Trin_AddInInteropWalkthrough#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_AddInInteropWalkthrough/CS/AddInUtilities.cs#2)]
     [!code-vb[Trin_AddInInteropWalkthrough#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_AddInInteropWalkthrough/VB/AddInUtilities.vb#2)]  
  
4.  Замените класс `AddInUtilities` на следующий код.  
  
     [!code-csharp[Trin_AddInInteropWalkthrough#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_AddInInteropWalkthrough/CS/AddInUtilities.cs#3)]
     [!code-vb[Trin_AddInInteropWalkthrough#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_AddInInteropWalkthrough/VB/AddInUtilities.vb#3)]  
  
     Этот код делает класс `AddInUtilities` видимым для COM, а также добавляет метод `ImportData` в класс. Для предоставления интерфейса [IDispatch](http://msdn.microsoft.com/ru-ru/ebbff4bc-36b2-4861-9efa-ffa45e013eb5) класс `AddInUtilities` также содержит атрибут <xref:System.Runtime.InteropServices.ClassInterfaceAttribute>, который реализует интерфейс, видимый для COM.  
  
## Предоставление класса другим решениям Office  
 Для предоставления класса `AddInUtilities` другим решениям Office переопределите метод <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> в классе `ThisAddIn`. В переопределении верните экземпляр класса `AddInUtilities`.  
  
#### Предоставление класса AddInUtilities другим решениям Office  
  
1.  В **обозревателе решений** разверните **Excel**.  
  
2.  Щелкните правой кнопкой мыши **ThisAddIn.cs** или **ThisAddIn.vb**, а затем выберите пункт **Просмотреть код**.  
  
3.  Добавьте следующий код в класс `ThisAddIn`.  
  
     [!code-csharp[Trin_AddInInteropWalkthrough#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_AddInInteropWalkthrough/CS/ThisAddIn.cs#1)]
     [!code-vb[Trin_AddInInteropWalkthrough#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_AddInInteropWalkthrough/VB/ThisAddIn.vb#1)]  
  
4.  В меню **Сборка** выберите **Собрать решение**.  
  
     Убедитесь, что сборка решения выполняется без ошибок.  
  
## Тестирование надстройки VSTO  
 Класс `AddInUtilities` можно вызывать из решений Office различного типа. В этом пошаговом руководстве будет использоваться код VBA в книге Excel. Дополнительные сведения о других типах решений Office, которые также можно использовать, см. в разделе [Вызов кода в надстройках VSTO из других решений Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md).  
  
#### Для тестирования надстройки VSTO выполните следующие действия.  
  
1.  Нажмите клавишу F5 для запуска проекта.  
  
2.  В Excel сохраните активную книгу как книгу Excel с поддержкой макросов \(\*.xlsm\). Сохраните ее в удобном месте, например на рабочем столе.  
  
3.  На ленте перейдите на вкладку **Разработчик**.  
  
    > [!NOTE]  
    >  Если вкладка **Разработчик** не отображается, сделайте ее видимой. Для получения дополнительной информации см. [Практическое руководство. Отображение вкладки разработчика на ленте](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
4.  В группе **Код** щелкните **Visual Basic**.  
  
     Открывается редактор Visual Basic.  
  
5.  В окне **Проект** дважды щелкните **ThisWorkbook**.  
  
     Открывается файл кода для объекта `ThisWorkbook`.  
  
6.  Добавьте следующий код VBA в файл кода. Этот код сначала получает объект COMAddIn, представляющий надстройку VSTO **ExcelImportData**. Затем код использует свойство Object объекта COMAddIn для вызова метода `ImportData`.  
  
    ```  
    Sub CallVSTOMethod() Dim addIn As COMAddIn Dim automationObject As Object Set addIn = Application.COMAddIns("ExcelImportData") Set automationObject = addIn.Object automationObject.ImportData End Sub  
    ```  
  
7.  Нажмите клавишу F5.  
  
8.  Убедитесь, что новый лист **Imported Data** \(Импортированные данные\) добавлен в книгу. Также убедитесь, что ячейка A1 содержит строку **This is my data** \(Это мои данные\).  
  
9. Выйдите из Excel.  
  
## Следующие действия  
 Дополнительные сведения о программировании надстроек VSTO см. в следующих статьях:  
  
-   Для автоматизации ведущего приложения и выполнения других задач в проектах надстроек VSTO используйте класс `ThisAddIn`. Для получения дополнительной информации см. [Приступая к программированию надстроек VSTO](../vsto/programming-vsto-add-ins.md).  
  
-   Создание настраиваемой области задач в надстройке VSTO. Дополнительные сведения см. в разделах [Настраиваемые области задач](../vsto/custom-task-panes.md) и [Практическое руководство. Добавление настраиваемой панели задач в приложение](../vsto/how-to-add-a-custom-task-pane-to-an-application.md).  
  
-   Настройка ленты в надстройке VSTO. Дополнительные сведения см. в разделах [Обзор ленты](../vsto/ribbon-overview.md) и [Практическое руководство. Работа с настройкой ленты](../vsto/how-to-get-started-customizing-the-ribbon.md).  
  
## См. также  
 [Приступая к программированию надстроек VSTO](../vsto/programming-vsto-add-ins.md)   
 [Вызов кода в надстройках VSTO из других решений Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)   
 [Разработка решений Office](../vsto/developing-office-solutions.md)   
 [Практическое руководство. Создание проектов Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Архитектура надстроек VSTO](../vsto/architecture-of-vsto-add-ins.md)   
 [Настройка функций пользовательского интерфейса с помощью интерфейсов расширяемости](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md)  
  
  