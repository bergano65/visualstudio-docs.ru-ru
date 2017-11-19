---
title: "Пошаговое руководство: Вызов кода из VBA в проекте Visual Basic | Документы Microsoft"
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
- documents [Office development in Visual Studio], Visual Basic for Applications and
- ThisDocument class
- Word [Office development in Visual Studio], calling code from VBA
- Visual Basic [Office development in Visual Studio], calling code from VBA
- VBA [Office development in Visual Studio], calling code in document-level customizations
- Office documents [Office development in Visual Studio, Visual Basic for Applications and
- calling code from VBA
- document-level customizations [Office development in Visual Studio], calling code
ms.assetid: 798bc2fa-449e-4d1a-86b4-18e57b02a4a8
caps.latest.revision: "45"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: bd1dfd2f1b1565a861b91730483cecde26fa9f08
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-calling-code-from-vba-in-a-visual-basic-project"></a>Пошаговое руководство. Вызов кода из VBA в проекте Visual Basic
  В этом пошаговом руководстве показано, как вызвать метод в настройке на уровне документа для Microsoft Office Word из кода Visual Basic для приложений (VBA) в документе. Данная процедура состоит из трех основных этапов: добавление метода в класс ведущего элемента `ThisDocument` , представление метода коду VBA и вызов метода из кода VBA в документе.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Хотя в этом пошаговом руководстве используется Word, рассмотренная процедура также применима к проектам на уровне документа для Excel.  
  
 В данном пошаговом руководстве рассмотрены следующие задачи:  
  
-   создание документа, содержащего код VBA;  
  
-   предоставление доверия расположению документа с помощью центра управления безопасностью в Word;  
  
-   добавление метода в класс ведущего элемента `ThisDocument` ;  
  
-   представление метода коду VBA;  
  
-   Вызов метода из кода VBA  
  
> [!NOTE]  
>  Отображаемые на компьютере имена или расположения некоторых элементов пользовательского интерфейса Visual Studio могут отличаться от указанных в следующих инструкциях. Это зависит от имеющегося выпуска Visual Studio и используемых параметров. Дополнительные сведения см. в разделе [Персонализация интегрированной среды разработки Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Предварительные требования  
 Ниже приведены компоненты, необходимые для выполнения данного пошагового руководства.  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Word  
  
## <a name="creating-a-document-that-contains-vba-code"></a>Создание документа, содержащего код VBA  
 Первым шагом является создание документа с поддержкой макросов, который содержит простой макрос VBA. При создании проекта Visual Studio, основанном на этом документе, он должен содержать проект VBA. В противном случае Visual Studio не сможет изменить проект VBA так, чтобы код VBA мог вызывать сборку настройки.  
  
 Если у вас уже есть документ, содержащий код VBA, который необходимо использовать, данный шаг можно пропустить.  
  
#### <a name="to-create-a-document-that-contains-vba-code"></a>Создание документа, содержащего код VBA  
  
1.  Запустите приложение Word.  
  
2.  Сохранить активный документ как слово **документ с поддержкой макросов (\*.docm)** с именем **DocumentWithVBA**. Сохраните его в удобном месте, например, на рабочем столе.  
  
3.  На ленте перейдите на вкладку **Разработчик** .  
  
    > [!NOTE]  
    >  Если вкладка **Разработчик** не отображается, сделайте ее видимой. Для получения дополнительной информации см. [How to: Show the Developer Tab on the Ribbon](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
4.  В группе **Код** щелкните **Visual Basic**.  
  
     Открывается редактор Visual Basic.  
  
5.  В окне **Проект** дважды щелкните **ThisDocument**.  
  
     Открывается файл кода для объекта `ThisDocument` .  
  
6.  Добавьте следующий код VBA в файл кода. Этот код определяет простую функцию, которая не выполняет никаких действий. Данная функция предназначена исключительно для проверки наличия проекта VBA в документе. Это необходимо для выполнения последующих действий в данном пошаговом руководстве.  
  
    ```  
    Sub EmptySub()  
    End Sub  
    ```  
  
7.  Сохраните документ и выйдите из Word.  
  
## <a name="creating-the-project"></a>Создание проекта  
 Теперь можно создать проект на уровне документа для Word, который использует созданный ранее документ с поддержкой макросов.  
  
#### <a name="to-create-a-new-project"></a>Создание нового проекта  
  
1.  Запустите [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  В меню **Файл** выберите пункт **Создать**, а затем команду **Проект**. Если интерфейс IDE настроен на использование параметров разработки Visual Basic, последовательно выберите в меню **Файл** пункт **Создать проект**.  
  
3.  В области шаблонов разверните узел **Visual Basic**, а затем узел **Office/SharePoint**.  
  
4.  Выберите узел **Надстройки Office** .  
  
5.  В списке шаблонов проектов выберите проект **Документ Word 2010** или **Документ Word 2013** .  
  
6.  В поле **Имя** введите **CallingCodeFromVBA**.  
  
7.  Нажмите кнопку **ОК**.  
  
     Откроется **Мастер проектов набора средств Visual Studio для Office** .  
  
8.  Выберите **Скопировать существующий документ**и в поле **Полный путь к существующему документу** укажите расположение документа **DocumentWithVBA** , созданного ранее. Если вы используете собственный документ с поддержкой макросов, укажите его расположение.  
  
9. Нажмите кнопку **Готово**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] открывает документ **DocumentWithVBA** в конструкторе и добавляет проект **CallingCodeFromVBA** в **обозреватель решений**.  
  
## <a name="trusting-the-location-of-the-document"></a>Предоставление доверия расположению документа  
 Перед предоставлением кода в своем решении коду VBA в документе необходимо предоставить доверие VBA на выполнение в документе. Для этого можно использовать следующие способы. В целях этого пошагового руководства предоставьте доверие расположению документа в **Центре управления безопасностью** в Word.  
  
#### <a name="to-trust-the-location-of-the-document"></a>Предоставление доверия расположению документа  
  
1.  Запустите приложение Word.  
  
2.  Перейдите на вкладку **Файл** .  
  
3.  Нажмите кнопку **Параметры Word** .  
  
4.  В области категорий нажмите **Центр управления безопасностью**.  
  
5.  В области сведений нажмите **Параметры центра управления безопасностью**.  
  
6.  В области категорий нажмите **Надежные расположения**.  
  
7.  В области сведений нажмите **Добавить новое расположение**.  
  
8.  В диалоговом окне **Надежное расположение Microsoft Office** перейдите в папку, содержащую проект **CallingCodeFromVBA** .  
  
9. Установите флажок **Также доверять всем вложенным папкам**.  
  
10. В диалоговом окне **Надежное расположение Microsoft Office** нажмите кнопку **ОК**.  
  
11. В диалоговом окне **Центр управления безопасностью** нажмите кнопку **ОК**.  
  
12. В диалоговом окне **Параметры Word** нажмите кнопку **ОК**.  
  
13. Закройте программу Word.  
  
## <a name="adding-a-method-to-the-thisdocument-class"></a>Добавление метода в класс ThisDocument  
 Теперь, когда проект VBA настроен, добавьте метод в класс ведущего элемента `ThisDocument` , который можно вызвать из кода VBA.  
  
#### <a name="to-add-a-method-to-the-thisdocument-class"></a>Добавление метода в класс ThisDocument  
  
1.  В **обозревателе решений**щелкните правой кнопкой мыши **ThisDocument.vb**и выберите пункт **Просмотреть код**.  
  
     В редакторе кода открывается файл **ThisDocument.vb** .  
  
2.  Добавьте следующий метод в класс `ThisDocument` . Этот метод создает таблицу с двумя строками и столбцами в начале документа. Параметры указывают текст, который отображается в первой строке. Далее в этом пошаговом руководстве данный метод будет вызываться из кода VBA в документе.  
  
     [!code-vb[Trin_CallingVBCustomizationFromVBA#1](../vsto/codesnippet/VisualBasic/CallingCodeFromVBA/ThisDocument.vb#1)]  
  
3.  Выполните построение проекта.  
  
## <a name="exposing-the-method-to-vba-code"></a>Представление метода коду VBA  
 Для предоставления метода `CreateTable` коду VBA в документе установите для свойства **EnableVbaCallers** ведущего элемента `ThisDocument` значение **True**.  
  
#### <a name="to-expose-the-method-to-vba-code"></a>Представление метода коду VBA  
  
1.  В **обозревателе решений**дважды щелкните файл **ThisDocument.vb**.  
  
     Файл **DocumentWithVBA** откроется в конструкторе.  
  
2.  В окне **Свойства** выберите свойство **EnableVbaCallers** и установите значение **True**.  
  
3.  Появляется сообщение, в котором следует нажать кнопку **ОК** .  
  
4.  Выполните построение проекта.  
  
## <a name="calling-the-method-from-vba-code"></a>Вызов метода из кода VBA  
 Теперь можно вызвать метод `CreateTable` из кода VBA в документе.  
  
> [!NOTE]  
>  В этом пошаговом руководстве будет добавлен код VBA в документ во время отладки проекта. Код VBA, добавляемый в этот документ, будет перезаписан в следующий раз при построении проекта, так как Visual Studio заменяет документ в выходной папке сборки копией документа из главной папки проекта. Если код VBA необходимо сохранить, его можно скопировать в документ в папке проекта. Для получения дополнительной информации см. [Combining VBA and Document-Level Customizations](../vsto/combining-vba-and-document-level-customizations.md).  
  
#### <a name="to-call-the-method-from-vba-code"></a>Вызов метода из кода VBA  
  
1.  Нажмите клавишу F5 для запуска проекта.  
  
2.  На вкладке **Разработчик** в группе **Код** щелкните элемент **Visual Basic**.  
  
     Открывается редактор Visual Basic.  
  
3.  В меню **Вставить** выберите пункт **Модуль**.  
  
4.  Добавьте в новый модуль следующий код:  
  
     Этот код вызывает метод `CreateTable` в сборке настройки. Макрос обращается к этому методу с помощью свойства `CallVSTOAssembly` объекта `ThisDocument` . Это свойство было автоматически создано ранее при установке значения для свойства **EnableVbaCallers** в этом пошаговом руководстве.  
  
    ```  
    Sub CreateTable()  
        Call ThisDocument.CallVSTOAssembly.CreateTable("Employee Name", "Start Date")  
    End Sub  
    ```  
  
5.  Нажмите клавишу F5.  
  
6.  Убедитесь, что новая таблица была добавлена в документ.  
  
7.  Выйдите из Word без сохранения изменений.  
  
## <a name="next-steps"></a>Дальнейшие действия  
 Дополнительные сведения о вызове кода в решениях Office из VBA см. в следующих разделах:  
  
-   Вызов кода в настройке Visual Basic из VBA. Этот процесс отличается от процесса Visual Basic. Дополнительные сведения см. в разделе [Пошаговое руководство: вызов кода из VBA в Visual C &#35; Проект](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md).  
  
-   Вызов кода в надстройке VSTO из VBA. Дополнительные сведения см. в разделе [Пошаговое руководство: вызов кода в надстройке VSTO из VBA](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md).  
  
## <a name="see-also"></a>См. также  
 [Combining VBA and Document-Level Customizations](../vsto/combining-vba-and-document-level-customizations.md)   
 [Программирование настроек на уровне документа](../vsto/programming-document-level-customizations.md)   
 [How to: Expose Code to VBA in a Visual Basic Project](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md)   
 [Как: предоставлять к коду VBA в Visual C &#35; Проект](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md)   
 [Пошаговое руководство: Вызов кода из VBA в Visual C &#35; Проект](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md)  
  
  