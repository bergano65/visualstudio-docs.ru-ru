---
title: Пошаговое руководство. Создание настраиваемой вкладки с помощью XML-ленты
ms.date: 02/02/2017
ms.topic: conceptual
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e05bd9173b83ec3303a058dcf61ea48a7ef7675c
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63438578"
---
# <a name="walkthrough-create-a-custom-tab-by-using-ribbon-xml"></a>Пошаговое руководство. Создание настраиваемой вкладки с помощью XML-ленты
  В этом пошаговом руководстве показано, как создать настраиваемую вкладку ленты с помощью **Лента (XML)** элемента.

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

 В данном пошаговом руководстве рассмотрены следующие задачи:

- Добавление кнопок на **Add-Ins** вкладки. **Add-Ins** вкладки — вкладка по умолчанию, которая определяется в XML-файле ленты.

- Автоматизация Microsoft Office Word с помощью кнопок на **Add-Ins** вкладки.

> [!NOTE]
> Отображаемые на компьютере имена или расположения некоторых элементов пользовательского интерфейса Visual Studio могут отличаться от указанных в следующих инструкциях. Это зависит от имеющегося выпуска Visual Studio и используемых параметров. Дополнительные сведения см. в разделе [Персонализация интегрированной среды разработки Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Предварительные требования
 Ниже приведены компоненты, необходимые для выполнения данного пошагового руководства.

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Word.

## <a name="create-the-project"></a>Создание проекта
 Первым шагом является создание проекта надстройки Word VSTO. После этого следует настроить **Add-Ins** вкладке настоящего документа.

### <a name="to-create-a-new-project"></a>Создание нового проекта

1. Создание **Word Add-in** проект с именем **MyRibbonAddIn**.

     Дополнительные сведения см. в разделе [Как Создание проектов Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Открывает **ThisAddIn.cs** или **ThisAddIn.vb** файл кода и добавляет **MyRibbonAddIn** проект **обозревателе решений**.

## <a name="create-the-vsto-add-ins-tab"></a>Создание вкладки надстройки VSTO
 Чтобы создать **Add-Ins** вкладку, добавьте **Лента (XML)** в проект. Далее в этом пошаговом руководстве мы добавим некоторые кнопки на эту вкладку.

### <a name="to-create-the-add-ins-tab"></a>Создание вкладки надстройки

1. В меню **Проект** выберите пункт **Добавить новый элемент**.

2. В **Добавление нового элемента** выберите **Лента (XML)**.

3. Измените имя новой ленты на **MyRibbon**и нажмите кнопку **Добавить**.

     **MyRibbon.cs** или **MyRibbon.vb** файл откроется в конструкторе. XML-файл с именем **MyRibbon.xml** также добавляется в проект.

4. В **обозревателе решений**, щелкните правой кнопкой мыши **ThisAddin.cs** или **ThisAddin.vb**, а затем нажмите кнопку **Просмотр кода**.

5. Добавьте следующий код в класс **ThisAddin** . Этот код переопределяет метод `CreateRibbonExtensibilityObject` и возвращает XML-класс ленты в приложение Office.

     [!code-csharp[Trin_Ribbon_Custom_Tab_XML#1](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.cs#1)]
     [!code-vb[Trin_Ribbon_Custom_Tab_XML#1](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.vb#1)]

6. В **обозревателе решений**, щелкните правой кнопкой мыши **MyRibbonAddIn** проект и выберите пункт **построения**. Убедитесь, что сборка проекта выполняется без ошибок.

## <a name="add-buttons-to-the-add-ins-tab"></a>Добавление кнопок на вкладку "надстройки"
 Данная надстройка VSTO предназначена для того, чтобы пользователи могли добавлять стандартный текст и конкретную таблицу в активный документ. Для обеспечения пользовательского интерфейса, добавьте две кнопки на **Add-Ins** вкладку, изменив XML-файле ленты. Далее в этом пошаговом руководстве мы определим методы обратного вызова для кнопок. Дополнительные сведения о XML-файле ленты, см. в разделе [Ribbon XML](../vsto/ribbon-xml.md).

### <a name="to-add-buttons-to-the-add-ins-tab"></a>Добавление кнопок на вкладку "надстройки"

1. В **обозревателе решений**, щелкните правой кнопкой мыши **MyRibbon.xml** и нажмите кнопку **откройте**.

2. Замените содержимое файла **вкладке** элемент следующим кодом XML. Этот XML-код изменяет метку группы элементов управления по умолчанию для **содержимого**, а также добавляет две новые кнопки с метками **вставить текст** и **вставить таблицу**.

    ```xml
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

## <a name="automate-the-document-by-using-the-buttons"></a>Автоматизация документа с помощью кнопок
 Необходимо добавить `onAction` методы обратного вызова для **вставить текст** и **вставить таблицу** кнопки для выполнения действий, когда пользователь щелкает их. Дополнительные сведения о методах обратного вызова для элементов управления ленты см. в разделе [Ribbon XML](../vsto/ribbon-xml.md).

### <a name="to-add-callback-methods-for-the-buttons"></a>Добавление методов обратного вызова для кнопок

1. В **обозревателе решений**, щелкните правой кнопкой мыши **MyRibbon.cs** или **MyRibbon.vb**, а затем нажмите кнопку **откройте**.

2. Добавьте следующий код в верхнюю часть **MyRibbon.cs** или **MyRibbon.vb** файл. Этот код создает псевдоним для пространства имен <xref:Microsoft.Office.Interop.Word>.

     [!code-csharp[Trin_RibbonButtons#1](../vsto/codesnippet/CSharp/Trin_RibbonButtons/MyRibbon.cs#1)]
     [!code-vb[Trin_RibbonButtons#1](../vsto/codesnippet/VisualBasic/Trin_RibbonButtons/MyRibbon.vb#1)]

3. Добавьте следующий метод в класс `MyRibbon` . Это метод обратного вызова для **вставить текст** кнопка, которая добавляет строку в активный документ в текущем положении курсора.

     [!code-csharp[Trin_Ribbon_Custom_Tab_XML#2](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/MyRibbon.cs#2)]
     [!code-vb[Trin_Ribbon_Custom_Tab_XML#2](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/MyRibbon.vb#2)]

4. Добавьте следующий метод в класс `MyRibbon` . Это метод обратного вызова для **вставить таблицу** кнопка, которая добавляет таблицу в активный документ в текущем положении курсора.

     [!code-csharp[Trin_Ribbon_Custom_Tab_XML#3](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/MyRibbon.cs#3)]
     [!code-vb[Trin_Ribbon_Custom_Tab_XML#3](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/MyRibbon.vb#3)]

## <a name="testing-the-vsto-add-in"></a>Тестирование надстройки VSTO
 При запуске проекта открывается Word и вкладка с именем **Add-Ins** отображается на ленте. Нажмите кнопку **вставить текст** и **вставить таблицу** кнопки на **Add-Ins** tab, чтобы проверить код.

### <a name="to-test-your-vsto-add-in"></a>Для тестирования надстройки VSTO выполните следующие действия.

1. Нажмите клавишу **F5** для запуска проекта.

2. Убедитесь, что **Add-Ins** вкладка отображается на ленте.

3. Перейдите на вкладку **Надстройки** .

4. Убедитесь, что **содержимого** группы отображается на ленте.

5. Нажмите кнопку **вставить текст** кнопку **содержимого** группы.

     Строка добавляется в документ в текущем положении курсора.

6. Нажмите кнопку **вставить таблицу** кнопку **содержимого** группы.

     Таблица добавляется в документ в текущем положении курсора.

## <a name="next-steps"></a>Следующие шаги
 Дополнительные сведения о настройке пользовательского интерфейса Office см. в следующих разделах:

- Настройка ленты другого приложения Office. Дополнительные сведения о приложениях, поддерживающих настройку ленты, см. в разделе [Обзор ленты](../vsto/ribbon-overview.md).

- Настройка ленты приложения Office с помощью конструктора лент. Для получения дополнительной информации см. [Ribbon Designer](../vsto/ribbon-designer.md).

- Создание настраиваемой панели действий. Дополнительные сведения см. в разделе [Общие сведения о панели действий](../vsto/actions-pane-overview.md).

- Настройка пользовательского интерфейса для Microsoft Office Outlook с помощью областей формы Outlook. Дополнительные сведения см. в разделе [Пошаговое руководство: Разработка области формы Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md).

## <a name="see-also"></a>См. также
- [Обзор ленты](../vsto/ribbon-overview.md)
- [Ribbon XML](../vsto/ribbon-xml.md)
- [Пошаговое руководство: Создание настраиваемой вкладки с помощью конструктора лент](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
