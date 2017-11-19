---
title: "Пошаговое руководство: Изменение форматирования листа с использованием элементов управления CheckBox | Документы Microsoft"
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
- worksheets, changing formatting using managed controls
- worksheets, check box controls
- controls [Office development in Visual Studio], adding to worksheets
ms.assetid: 4be79613-50a0-428e-9816-aadbc098272a
caps.latest.revision: "70"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7f10b0ed77dc9d5f97b6fc2fc4f218c86dafee41
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-changing-worksheet-formatting-using-checkbox-controls"></a>Пошаговое руководство. Изменение форматирования листа с использованием элементов управления CheckBox
  В этом пошаговом руководстве описываются основные принципы использования флажков на листе Microsoft Office Excel для изменения форматирования. Будет использовать средства разработки Office в Visual Studio для создания и добавления кода в проект. Для просмотра результатов в виде полного примера, см [примеры разработки решений Office и пошаговые руководства](../vsto/office-development-samples-and-walkthroughs.md).  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 В этом пошаговом руководстве описаны следующие процедуры.  
  
-   Добавление текста и элементов управления на лист.  
  
-   Если параметр выбран, форматирование текста.  
  
-   Тестирование проекта.  
  
> [!NOTE]  
>  Отображаемые на компьютере имена или расположения некоторых элементов пользовательского интерфейса Visual Studio могут отличаться от указанных в следующих инструкциях. Это зависит от имеющегося выпуска Visual Studio и используемых параметров. Дополнительные сведения см. в разделе [Персонализация интегрированной среды разработки Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Предварительные требования  
 Ниже приведены компоненты, необходимые для выполнения данного пошагового руководства.  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] или [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
## <a name="creating-the-project"></a>Создание проекта  
 На этом шаге будет создан проект книги Excel с помощью Visual Studio.  
  
#### <a name="to-create-a-new-project"></a>Создание нового проекта  
  
1.  Создайте проект книги Excel с именем **форматирование Excel**. Убедитесь, что **создания документа** выбран. Дополнительные сведения см. в разделе [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio открывает новую книгу Excel в конструкторе и добавляет **форматирование Excel** проекта **обозревателе решений**.  
  
## <a name="adding-text-and-controls-to-the-worksheet"></a>Добавление текста и элементов управления на лист  
 Для этого пошагового руководства потребуется три <xref:Microsoft.Office.Tools.Excel.Controls.CheckBox> элементов управления и некоторый текст в <xref:Microsoft.Office.Tools.Excel.NamedRange> элемента управления.  
  
#### <a name="to-add-three-check-boxes"></a>Чтобы добавить три флажка  
  
1.  Убедитесь, что книга открыта в конструкторе Visual Studio, которые `Sheet1` открыт.  
  
2.  Из **стандартные элементы управления** вкладке **элементов**, перетащите <xref:Microsoft.Office.Tools.Excel.Controls.CheckBox> управления в ячейку или рядом с **В2** в **Sheet1**.  
  
3.  Из **представление** последовательно выберите пункты **свойства** окна.  
  
4.  Убедитесь, что **Checkbox1** отображается в поле имя списка объектов **свойства** окна и измените следующие свойства:  
  
    |Свойство|Значение|  
    |--------------|-----------|  
    |**Имя**|**applyBoldFont**|  
    |**Text**|**Полужирный**|  
  
5.  Перетащите второй флажок в ячейку или рядом **B4** и измените следующие свойства:  
  
    |Свойство|Значение|  
    |--------------|-----------|  
    |**Имя**|**applyItalicFont**|  
    |**Text**|**Курсив**|  
  
6.  Перетащите третий флажок в ячейку или рядом **B6** и измените следующие свойства:  
  
    |Свойство|Значение|  
    |--------------|-----------|  
    |**Имя**|**applyUnderlineFont**|  
    |**Text**|**Подчеркивание**|  
  
7.  Удерживая нажатой клавишу CTRL, выберите все три флажка.  
  
8.  На вкладке «Формат» в Excel в группе расположение щелкните **выровнять**, а затем нажмите кнопку **Выровнять по левому краю**.  
  
     Три флажка выровнены по левой позиции первого выбранного элемента управления.  
  
     Затем будет перетащите <xref:Microsoft.Office.Tools.Excel.NamedRange> управления на лист.  
  
    > [!NOTE]  
    >  Можно также добавить <xref:Microsoft.Office.Tools.Excel.NamedRange> управления, введя **textFont** в **имя** поле.  
  
#### <a name="to-add-text-to-a-namedrange-control"></a>Добавление текста в элементе управления NamedRange  
  
1.  Из **элементов управления Excel** вкладки панели элементов перетащите <xref:Microsoft.Office.Tools.Excel.NamedRange> управления ячейку **B9**.  
  
2.  Убедитесь, что **$B$ 9** отображается в редактируемом текстовом поле и ячейка **B9** выбран. Если это не так, щелкните ячейку **B9** для ее выделения.  
  
3.  Нажмите кнопку **ОК**.  
  
4.  Ячейка **B9** становится диапазоном `NamedRange1`.  
  
     Никак не видны на листе, но `NamedRange1` отображается в **имя** (над листом слева) ячеек **B9** выбран.  
  
5.  Убедитесь, что **NamedRange1** отображается в поле имя списка объектов **свойства** окна и измените следующие свойства:  
  
    |Свойство|Значение|  
    |--------------|-----------|  
    |**Имя**|**textFont**|  
    |**Value2**|**Установите флажок, чтобы изменить форматирование текста.**|  
  
 Затем напишите код для форматирования текста при выбранном параметре.  
  
## <a name="formatting-the-text-when-an-option-is-selected"></a>Форматирование текста параметром при выборе  
 В этом разделе будет написан код, когда пользователь выбирает способ форматирования, является изменение формата текста на рабочем листе.  
  
#### <a name="to-change-formatting-when-a-check-box-is-selected"></a>Для изменения форматирования, если флажок установлен  
  
1.  Щелкните правой кнопкой мыши **Sheet1**, а затем нажмите кнопку **Просмотр кода** в контекстном меню.  
  
2.  Добавьте следующий код в <xref:System.Windows.Forms.Control.Click> обработчик событий `applyBoldFont` флажок:  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#7](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#7)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#7](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#7)]  
  
3.  Добавьте следующий код в <xref:System.Windows.Forms.Control.Click> обработчик событий `applyItalicFont` флажок:  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#8](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#8)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#8](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#8)]  
  
4.  Добавьте следующий код в <xref:System.Windows.Forms.Control.Click> обработчик событий `applyUnderlineFont` флажок:  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#9](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#9)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#9](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#9)]  
  
5.  В C# необходимо добавить обработчики событий для флажков для <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> события, как показано ниже. Сведения о создании обработчиков событий см. в разделе [как: Создание обработчиков событий в проектах Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#10)]  
  
## <a name="testing-the-application"></a>Тестирование приложения  
 Теперь можно протестировать книгу, чтобы убедиться в том, что текст имеет правильный формат при установке или снятии флажка.  
  
#### <a name="to-test-your-workbook"></a>Проверка книги  
  
1.  Нажмите клавишу F5 для запуска проекта.  
  
2.  Установите или снимите флажок.  
  
3.  Убедитесь, что текст имеет правильный формат.  
  
## <a name="next-steps"></a>Дальнейшие действия  
 В этом пошаговом руководстве показаны основные принципы использования флажков и форматирования текста на листах Excel. Ниже приводятся некоторые из возможных последующих задач.  
  
-   Развертывание проекта. Дополнительные сведения см. в разделе [развертывание решения Office с помощью ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).  
  
-   Использование кнопки для заполнения текстового поля. Дополнительные сведения см. в разделе [Пошаговое руководство: отображение текста в текстовом поле в лист с помощью кнопки](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md).  
  
## <a name="see-also"></a>См. также  
 [Пошаговые руководства с использованием Excel](../vsto/walkthroughs-using-excel.md)   
 [Элемент управления NamedRange](../vsto/namedrange-control.md)   
 [Ограничения по использованию элементов управления Windows Forms в документах Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)  
  
  