---
title: "Пошаговое руководство: Вызов кода из VBA в проекте Visual C# | Документы Microsoft"
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
helpviewer_keywords:
- Excel [Office development in Visual Studio], calling code from VBA
- Word [Office development in Visual Studio], calling code from VBA
- Visual C# [Office development in Visual Studio], calling code from VBA
- workbooks [Office development in Visual Studio], calling code from VBA
- VBA [Office development in Visual Studio], calling code in document-level customizations
- Office documents [Office development in Visual Studio, Visual Basic for Applications and
- calling code from VBA
- document-level customizations [Office development in Visual Studio], calling code
ms.assetid: 9a5741f1-8260-4964-afa1-c69b68d1cfdf
caps.latest.revision: "38"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: a1e61b3b2055e6a32fa1e179232e7366fe2b3d16
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-calling-code-from-vba-in-a-visual-c-project"></a>Пошаговое руководство. Вызов кода из VBA в проекте Visual C#
  В этом пошаговом руководстве показано, как вызвать метод в настройке на уровне документа для Microsoft Office Excel из кода Visual Basic для приложений (VBA) в книге. Данная процедура состоит из трех основных этапов: добавление метода в класс ведущего элемента `Sheet1` , представление метода коду VBA в книге и вызов метода из кода VBA в книге.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Хотя в этом пошаговом руководстве используется Excel, рассмотренная процедура также применима к проектам на уровне документа для Word.  
  
 В данном пошаговом руководстве рассмотрены следующие задачи:  
  
-   Создание книги, содержащей код VBA  
  
-   Предоставление доверия расположению книги с помощью центра управления безопасностью в Excel  
  
-   Добавление метода в класс ведущего элемента `Sheet1`  
  
-   Извлечение интерфейса для класса ведущего элемента `Sheet1`  
  
-   Представление метода коду VBA  
  
-   Вызов метода из кода VBA  
  
> [!NOTE]  
>  Отображаемые на компьютере имена или расположения некоторых элементов пользовательского интерфейса Visual Studio могут отличаться от указанных в следующих инструкциях. Это зависит от имеющегося выпуска Visual Studio и используемых параметров. Дополнительные сведения см. в разделе [Персонализация интегрированной среды разработки Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Предварительные требования  
 Ниже приведены компоненты, необходимые для выполнения данного пошагового руководства.  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Excel  
  
## <a name="creating-a-workbook-that-contains-vba-code"></a>Создание книги, содержащей код VBA  
 Первым шагом является создание книги с поддержкой макросов, которая содержит простой макрос VBA. Прежде чем код в настройке можно будет предоставить VBA, книга уже должна содержать код VBA. В противном случае Visual Studio не сможет изменить проект VBA так, чтобы код VBA мог вызывать сборку настройки.  
  
 Если у вас уже есть книга, содержащая код VBA, который необходимо использовать, данный шаг можно пропустить.  
  
#### <a name="to-create-a-workbook-that-contains-vba-code"></a>Создание книги, содержащей код VBA  
  
1.  Запустите Excel.  
  
2.  Сохранить активный документ как **книга Excel с поддержкой макросов (\*.xlsm)** с именем **WorkbookWithVBA**. Сохраните его в удобном месте, например на рабочем столе.  
  
3.  На ленте перейдите на вкладку **Разработчик** .  
  
    > [!NOTE]  
    >  Если вкладка **Разработчик** не отображается, сделайте ее видимой. Дополнительные сведения см. в разделе [How to: Show the Developer Tab on the Ribbon](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
4.  В группе **Код** щелкните **Visual Basic**.  
  
     Открывается редактор Visual Basic.  
  
5.  В окне **Проект** дважды щелкните **ThisWorkbook**.  
  
     Открывается файл кода для объекта `ThisWorkbook` .  
  
6.  Добавьте следующий код VBA в файл кода. Этот код определяет простую функцию, которая не выполняет никаких действий. Данная функция предназначена исключительно для проверки наличия проекта VBA в книге. Это необходимо для выполнения последующих действий в данном пошаговом руководстве.  
  
    ```  
    Sub EmptySub()  
    End Sub  
    ```  
  
7.  Сохраните документ и выйдите из Excel.  
  
## <a name="creating-the-project"></a>Создание проекта  
 Теперь можно создать проект на уровне документа для Excel, который использует созданную ранее книгу с поддержкой макросов.  
  
#### <a name="to-create-a-new-project"></a>Создание нового проекта  
  
1.  Запустите [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  В меню **Файл** выберите пункт **Создать**, а затем команду **Проект**.  
  
3.  В области шаблонов разверните узел **Visual C#**, а затем узел **Office/SharePoint**.  
  
4.  Выберите узел **Надстройки Office** .  
  
5.  В списке шаблонов проектов выберите проект **Книга Excel 2010** или **Книга Excel 2013** .  
  
6.  В поле **Имя** введите **CallingCodeFromVBA**.  
  
7.  Нажмите кнопку **ОК**.  
  
     Откроется **Мастер проектов набора средств Visual Studio для Office** .  
  
8.  Выберите **Копировать существующий документ**и в поле **Полный путь к существующему документу** укажите расположение книги **WorkbookWithVBA** , которая была создана ранее. Если вы используете собственную книгу с поддержкой макросов, укажите расположение этой книги.  
  
9. Нажмите кнопку **Готово**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] открывает книгу **WorkbookWithVBA** в конструкторе и добавляет проект **CallingCodeFromVBA** в **обозреватель решений**.  
  
## <a name="trusting-the-location-of-the-workbook"></a>Предоставление доверия расположению книги  
 Перед предоставлением кода в своем решении коду VBA в книге необходимо предоставить доверие VBA на выполнение в книге. Для этого можно использовать следующие способы. В этом пошаговом руководстве данную задачу предстоит выполнить путем предоставления доверия расположению книги в **центре управления безопасностью** в Excel.  
  
#### <a name="to-trust-the-location-of-the-workbook"></a>Предоставление доверия расположению книги  
  
1.  Запустите Excel.  
  
2.  Перейдите на вкладку **Файл** .  
  
3.  Нажмите кнопку **Параметры Excel** .  
  
4.  В области категорий нажмите **Центр управления безопасностью**.  
  
5.  В области сведений нажмите **Параметры центра управления безопасностью**.  
  
6.  В области категорий нажмите **Надежные расположения**.  
  
7.  В области сведений нажмите **Добавить новое расположение**.  
  
8.  В диалоговом окне **Надежное расположение Microsoft Office** перейдите в папку, содержащую проект **CallingCodeFromVBA** .  
  
9. Установите флажок **Также доверять всем вложенным папкам**.  
  
10. В диалоговом окне **Надежное расположение Microsoft Office** нажмите кнопку **ОК**.  
  
11. В диалоговом окне **Центр управления безопасностью** нажмите кнопку **ОК**.  
  
12. В диалоговом окне **Параметры Excel** нажмите кнопку **ОК**.  
  
13. Выйдите из **Excel**.  
  
## <a name="adding-a-method-to-the-sheet1-class"></a>Добавление метода в класс Sheet1  
 Теперь, когда проект VBA настроен, добавьте открытый метод в класс ведущего элемента `Sheet1` , который можно вызвать из кода VBA.  
  
#### <a name="to-add-a-method-to-the-sheet1-class"></a>Порядок добавления метода в класс Sheet1  
  
1.  В **обозревателе решений**щелкните правой кнопкой мыши файл **Sheet1.cs**и выберите пункт **Просмотреть код**.  
  
     Файл **Sheet1.cs** открывается в редакторе кода.  
  
2.  Добавьте следующий код в класс `Sheet1` . Метод `CreateVstoNamedRange` создает новый объект <xref:Microsoft.Office.Tools.Excel.NamedRange> в указанном диапазоне. При этом также создается обработчик событий для события <xref:Microsoft.Office.Tools.Excel.NamedRange.Selected> в <xref:Microsoft.Office.Tools.Excel.NamedRange>. Далее в этом пошаговом руководстве будет вызван метод `CreateVstoNamedRange` из кода VBA в документе.  
  
     [!code-csharp[Trin_CallingCSCustomizationFromVBA#2](../vsto/codesnippet/CSharp/CallingCodeFromVBA/Sheet1.cs#2)]  
  
3.  Добавьте следующий метод в класс `Sheet1` . Этот метод переопределяет метод <xref:Microsoft.Office.Tools.Excel.Worksheet.GetAutomationObject%2A> для возврата текущего экземпляра класса `Sheet1` .  
  
     [!code-csharp[Trin_CallingCSCustomizationFromVBA#3](../vsto/codesnippet/CSharp/CallingCodeFromVBA/Sheet1.cs#3)]  
  
4.  Примените следующие атрибуты перед первой строкой объявления класса `Sheet1` . Эти атрибуты делают класс видимым для модели COM, но без создания интерфейса класса.  
  
     [!code-csharp[Trin_CallingCSCustomizationFromVBA#1](../vsto/codesnippet/CSharp/CallingCodeFromVBA/Sheet1.cs#1)]  
  
## <a name="extracting-an-interface-for-the-sheet1-class"></a>Извлечение интерфейса для класса Sheet1  
 Перед предоставлением метода `CreateVstoNamedRange` коду VBA необходимо создать открытый интерфейс, который определяет данный метод, а также предоставить этот интерфейс модели COM.  
  
#### <a name="to-extract-an-interface-for-the-sheet1-class"></a>Извлечение интерфейса для класса Sheet1  
  
1.  В файле кода **Sheet1.cs** щелкните в любом месте внутри класса `Sheet1` .  
  
2.  В меню **Рефакторинг** выберите пункт **Извлечь интерфейс**.  
  
3.  В диалоговом окне **Извлечение интерфейса** в поле **Выбрать открытые методы для создания интерфейса** выберите значение для метода `CreateVstoNamedRange` .  
  
4.  Нажмите кнопку **ОК**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] создает новый интерфейс с именем `ISheet1`и изменяет определение класса `Sheet1` , чтобы он реализовал интерфейс `ISheet1` . [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] также открывает файл **ISheet1.cs** в редакторе кода.  
  
5.  В файле **ISheet1.cs** замените объявление интерфейса `ISheet1` на следующий код. Этот код делает интерфейс `ISheet1` общедоступным и применяет атрибут <xref:System.Runtime.InteropServices.ComVisibleAttribute> , чтобы сделать интерфейс видимым для модели COM.  
  
     [!code-csharp[Trin_CallingCSCustomizationFromVBA#4](../vsto/codesnippet/CSharp/CallingCodeFromVBA/ISheet1.cs#4)]  
  
6.  Выполните построение проекта.  
  
## <a name="exposing-the-method-to-vba-code"></a>Представление метода коду VBA  
 Для предоставления метода `CreateVstoNamedRange` коду VBA в книге установите для свойства **ReferenceAssemblyFromVbaProject значения** для ведущего элемента `Sheet1` значение **True**.  
  
#### <a name="to-expose-the-method-to-vba-code"></a>Порядок представления метода коду VBA  
  
1.  В **обозревателе решений**дважды щелкните файл **Sheet1.cs**.  
  
     Файл **WorkbookWithVBA** открывается в конструкторе, и отображается Sheet1.  
  
2.  В окне **Свойства** выберите свойство **ReferenceAssemblyFromVbaProject** и установите значение **True**.  
  
3.  Появляется сообщение, в котором следует нажать кнопку **ОК** .  
  
4.  Выполните построение проекта.  
  
## <a name="calling-the-method-from-vba-code"></a>Вызов метода из кода VBA  
 Теперь можно вызвать метод `CreateVstoNamedRange` из кода VBA в книге.  
  
> [!NOTE]  
>  В этом пошаговом руководстве будет добавлен код VBA в книгу во время отладки проекта. Код VBA, добавляемый в этот документ, будет перезаписан в следующий раз при построении проекта, так как Visual Studio заменяет документ в выходной папке сборки копией документа из главной папки проекта. Если код VBA необходимо сохранить, его можно скопировать в документ в папке проекта. Для получения дополнительной информации см. [Combining VBA and Document-Level Customizations](../vsto/combining-vba-and-document-level-customizations.md).  
  
#### <a name="to-call-the-method-from-vba-code"></a>Вызов метода из кода VBA  
  
1.  Нажмите клавишу F5 для запуска проекта.  
  
2.  На вкладке **Разработчик** в группе **Код** щелкните элемент **Visual Basic**.  
  
     Открывается редактор Visual Basic.  
  
3.  В меню **Вставить** выберите пункт **Модуль**.  
  
4.  Добавьте в новый модуль следующий код:  
  
     Этот код вызывает метод `CreateTable` в сборке настройки. Макрос обращается к этому методу, используя глобальный метод `GetManagedClass` для доступа к классу ведущего элемента `Sheet1` , который был предоставлен коду VBA. Метод `GetManagedClass` был автоматически создан ранее при установке значения для свойства **ReferenceAssemblyFromVbaProject** в этом пошаговом руководстве.  
  
    ```  
    Sub CallVSTOMethod()  
        Dim VSTOSheet1 As CallingCodeFromVBA.Sheet1  
        Set VSTOSheet1 = GetManagedClass(Sheet1)  
        Call VSTOSheet1.CreateVstoNamedRange(Sheet1.Range("A1"), "VstoNamedRange")  
    End Sub  
    ```  
  
5.  Нажмите клавишу F5.  
  
6.  В открытой книге щелкните ячейку **A1** на листе **Sheet1**. Убедитесь, что появляется окно сообщения.  
  
7.  Выйдите из Excel без сохранения изменений.  
  
## <a name="next-steps"></a>Следующие шаги  
 Дополнительные сведения о вызове кода в решениях Office из VBA см. в следующих разделах:  
  
-   Вызов кода в ведущем элементе в настройке Visual Basic из VBA. Этот процесс отличается от процесса Visual C#. Дополнительные сведения см. в разделе [Пошаговое руководство: вызов кода из VBA в проекте Visual Basic](../vsto/walkthrough-calling-code-from-vba-in-a-visual-basic-project.md).  
  
-   Вызов кода в надстройке VSTO из VBA. Дополнительные сведения см. в разделе [Пошаговое руководство: вызов кода в надстройке VSTO из VBA](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md).  
  
## <a name="see-also"></a>См. также  
 [Combining VBA and Document-Level Customizations](../vsto/combining-vba-and-document-level-customizations.md)   
 [Программирование настроек на уровне документа](../vsto/programming-document-level-customizations.md)   
 [How to: Expose Code to VBA in a Visual Basic Project](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md)   
 [Как: предоставлять к коду VBA в Visual C &#35; Проект](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md)   
 [Пошаговое руководство. Вызов кода из VBA в проекте Visual Basic](../vsto/walkthrough-calling-code-from-vba-in-a-visual-basic-project.md)  
  