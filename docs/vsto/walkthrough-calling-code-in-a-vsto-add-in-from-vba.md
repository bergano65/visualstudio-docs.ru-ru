---
title: 'Пошаговое руководство: Вызов кода в надстройке VSTO из VBA'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- VBA [Office development in Visual Studio], calling code in application-level add-ins
- application-level add-ins [Office development in Visual Studio], calling code from other solutions
- Video How tos, Office development in Visual Studio
- calling add-in code
- add-ins [Office development in Visual Studio], calling code from other solutions
- interoperability [Office development in Visual Studio]
- calling code from VBA
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9e46cf9032cae7d6400822be7d72394a7845314f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49843825"
---
# <a name="walkthrough-call-code-in-a-vsto-add-in-from-vba"></a>Пошаговое руководство: Вызов кода в надстройке VSTO из VBA
  В этом пошаговом руководстве показано, как предоставить объект в надстройке VSTO другим решениям Microsoft Office, включая Visual Basic для приложений (VBA) и надстроек VSTO COM.  
  
 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]  
  
 Хотя в этом пошаговом руководстве используется Excel, рассмотренная процедура применима к любому шаблону проекта надстройки VSTO, которые предоставляет Visual Studio.  
  
 В данном пошаговом руководстве рассмотрены следующие задачи:  
  
- Определение класса, который может быть предоставлен другим решениям Office.  
  
- Предоставление класса другим решениям Office.  
  
- Вызов метода класса из кода VBA.  
  
  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Предварительные требования  
 Ниже приведены компоненты, необходимые для выполнения данного пошагового руководства.  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Excel  
  
## <a name="create-the-vsto-add-in-project"></a>Создайте проект надстройки VSTO  
 Первым шагом является создание проекта надстройки VSTO для Excel.  
  
### <a name="to-create-a-new-project"></a>Создание нового проекта  
  
1.  Создайте проект надстройки VSTO для Excel с именем **ExcelImportData**с помощью шаблона проекта надстройки VSTO для Excel. Дополнительные сведения см. в разделе [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] открывает файл кода **ThisAddIn.cs** или **ThisAddIn.vb** и добавляет проект **ExcelImportData** в **обозреватель решений**.  
  
## <a name="define-a-class-that-you-can-expose-to-other-office-solutions"></a>Определите класс, который можно предоставить другим решениям Office  
 В этом пошаговом руководстве описывается вызов метода `ImportData` класса с именем `AddInUtilities` в надстройке VSTO из кода VBA. Этот метод записывает строку в ячейку A1 активного листа.  
  
 Для предоставления класса `AddInUtilities` другим решениям Office необходимо сделать класс общедоступным и видимым для COM. Необходимо также предоставить интерфейс [IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) в классе. Код в следующей процедуре демонстрирует один из способов выполнения этих требований. Для получения дополнительной информации см. [Calling Code in VSTO Add-ins from Other Office Solutions](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md).  
  
### <a name="to-define-a-class-that-you-can-expose-to-other-office-solutions"></a>Определение класса, который можно предоставить другим решениям Office  
  
1.  В меню **Проект** выберите пункт **Добавить класс**.  
  
2.  В диалоговом окне **Добавить новый элемент** измените имя нового класса на **AddInUtilities**и нажмите кнопку **Добавить**.  
  
     В редакторе кода откроется файл **AddInUtilities.cs** или **AddInUtilities.vb** .  
  
