---
title: "Пошаговое руководство. Изменение форматирования листа с использованием элементов управления CheckBox"
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
  - "элементы управления [разработка решений Office в Visual Studio], добавление к листам"
  - "листы, изменение форматирования с помощью управляемых элементов управления"
  - "листы, элементы управления "флажок""
ms.assetid: 4be79613-50a0-428e-9816-aadbc098272a
caps.latest.revision: 70
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 69
---
# Пошаговое руководство. Изменение форматирования листа с использованием элементов управления CheckBox
  В этом пошаговом руководстве описываются основные принципы использования флажков для изменения форматирования листа Microsoft Office Excel.  Для создания кода и добавления его в проект будут использоваться средства разработки Office в Visual Studio.  Для просмотра результатов в готовом примере обратитесь к примеру элементов управления Excel в разделе [Образцы и пошаговые руководства разработки Office](../vsto/office-development-samples-and-walkthroughs.md).  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 В процессе выполнения этого пошагового руководства вы научитесь:  
  
-   Добавление текста и элементов управления на лист.  
  
-   Форматирование текста при выборе определенного параметра.  
  
-   Тестирование проекта.  
  
> [!NOTE]  
>  Отображаемые на компьютере имена или расположения некоторых элементов пользовательского интерфейса Visual Studio могут отличаться от указанных в следующих инструкциях.  Эти элементы определяются используемым выпуском Visual Studio и его параметрами.  Дополнительные сведения см. в разделе [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ru-ru/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Обязательные компоненты  
 Ниже приведены компоненты, необходимые для выполнения данного пошагового руководства.  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] или [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
## Создание проекта  
 На данном этапе с помощью Visual Studio создается проект книги Excel.  
  
#### Создание нового проекта  
  
1.  Создайте проект книги Excel с именем Форматирование Excel.  Убедитесь, что выбрано **Создать новый документ**.  Дополнительные сведения см. в разделе [Практическое руководство. Создание проектов Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Созданная книга Excel открывается в конструкторе Visual Studio. Проект **Форматирование Excel** добавляется в **обозреватель решений**.  
  
## Добавление текста и элементов управления на лист  
 В этом пошаговом руководстве выполняется добавление трех элементов управления <xref:Microsoft.Office.Tools.Excel.Controls.CheckBox> и текстового содержимого к элементу управления <xref:Microsoft.Office.Tools.Excel.NamedRange>.  
  
#### Добавление трех флажков  
  
1.  Убедитесь, что в конструкторе Visual Studio открыт лист `Sheet1` книги.  
  
2.  Со вкладки **Общие элементы управленияпанели элементов** перетащите элемент управления <xref:Microsoft.Office.Tools.Excel.Controls.CheckBox> в ячейку **B2** на листе **Лист1** \(или рядом с ней\).  
  
3.  В меню **Вид** выберите команду **Окно свойств**.  
  
4.  Убедитесь, что в поле со списком имен объектов окна **Свойства** отображается элемент **Checkbox1**, после чего измените следующие свойства:  
  
    |Свойство|Значение|  
    |--------------|--------------|  
    |**Имя**|**applyBoldFont**|  
    |**Текст.**|Полужирный|  
  
5.  Перетащите второй флажок в ячейку **B4** \(или рядом с ней\) и измените следующие свойства:  
  
    |Свойство|Значение|  
    |--------------|--------------|  
    |**Имя**|**applyItalicFont**|  
    |**Текст.**|Курсив|  
  
6.  Перетащите третий флажок в ячейку **B6** \(или рядом с ней\) и измените следующие свойства:  
  
    |Свойство|Значение|  
    |--------------|--------------|  
    |**Имя**|**applyUnderlineFont**|  
    |**Текст.**|Подчеркивание|  
  
7.  Выберите все три флажка, удерживая нажатой клавишу CTRL.  
  
8.  В группе в составе размещения на вкладку формата в Excel щелкните **Выровнять**, а затем нажмите кнопку **Выровнять по левому краю**.  
  
     3 Элементов управления checkbox выравнены слева на позиции первого элемента управления.  
  
     После этого перетащите на лист элемент управления <xref:Microsoft.Office.Tools.Excel.NamedRange>.  
  
    > [!NOTE]  
    >  Чтобы добавить элемент управления <xref:Microsoft.Office.Tools.Excel.NamedRange>, также можно ввести **textFont** в поле **Имя**.  
  
#### Добавление текста в элемент управления NamedRange  
  
1.  Со вкладки **Элементы управления Excel** панели элементов перетащите элемент управления <xref:Microsoft.Office.Tools.Excel.NamedRange> в ячейку **B9**.  
  
2.  Убедитесь, что в редактируемом текстовом поле отображается **$B$9**, и ячейка **B9** выбрана.  Если ячейка **B9** не выбрана, щелкните ее.  
  
3.  Нажмите кнопку **ОК**.  
  
4.  В ячейке **B9** создается диапазон `NamedRange1`.  
  
     Видимых изменений на листе не происходит, однако при выборе ячейки **B9** в поле **Имя** в левом верхнем углу листа отображается `NamedRange1`.  
  
5.  Убедитесь, что в поле со списком имен объектов окна **Свойства** отображается элемент **NamedRange1**, после чего измените следующие свойства:  
  
    |Свойство|Значение|  
    |--------------|--------------|  
    |**Имя**|**textFont**|  
    |**Value2**|Установите соответствующий флажок, чтобы изменить форматирование текста.|  
  
 Далее напишите код для форматирования текста при выборе определенного параметра.  
  
## Форматирование текста при выборе определенного параметра  
 В этом разделе создается код, определяющий изменение форматирования текста на листе при выборе соответствующего параметра форматирования.  
  
#### Изменение форматирования при установке флажка  
  
1.  Щелкните правой кнопкой мыши лист **Лист1**, затем в появившемся контекстном меню выберите команду **Перейти к коду**.  
  
2.  В обработчике событий <xref:System.Windows.Forms.Control.Click> для флажка `applyBoldFont` добавьте следующий код:  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#7](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/Sheet1.cs#7)]
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#7](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/VB/Sheet1.vb#7)]  
  
3.  В обработчике событий <xref:System.Windows.Forms.Control.Click> для флажка `applyItalicFont` добавьте следующий код:  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#8](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/Sheet1.cs#8)]
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#8](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/VB/Sheet1.vb#8)]  
  
4.  В обработчике событий <xref:System.Windows.Forms.Control.Click> для флажка `applyUnderlineFont` добавьте следующий код:  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#9](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/Sheet1.cs#9)]
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#9](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/VB/Sheet1.vb#9)]  
  
5.  В C\# следует добавить обработчики событий для флажков к событию <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup>, как показано ниже.  Сведения о создании обработчиков событий см. в разделе [Практическое руководство. Создание обработчиков событий в проектах Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#10](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/Sheet1.cs#10)]  
  
## Тестирование приложения  
 Теперь можно правильность форматирования текста книги при установке или снятии флажков.  
  
#### Проверка рабочей книги  
  
1.  Нажмите клавишу F5 для запуска проекта.  
  
2.  Установите или снимите флажок.  
  
3.  Убедитесь, что применяется правильное форматирование текста.  
  
## Следующие действия  
 В этом пошаговом руководстве описываются основные принципы использования флажков и форматирования текста на листах Microsoft Office Excel.  Далее будут рассмотрены следующие задачи:  
  
-   Развертывание проекта.  Дополнительные сведения см. в разделе [Развертывание решения Office с помощью ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).  
  
-   Заполнение текстового поля с помощью кнопки.  Дополнительные сведения см. в разделе [Пошаговое руководство. Отображение текста в текстовом поле рабочего листа с помощью кнопки](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md).  
  
## См. также  
 [Пошаговые руководства с использованием Excel](../vsto/walkthroughs-using-excel.md)   
 [Элемент управления NamedRange](../vsto/namedrange-control.md)   
 [Ограничения по использованию элементов управления Windows Forms в документах Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)  
  
  