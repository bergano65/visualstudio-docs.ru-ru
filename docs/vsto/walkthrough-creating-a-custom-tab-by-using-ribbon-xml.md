---
title: "Пошаговое руководство: Создание настраиваемой вкладки с помощью XML-ленты | Документы Microsoft"
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
- Ribbon [Office development in Visual Studio], tabs
- customizing the Ribbon, tabscustom Ribbon, tabs
- Ribbon [Office development in Visual Studio], XML
- XML [Office development in Visual Studio], Ribbon
- Ribbon [Office development in Visual Studio], customizing
- Custom tab [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 1b736ace651854b3b6a527685e150f6f1ec7194c
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/10/2018
---
# <a name="walkthrough-creating-a-custom-tab-by-using-ribbon-xml"></a>Walkthrough: Creating a Custom Tab by Using Ribbon XML
  В этом пошаговом руководстве показано, как создать настраиваемую вкладку ленты с помощью **Лента (XML)** элемента.  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
 В данном пошаговом руководстве рассмотрены следующие задачи:  
  
-   Добавление кнопок на **надстройки** вкладки. **Надстройки** вкладка по умолчанию, определенные в XML-файле ленты.  
  
-   Автоматизация Microsoft Office Word с помощью кнопок на **надстройки** вкладки.  
  
> [!NOTE]  
>  Отображаемые на компьютере имена или расположения некоторых элементов пользовательского интерфейса Visual Studio могут отличаться от указанных в следующих инструкциях. Это зависит от имеющегося выпуска Visual Studio и используемых параметров. Дополнительные сведения см. в разделе [Персонализация интегрированной среды разработки Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Предварительные требования  
 Ниже приведены компоненты, необходимые для выполнения данного пошагового руководства.  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Word.  
  
## <a name="creating-the-project"></a>Создание проекта  
 Первым шагом является создание проекта надстройки Word VSTO. После этого следует настроить **надстройки** этого документа.  
  
#### <a name="to-create-a-new-project"></a>Создание нового проекта  
  
1.  Создание **надстройки Word** проект с именем **MyRibbonAddIn**.  
  
     Дополнительные сведения см. в разделе [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Открывает **ThisAddIn.cs** или **ThisAddIn.vb** файл кода и добавляет **MyRibbonAddIn** проекта **обозревателе решений**.  
  
## <a name="creating-the-vsto-add-ins-tab"></a>Создание вкладки надстройки VSTO  
 Для создания **надстройки** добавьте **Лента (XML)** в проект. Далее в этом пошаговом руководстве мы добавим некоторые кнопки на эту вкладку.  
  
#### <a name="to-create-the-add-ins-tab"></a>Создание вкладки «Надстройки»  
  
1.  В меню **Проект** выберите пункт **Добавить новый элемент**.  
  
2.  В **Добавление нового элемента** выберите **Лента (XML)**.  
  
3.  Измените имя новой ленты на **MyRibbon**и нажмите кнопку **Добавить**.  
  
     **MyRibbon.cs** или **MyRibbon.vb** файл откроется в конструкторе. XML-файл с именем **MyRibbon.xml** также добавляется в проект.  
  
4.  В **обозревателе решений**, щелкните правой кнопкой мыши **ThisAddin.cs** или **ThisAddin.vb**, а затем нажмите кнопку **Просмотр кода**.  
  
5.  Добавьте следующий код в класс **ThisAddin** . Этот код переопределяет метод CreateRibbonExtensibilityObject и возвращает класс XML ленты в приложение Office.  
  
     [!code-csharp[Trin_Ribbon_Custom_Tab_XML#1](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.cs#1)]
     [!code-vb[Trin_Ribbon_Custom_Tab_XML#1](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.vb#1)]  
  
6.  В **обозревателе решений**, щелкните правой кнопкой мыши **MyRibbonAddIn** проект и выберите пункт **сборки**. Убедитесь, что сборка проекта выполняется без ошибок.  
  
## <a name="adding-buttons-to-the-add-ins-tab"></a>Добавление кнопок на вкладку «Надстройки»  
 Данная надстройка VSTO предназначена для того, чтобы пользователи могли добавлять стандартный текст и конкретную таблицу в активный документ. Для предоставления пользовательского интерфейса, добавьте две кнопки для **надстройки** путем внесения изменений в XML-файле ленты. Далее в этом пошаговом руководстве мы определим методы обратного вызова для кнопок. Дополнительные сведения о XML-файле ленты см. в разделе [XML-ленты](../vsto/ribbon-xml.md).  
  
#### <a name="to-add-buttons-to-the-add-ins-tab"></a>Добавление кнопок на вкладку «Надстройки»  
  
1.  В **обозревателе решений**, щелкните правой кнопкой мыши **MyRibbon.xml** и нажмите кнопку **откройте**.  
  
2.  Замените содержимое **вкладке** элемент следующий XML-код. Этот XML-код изменяет метку группы элементов управления по умолчанию для **содержимого**, а также добавляет две новые кнопки с метками **вставить текст** и **вставить таблицу**.  
  
    ```  
    <tab idMso="TabAddIns">  
        <group id="ContentGroup" label="Content">  
            <button id="textButton" label="Insert Text"  
                 screentip="Text" onAction="OnTextButton"  
                 supertip="Inserts text at the cursor location."/>  
            <button id="tableButton" label="Insert Table"  
                 screentip="Table" onAction="OnTableButton"  
                 supertip="Inserts a table at the cursor location."/>  
        </group>  
    </tab>  
    ```  
  
## <a name="automating-the-document-by-using-the-buttons"></a>Автоматизация документа с помощью кнопок  
 Необходимо добавить `onAction` методов обратного вызова для **вставить текст** и **вставить таблицу** кнопки для выполнения действий, когда пользователь щелкает их. Дополнительные сведения о методах обратного вызова для элементов управления ленты см. в разделе [XML-ленты](../vsto/ribbon-xml.md).  
  
#### <a name="to-add-callback-methods-for-the-buttons"></a>Добавление методов обратного вызова для кнопок  
  
1.  В **обозревателе решений**, щелкните правой кнопкой мыши **MyRibbon.cs** или **MyRibbon.vb**, а затем нажмите кнопку **откройте**.  
  
2.  Добавьте следующий код в начало **MyRibbon.cs** или **MyRibbon.vb** файла. Этот код создает псевдоним для пространства имен <xref:Microsoft.Office.Interop.Word>.  
  
     [!code-csharp[Trin_RibbonButtons#1](../vsto/codesnippet/CSharp/Trin_RibbonButtons/MyRibbon.cs#1)]
     [!code-vb[Trin_RibbonButtons#1](../vsto/codesnippet/VisualBasic/Trin_RibbonButtons/MyRibbon.vb#1)]  
  
3.  Добавьте следующий метод в класс `MyRibbon`. Это метод обратного вызова для **вставить текст** кнопки, которая добавляет строку в активный документ в текущем положении курсора.  
  
     [!code-csharp[Trin_Ribbon_Custom_Tab_XML#2](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/MyRibbon.cs#2)]
     [!code-vb[Trin_Ribbon_Custom_Tab_XML#2](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/MyRibbon.vb#2)]  
  
4.  Добавьте следующий метод в класс `MyRibbon`. Это метод обратного вызова для **вставить таблицу** кнопки, которая добавляет таблицу в активный документ в текущем положении курсора.  
  
     [!code-csharp[Trin_Ribbon_Custom_Tab_XML#3](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/MyRibbon.cs#3)]
     [!code-vb[Trin_Ribbon_Custom_Tab_XML#3](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/MyRibbon.vb#3)]  
  
## <a name="testing-the-vsto-add-in"></a>Тестирование надстройки VSTO  
 При запуске проекта открывается Word и вкладка с именем **надстройки** отображается на ленте. Нажмите кнопку **вставить текст** и **вставить таблицу** кнопок, расположенных на **надстройки** для тестирования кода.  
  
#### <a name="to-test-your-vsto-add-in"></a>Для тестирования надстройки VSTO выполните следующие действия.  
  
1.  Нажмите клавишу F5 для запуска проекта.  
  
2.  Убедитесь, что **надстройки** вкладка отображается на ленте.  
  
3.  Перейдите на вкладку **Надстройки** .  
  
4.  Убедитесь, что **содержимого** группы отображается на ленте.  
  
5.  Нажмите кнопку **вставить текст** кнопку в **содержимого** группы.  
  
     Строка добавляется в документ в текущем положении курсора.  
  
6.  Нажмите кнопку **вставить таблицу** кнопку в **содержимого** группы.  
  
     Таблица добавляется в документ в текущем положении курсора.  
  
## <a name="next-steps"></a>Следующие шаги  
 Дополнительные сведения о настройке пользовательского интерфейса Office см. в следующих разделах:  
  
-   Настройка ленты другого приложения Office. Дополнительные сведения о приложениях, поддерживающих настройку ленты см. в разделе [Обзор ленты](../vsto/ribbon-overview.md).  
  
-   Настройка ленты приложения Office с помощью конструктора лент. Для получения дополнительной информации см. [Ribbon Designer](../vsto/ribbon-designer.md).  
  
-   Создание настраиваемой панели действий. Дополнительные сведения см. в разделе [Actions Pane Overview](../vsto/actions-pane-overview.md).  
  
-   Настройка пользовательского интерфейса для Microsoft Office Outlook с помощью областей формы Outlook. Дополнительные сведения см. в разделе [Пошаговое руководство: разработка области формы Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md).  
  
## <a name="see-also"></a>См. также  
 [Обзор ленты](../vsto/ribbon-overview.md)   
 [XML-ленты](../vsto/ribbon-xml.md)   
 [Пошаговое руководство. Создание настраиваемой вкладки с помощью конструктора лент](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)  
  
  