3.  Добавьте следующие инструкции в начало файла.  
  
     [!code-csharp[Trin_AddInInteropWalkthrough#2](../vsto/codesnippet/CSharp/Trin_AddInInteropWalkthrough/AddInUtilities.cs#2)]
     [!code-vb[Trin_AddInInteropWalkthrough#2](../vsto/codesnippet/VisualBasic/Trin_AddInInteropWalkthrough/AddInUtilities.vb#2)]  
  
4.  Замените класс `AddInUtilities` на следующий код.  
  
     [!code-csharp[Trin_AddInInteropWalkthrough#3](../vsto/codesnippet/CSharp/Trin_AddInInteropWalkthrough/AddInUtilities.cs#3)]
     [!code-vb[Trin_AddInInteropWalkthrough#3](../vsto/codesnippet/VisualBasic/Trin_AddInInteropWalkthrough/AddInUtilities.vb#3)]  
  
     Этот код делает класс `AddInUtilities` видимым для COM, а также добавляет метод `ImportData` в класс. Для предоставления интерфейса [IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) класс `AddInUtilities` также содержит атрибут <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> , который реализует интерфейс, видимый для COM.  
  
## <a name="expose-the-class-to-other-office-solutions"></a>Предоставление класса другим решениям Office  
 Для предоставления класса `AddInUtilities` другим решениям Office переопределите метод <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> в классе `ThisAddIn` . В переопределении верните экземпляр класса `AddInUtilities` .  
  
### <a name="to-expose-the-addinutilities-class-to-other-office-solutions"></a>Предоставление класса AddInUtilities другим решениям Office  
  
1.  В **обозревателе решений**разверните **Excel**.  
  
2.  Щелкните правой кнопкой мыши **ThisAddIn.cs** или **ThisAddIn.vb**, а затем выберите пункт **Просмотреть код**.  
  
3.  Добавьте следующий код в класс `ThisAddIn` .  
  
     [!code-csharp[Trin_AddInInteropWalkthrough#1](../vsto/codesnippet/CSharp/Trin_AddInInteropWalkthrough/ThisAddIn.cs#1)]
     [!code-vb[Trin_AddInInteropWalkthrough#1](../vsto/codesnippet/VisualBasic/Trin_AddInInteropWalkthrough/ThisAddIn.vb#1)]  
  
4.  В меню **Сборка** выберите **Собрать решение**.  
  
     Убедитесь, что сборка решения выполняется без ошибок.  
  
## <a name="test-the-vsto-add-in"></a>Тестирование надстройки VSTO  
 Класс `AddInUtilities` можно вызывать из решений Office различного типа. В этом пошаговом руководстве будет использоваться код VBA в книге Excel. Дополнительные сведения о других типах решений Office, можно также использовать, см. в разделе [вызов кода в надстройках VSTO из других решений Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md).  
  
### <a name="to-test-your-vsto-add-in"></a>Для тестирования надстройки VSTO выполните следующие действия.  
  
1.  Нажмите клавишу **F5** для запуска проекта.  
  
2.  В Excel сохраните активную книгу как книгу Excel с поддержкой макросов (*.xlsm). Сохраните ее в удобном месте, например на рабочем столе.  
  
3.  На ленте перейдите на вкладку **Разработчик** .  
  
    > [!NOTE]  
    >  Если вкладка **Разработчик** не отображается, сделайте ее видимой. Дополнительные сведения см. в разделе [как: Отображение вкладки разработчика на ленте](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
4.  В группе **Код** щелкните **Visual Basic**.  
  
     Открывается редактор Visual Basic.  
  
5.  В окне **Проект** дважды щелкните **ThisWorkbook**.  
  
     Открывается файл кода для объекта `ThisWorkbook` .  
  
6.  Добавьте следующий код VBA в файл кода. Этот код сначала получает объект COMAddIn, который представляет **ExcelImportData** надстройки VSTO. Затем код использует свойство объекта COMAddIn объекта для вызова `ImportData` метод.  
  
    ```vb  
    Sub CallVSTOMethod()  
        Dim addIn As COMAddIn  
        Dim automationObject As Object  
        Set addIn = Application.COMAddIns("ExcelImportData")  
        Set automationObject = addIn.Object  
        automationObject.ImportData  
    End Sub  
    ```  
  
7.  Нажмите клавишу **F5**.  
  
8.  Убедитесь, что новый лист **Imported Data** (Импортированные данные) добавлен в книгу. Также убедитесь, что ячейка A1 содержит строку **This is my data**(Это мои данные).  
  
9. Выйдите из Excel.  
  
## <a name="next-steps"></a>Следующие шаги  
 Дополнительные сведения о программировании надстроек VSTO см. в следующих статьях:  
  
-   Для автоматизации ведущего приложения и выполнения других задач в проектах надстроек VSTO используйте класс `ThisAddIn` . Дополнительные сведения см. в разделе [программы VSTO Add-ins](../vsto/programming-vsto-add-ins.md).  
  
-   Создание настраиваемой области задач в надстройке VSTO. Дополнительные сведения см. в разделе [настраиваемых панелей задач](../vsto/custom-task-panes.md) и [как: добавление настраиваемой области задач в приложение](../vsto/how-to-add-a-custom-task-pane-to-an-application.md).  
  
-   Настройка ленты в надстройке VSTO. Дополнительные сведения см. в разделе [Обзор ленты](../vsto/ribbon-overview.md) и [как: Приступая к настройке ленты](../vsto/how-to-get-started-customizing-the-ribbon.md).  
  
## <a name="see-also"></a>См. также  
 [Программирование надстроек VSTO](../vsto/programming-vsto-add-ins.md)   
 [Вызов кода в надстройках VSTO из других решений Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)   
 [Разработка решений Office](../vsto/developing-office-solutions.md)   
 [Практическое: Создание проектов Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md)   
 [Настройка возможностей пользовательского интерфейса с помощью интерфейсов расширяемости](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md)  
  
  