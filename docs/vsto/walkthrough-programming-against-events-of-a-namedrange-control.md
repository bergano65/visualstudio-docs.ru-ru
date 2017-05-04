---
title: "Пошаговое руководство. Программирование реакции на события элементов управления NamedRange | Microsoft Docs"
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
  - "NamedRange - элемент управления, события"
  - "диапазоны, программирование реакции на события"
  - "листы, автоматизация"
  - "листы, изменение значений ячеек"
  - "листы, события"
ms.assetid: b69676f9-23b2-4ed6-83ab-8868c3f10948
caps.latest.revision: 57
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 56
---
# Пошаговое руководство. Программирование реакции на события элементов управления NamedRange
  В этом пошаговом руководстве демонстрируется добавление элемента управления <xref:Microsoft.Office.Tools.Excel.NamedRange> в лист Microsoft Office Excel и создание кода для его событий с помощью средств разработки Office в Visual Studio.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 В процессе выполнения этого пошагового руководства вы научитесь:  
  
-   Добавление элемента управления <xref:Microsoft.Office.Tools.Excel.NamedRange> в лист.  
  
-   Программирование реакции на события элемента управления <xref:Microsoft.Office.Tools.Excel.NamedRange>.  
  
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
  
1.  Создайте проект книги Excel с именем Мои события именованного диапазона.  Убедитесь, что выбрано **Создать новый документ**.  Дополнительные сведения см. в разделе [Практическое руководство. Создание проектов Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio открывает созданную книгу Excel в конструкторе и добавляет проект My Named Range Events в **обозреватель решений**.  
  
## Добавление в лист текста и именованных диапазонов  
 Поскольку элементы управления ведущего приложения являются расширенными объектами Office, их можно добавлять в документ таким же образом, как добавляется собственный объект.  Например, можно добавить в лист элемент управления Excel <xref:Microsoft.Office.Tools.Excel.NamedRange>, открыв меню **Вставка**, поместив указатель на пункт **Имя** и выбрав **Определить**.  Можно также добавить элемент управления <xref:Microsoft.Office.Tools.Excel.NamedRange>, перетащив его в лист из **панели элементов**.  
  
 На данном этапе в лист будут добавлены два элемента управления именованного диапазона с помощью **панели элементов**, а затем в этот лист будет добавлен текст.  
  
#### Добавление диапазона в лист  
  
1.  Убедитесь, что книга **My именованный диапазон Events.xlsx** открыта в конструкторе Visual Studio `Sheet1`.  
  
2.  Перетащите элемент управления <xref:Microsoft.Office.Tools.Excel.NamedRange> со вкладки **Элементы управления Excel** панели элементов в ячейку **A1** в `Sheet1`.  
  
     Открывается диалоговое окно **Добавление элемента управления NamedRange**.  
  
3.  Убедитесь, что в редактируемом текстовом поле отображается **$A$1**, и ячейка **A1** выбрана.  Если ячейка **A1** не выбрана, щелкните ее.  
  
4.  Нажмите кнопку **ОК**.  
  
     Ячейка **A1** становится диапазоном `namedRange1`.  Видимых изменений на листе не происходит, однако при выборе ячейки **А1** в поле **Имя** в левом верхнем углу листа отображается `namedRange1`.  
  
5.  Добавьте другой элемент управления <xref:Microsoft.Office.Tools.Excel.NamedRange> в ячейку **B3**.  
  
6.  Убедитесь, что в редактируемом текстовом поле отображается **$B$3**, и ячейка **B3** выбрана.  Если ячейка **B3** не выбрана, щелкните ее.  
  
7.  Нажмите кнопку **ОК**.  
  
     Ячейка **В3** становится диапазоном `namedRange2`.  
  
#### Добавление текста в лист  
  
1.  В ячейке **A1** введите следующий текст:  
  
     Это пример элемента управления NamedRange.  
  
2.  В ячейке **A3** \(слева от `namedRange2`\) введите следующий текст:  
  
     События:  
  
 В следующих разделах будет написан код, который вставляет текст в `namedRange2` и модифицирует свойства элемента управления `namedRange2` в ответ на события <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick>, <xref:Microsoft.Office.Tools.Excel.NamedRange.Change> и <xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange> именованного диапазона `namedRange1`.  
  
## Добавление кода в ответ на событие BeforeDoubleClick  
  
#### Вставка текста в Именованный\_Диапазон2 в зависимости от события BeforeDoubleClick  
  
1.  В **Обозревателе решений** щелкните правой кнопкой мыши **Sheet1.vb** или **Sheet1.cs** и выберите **Просмотреть код**.  
  
2.  Дополните код, чтобы обработчик событий `namedRange1_BeforeDoubleClick` выглядел следующим образом:  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#24](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet1.cs#24)]
     [!code-vb[Trin_VstcoreHostControlsExcel#24](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet1.vb#24)]  
  
3.  В C\# необходимо добавлять обработчики событий для именованных диапазонов, как показано в описании события <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> ниже.  Сведения о создании обработчиков событий см. в разделе [Практическое руководство. Создание обработчиков событий в проектах Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#25](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet1.cs#25)]  
  
## Добавление кода в ответ на событие Change  
  
#### Вставка текста в Именованный\_Диапазон2 в зависимости от события Change  
  
1.  Дополните код, чтобы обработчик событий `NamedRange1_Change` выглядел следующим образом:  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#26](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet1.cs#26)]
     [!code-vb[Trin_VstcoreHostControlsExcel#26](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet1.vb#26)]  
  
    > [!NOTE]  
    >  Поскольку двойной щелчок мыши по ячейке в диапазоне Excel переводит в режим редактирования, событие <xref:Microsoft.Office.Tools.Excel.NamedRange.Change> происходит при перемещении выделения за пределы диапазона, даже если в текст не вносятся изменения.  
  
## Добавление кода в ответ на событие SelectionChange  
  
#### Вставка текста в Именованный\_Диапазон2 в зависимости от события SelectionChange  
  
1.  Дополните код, чтобы обработчик событий **NamedRange1\_SelectionChange** выглядел следующим образом:  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#27](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet1.cs#27)]
     [!code-vb[Trin_VstcoreHostControlsExcel#27](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet1.vb#27)]  
  
    > [!NOTE]  
    >  Поскольку двойной щелчок мыши по ячейке в диапазоне Excel приводит к перемещению выделения в диапазон, событие <xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange> происходит до события <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick>.  
  
## Тестирование приложения  
 Теперь можно протестировать книгу, чтобы убедиться, что текст, описывающий события элемента управления <xref:Microsoft.Office.Tools.Excel.NamedRange>, вставляется в другой именованный диапазон при возникновении этих событий.  
  
#### Проверка документа  
  
1.  Нажмите клавишу F5 для запуска проекта.  
  
2.  Поместите курсор в диапазон `namedRange1` и убедитесь, что текст, зависящий от события <xref:Microsoft.Office.Tools.Excel.NamedRange.SelectionChange>, вставляется, и следовательно комментарий вставляется в лист.  
  
3.  Дважды щелкните мышью в диапазоне `namedRange1` и убедитесь, что текст, зависящий от событий <xref:Microsoft.Office.Tools.Excel.NamedRange.BeforeDoubleClick>, вставляется красным курсивом а диапазон `namedRange2`.  
  
4.  Щелкните мышью вне диапазона `namedRange1` и обратите внимание, что событие Change возникает при выходе из режима редактирования, даже если не было сделано никаких изменений в тексте.  
  
5.  Измените текст в `namedRange1`.  
  
6.  Щелкните мышью вне `namedRange1` и убедитесь, что текст, зависящий от события <xref:Microsoft.Office.Tools.Excel.NamedRange.Change>, вставляется голубым цветом в диапазон `namedRange2`.  
  
## Следующие действия  
 В данном пошаговом руководстве показаны основы программирования реакции на события элемента управления <xref:Microsoft.Office.Tools.Excel.NamedRange>.  Далее будет рассмотрена следующая задача.  
  
-   Развертывание проекта.  Дополнительные сведения см. в разделе [Развертывание решения Office](../vsto/deploying-an-office-solution.md).  
  
## См. также  
 [Общие сведения о ведущих элементах и элементах управления ведущего приложения](../vsto/host-items-and-host-controls-overview.md)   
 [Автоматизация Excel с помощью расширенных объектов](../vsto/automating-excel-by-using-extended-objects.md)   
 [Элемент управления NamedRange](../vsto/namedrange-control.md)   
 [Практическое руководство. Изменения размера элементов управления "NamedRange"](../vsto/how-to-resize-namedrange-controls.md)   
 [Практическое руководство. Добавление элементов управления NamedRange на листы](../vsto/how-to-add-namedrange-controls-to-worksheets.md)   
 [Программные ограничения ведущих элементов и элементов управления ведущего приложения](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Практическое руководство. Создание обработчиков событий в проектах Office](../vsto/how-to-create-event-handlers-in-office-projects.md)  
  
  