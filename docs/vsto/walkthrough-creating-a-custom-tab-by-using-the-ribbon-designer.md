---
title: "Пошаговое руководство: Создание настраиваемой вкладки с помощью конструктора лент | Документы Microsoft"
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
- actions panes [Office development in Visual Studio], controlling from Ribbon
- Ribbon [Office development in Visual Studio], customizing
- Ribbon Designer [Office development in Visual Studio]
- customizing the Ribbon, tabs
- custom Ribbon, tabs
- Custom tab [Office development in Visual Studio]
ms.assetid: 312865e6-950f-46ab-88de-fe7eb8036bfe
caps.latest.revision: "68"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 811e4eff77780bda2b348c26bb220a29d5fd1731
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer"></a>Пошаговое руководство. Создание настраиваемой вкладки с помощью конструктора лент
  Конструктор лент позволяет создать настраиваемую вкладку, а затем добавить и расположить на ней элементы управления.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 В данном пошаговом руководстве рассмотрены следующие задачи:  
  
-   [Создание панелей действий](#BKMK_CreateActionsPanes).  
  
-   [Создание настраиваемой вкладки](#BKMK_CreateCustomTab).  
  
-   [Скрытие и отображение панелей действий при помощи кнопок настраиваемой вкладки](#BKMK_HideShowActionsPane).  
  
> [!NOTE]  
>  Отображаемые на компьютере имена или расположения некоторых элементов пользовательского интерфейса Visual Studio могут отличаться от указанных в следующих инструкциях. Это зависит от имеющегося выпуска Visual Studio и используемых параметров. Дополнительные сведения см. в разделе [Персонализация интегрированной среды разработки Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Предварительные требования  
 Ниже приведены компоненты, необходимые для выполнения данного пошагового руководства.  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Excel  
  
## <a name="creating-an-excel-workbook-project"></a>Создание проекта книги Excel  
 Этапы использования конструктора лент практически идентичны для всех приложений Office. В этом примере используется книга Excel.  
  
#### <a name="to-create-an-excel-workbook-project"></a>Создание проекта книги Excel  
  
-   Создайте проект книги Excel с именем **MyExcelRibbon**. Дополнительные сведения см. в разделе [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio открывает новую книгу в конструкторе и добавляет **MyExcelRibbon** проекта **обозревателе решений**.  
  
##  <a name="BKMK_CreateActionsPanes"></a>Создание панелей действий  
 Добавьте в проект две настраиваемые панели действий. Позже на настраиваемой вкладке будут добавлены кнопки для скрытия и отображения этих панелей действий.  
  
#### <a name="to-create-actions-panes"></a>Создание панелей действий  
  
1.  В меню **Проект** выберите пункт **Добавить новый элемент**.  
  
2.  В **Добавление нового элемента** выберите **ActionsPaneControl**и нажмите кнопку **добавить**.  
  
     **ActionsPaneControl1.cs** или **ActionsPaneControl1.vb** файл откроется в конструкторе.  
  
3.  Из **стандартные элементы управления** вкладке **элементов**, добавления метки к рабочей области конструктора.  
  
4.  В **свойства** задайте **текст** метки label1 значение **панель действий 1**.  
  
5.  Повторите этапы 1–5, чтобы создать вторую панель действий и метку. Задать **текст** свойство второй метки значение **панель действий 2**.  
  
##  <a name="BKMK_CreateCustomTab"></a>Создание настраиваемой вкладки  
 Один из принципов проектирования приложений Office состоит в том, что пользователь всегда должен иметь возможность распоряжаться пользовательским интерфейсом приложения Office. Чтобы обеспечить такую возможность для панелей действий, можно добавить на настраиваемую вкладку ленты кнопки, скрывающие и отображающие каждую панель. Чтобы создать настраиваемую вкладку, добавьте **Лента (визуальный конструктор)** в проект. Конструктор помогает добавлять и размещать элементы управления, задавать их свойства и обрабатывать связанные с ними события.  
  
#### <a name="to-create-a-custom-tab"></a>Создание настраиваемой вкладки  
  
1.  В меню **Проект** выберите пункт **Добавить новый элемент**.  
  
2.  В диалоговом окне **Добавление нового элемента** выберите элемент **Лента (визуальный конструктор)**.  
  
3.  Измените имя новой ленты на **MyRibbon**и выберите **добавить**.  
  
     В конструкторе лент откроется файл **MyRibbon.cs** или **MyRibbon.vb** ; отобразятся вкладка и группа, используемые по умолчанию.  
  
4.  В конструкторе лент перейдите на вкладку по умолчанию.  
  
5.  В **свойства** окна, разверните **ControlId** , а затем установите **ControlIdType** свойства **настраиваемый**.  
  
6.  Задать **метка** свойства **My Custom Tab**.  
  
7.  В конструкторе лент выберите **group1**.  
  
8.  В **свойства** задайте **метка** для **Диспетчер панелей действий**.  
  
9. Из **элементы управления ленты Office** вкладке **элементов**, перетащите кнопку **group1**.  
  
10. Выберите **button1**.  
  
11. В **свойства** задайте **метка** для **отобразить панель действий 1**.  
  
12. Добавьте вторую кнопку в **group1**и задайте **метка** свойства **отобразить панель действий 2**.  
  
13. Из **элементы управления ленты Office** вкладке **элементов**, перетащите **ToggleButton** управления **group1**.  
  
14. Задать **метка** свойства **скрыть панель действий**.  
  
##  <a name="BKMK_HideShowActionsPane"></a>Скрытие и отображение панелей действий при помощи кнопок настраиваемой вкладки  
 Последним этапом является добавление кода, который взаимодействует с пользователем. Добавьте обработчики событий для событий <xref:Microsoft.Office.Tools.Ribbon.RibbonButton.Click> обеих кнопок и события <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click> выключателя. Добавьте в эти обработчики событий код для скрытия и отображения панелей действий.  
  
#### <a name="to-hide-and-show-actions-panes-by-using-buttons-in-the-custom-tab"></a>Скрытие и отображение панелей действий при помощи кнопок настраиваемой вкладки  
  
1.  В **обозревателе решений**, откройте контекстное меню для файла MyRibbon.cs или MyRibbon.vb и выберите **Просмотр кода**.  
  
2.  Добавьте следующий код в начало класса `MyRibbon`. Данный код создает два объекта панелей действий.  
  
     [!code-csharp[Trin_Ribbon_Custom_Tab#1](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab/MyRibbon.cs#1)]
     [!code-vb[Trin_Ribbon_Custom_Tab#1](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab/MyRibbon.vb#1)]  
  
3.  Замените метод `MyRibbon_Load` следующим кодом. Данный код добавляет объекты панелей действий в коллекцию панелей действий <xref:Microsoft.Office.Tools.ActionsPane.Controls%2A> и скрывает объекты. Кроме того, код Visual C# присоединяет делегаты к нескольким событиям элементов управления ленты.  
  
     [!code-csharp[Trin_Ribbon_Custom_Tab#2](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab/MyRibbon.cs#2)]
     [!code-vb[Trin_Ribbon_Custom_Tab#2](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab/MyRibbon.vb#2)]  
  
4.  Добавьте следующие три метода обработчиков событий в класс `MyRibbon`. Эти методы обрабатывают события <xref:Microsoft.Office.Tools.Ribbon.RibbonButton.Click> обеих кнопок и события <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click> выключателя. Обработчики событий button1 и button2 отображают соответствующие панели действий. Обработчик событий toggleButton1 отображает и скрывает активную панель действий.  
  
     [!code-csharp[Trin_Ribbon_Custom_Tab#3](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab/MyRibbon.cs#3)]
     [!code-vb[Trin_Ribbon_Custom_Tab#3](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab/MyRibbon.vb#3)]  
  
## <a name="testing-the-custom-tab"></a>Тестирование настраиваемой вкладки  
 При запуске проекта, запускается приложение Excel и **My Custom Tab** на ленте появляется вкладка. Нажимая кнопки на **My Custom Tab** для отображения или скрытия панели действий.  
  
#### <a name="to-test-the-custom-tab"></a>Тестирование настраиваемой вкладки  
  
1.  Нажмите клавишу F5 для запуска проекта.  
  
2.  Выберите **My Custom Tab** вкладки.  
  
3.  В **Диспетчер настраиваемой панели действий** выберите **отобразить панель действий 1**.  
  
     Панель действий отображается и отображается метка **панель действий 1**.  
  
4.  Выберите **отобразить панель действий 2**.  
  
     Панель действий отображается и отображается метка **панель действий 2**.  
  
5.  Выберите **скрыть панель действий**.  
  
     Панели действий будут скрыты.  
  
## <a name="next-steps"></a>Дальнейшие действия  
 Дополнительные сведения о настройке пользовательского интерфейса Office см. в следующих разделах:  
  
-   Добавление пользовательского интерфейса на основе контекста к настройкам уровня документа. Дополнительные сведения см. в разделе [Actions Pane Overview](../vsto/actions-pane-overview.md).  
  
-   Расширение стандартной или пользовательской формы Microsoft Office Outlook. Дополнительные сведения см. в разделе [Пошаговое руководство: разработка области формы Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md).  
  
## <a name="see-also"></a>См. также  
 [Accessing the Ribbon at Run Time](../vsto/accessing-the-ribbon-at-run-time.md)   
 [Обзор ленты](../vsto/ribbon-overview.md)   
 [Конструктор лент](../vsto/ribbon-designer.md)   
 [Настройка ленты для Outlook](../vsto/customizing-a-ribbon-for-outlook.md)   
 [Как: работа с настройкой ленты](../vsto/how-to-get-started-customizing-the-ribbon.md)   
 [Как: изменение положения вкладки на ленте](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)   
 [Как: Настройка встроенной вкладки](../vsto/how-to-customize-a-built-in-tab.md)   
 [Как: Добавление элементов управления в представление Backstage](../vsto/how-to-add-controls-to-the-backstage-view.md)   
 [Общие сведения об объектной модели ленты](../vsto/ribbon-object-model-overview.md)  
  
  