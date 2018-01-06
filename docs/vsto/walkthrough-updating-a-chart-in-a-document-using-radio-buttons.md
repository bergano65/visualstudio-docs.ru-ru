---
title: "Пошаговое руководство: Обновление диаграммы в документе с помощью переключателей | Документы Microsoft"
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
- documents [Office development in Visual Studio], updating using controls
- controls [Office development in Visual Studio], updating documents
ms.assetid: 56e6d1f2-65a4-41f0-aff5-f0cfd96d7185
caps.latest.revision: "60"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 35f5a865faafc730a13f5d0cd3a432a724434dde
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-updating-a-chart-in-a-document-using-radio-buttons"></a>Пошаговое руководство. Обновление диаграммы в документе с помощью переключателей
  В данном пошаговом руководстве описывается использование переключателей в настройке уровня документа для Microsoft Office Word, позволяющих пользователям выбирать стили диаграмм в документе.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 В данном пошаговом руководстве рассмотрены следующие задачи:  
  
-   добавление диаграммы в документ проекта на уровне документа во время разработки;  
  
-   группировка переключателей путем их добавления в пользовательский элемент управления;  
  
-   изменение стиля диаграммы при выбранном параметре.  
  
 Для просмотра результатов в виде полного примера, см [примеры разработки решений Office и пошаговые руководства](../vsto/office-development-samples-and-walkthroughs.md).  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Предварительные требования  
 Ниже приведены компоненты, необходимые для выполнения данного пошагового руководства.  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] или [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].  
  
## <a name="creating-the-project"></a>Создание проекта  
 Первым шагом является создание документа Word.  
  
#### <a name="to-create-a-new-project"></a>Создание нового проекта  
  
1.  Создайте проект документа Word с именем **параметры диаграммы**. В мастере выберите **создания документа**. Дополнительные сведения см. в разделе [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio откроет новый документ Word в конструкторе и добавляет **параметры диаграммы** проекта **обозревателе решений**.  
  
## <a name="adding-a-chart-to-the-document"></a>Добавление диаграммы в документ  
  
#### <a name="to-add-a-chart"></a>Добавление диаграммы  
  
1.  В документе Word, размещенном в конструкторе Visual Studio, на ленте щелкните **вставить** вкладки.  
  
2.  В **текст** щелкните **вставить объект** кнопку раскрывающегося списка и нажмите кнопку **объекта**.  
  
     **Объекта** откроется диалоговое окно.  
  
3.  В **тип объекта** списке **создать новый** выберите **диаграмма Microsoft Graph** и нажмите кнопку **ОК**.  
  
     Диаграмма будет добавлена в документ в позиции курсора и **таблицы** откроется окно с данными по умолчанию.  
  
4.  Закрыть **таблицы** окно, чтобы принять значения по умолчанию в диаграмме и щелкните внутри документа, чтобы переместить фокус от диаграммы.  
  
5.  Щелкните правой кнопкой мыши диаграмму и выберите **формат объекта**.  
  
6.  На **макета** вкладке **формат объекта** выберите **квадрат** и нажмите кнопку **ОК**.  
  
## <a name="adding-a-user-control-to-the-project"></a>Добавление пользовательского элемента управления в проект  
 Переключатели в документе не являются взаимоисключающими по умолчанию. Их работу можно сделать правильной, добавив их в пользовательский элемент управления и написав код для управления выбором.  
  
#### <a name="to-add-a-user-control"></a>Добавление пользовательского элемента управления  
  
1.  Выберите **параметры диаграммы** проекта в **обозревателе решений**.  
  
2.  В меню **Проект** выберите пункт **Добавить новый элемент**.  
  
3.  В **Добавление нового элемента** диалоговое окно, нажмите кнопку **пользовательский элемент управления**, имя элемента управления **ChartOptions** и нажмите кнопку **добавить**.  
  
#### <a name="to-add-windows-form-controls-to-the-user-control"></a>Добавление элементов управления формы Windows в пользовательский элемент управления  
  
1.  Если пользовательский элемент управления не виден в конструкторе, дважды щелкните **ChartOptions** в **обозревателе решений**.  
  
2.  Из **стандартные элементы управления** вкладке **элементов**, перетащите первый **переключатель** управления в пользовательский элемент управления и измените следующие свойства.  
  
    |Свойство.|Значение|  
    |--------------|-----------|  
    |**Name**|**columnChart**|  
    |**Text**|**Гистограмма**|  
  
3.  Добавьте второй **переключатель** пользователю управления и измените следующие свойства.  
  
    |Свойство.|Значение|  
    |--------------|-----------|  
    |**Name**|**barChart**|  
    |**Text**|**Линейчатая диаграмма**|  
  
4.  Добавьте третий **переключатель** пользователю управления и измените следующие свойства.  
  
    |Свойство.|Значение|  
    |--------------|-----------|  
    |**Name**|**lineChart**|  
    |**Text**|**График**|  
  
5.  Добавьте четвертый **переключатель** пользователю управления и измените следующие свойства.  
  
    |Свойство.|Значение|  
    |--------------|-----------|  
    |**Name**|**areaBlockChart**|  
    |**Text**|**Диаграмма с областями**|  
  
## <a name="adding-references"></a>Добавление ссылок  
 Чтобы получить доступ к диаграмме из пользовательского элемента управления в документе, в проекте должна присутствовать ссылка на сборку Microsoft.Office.Interop.Graph.  
  
#### <a name="to-add-a-reference-to-the-microsoftofficeinteropgraph-assembly"></a>Добавление ссылки на сборку Microsoft.Office.Interop.Graph  
  
1.  В меню **Проект** щелкните команду **Добавить ссылку**.  
  
     Откроется диалоговое окно **Добавление ссылки**.  
  
2.  На **.NET** выберите **Microsoft.Office.Interop.Graph** и нажмите кнопку **ОК**. Выберите версию сборки 14.0.0.0.  
  
## <a name="changing-the-chart-style-when-a-radio-button-is-selected"></a>Изменение стиля диаграммы при выбранном переключателе  
 Чтобы кнопки работали правильно, создайте открытое событие для пользовательского элемента управления, добавьте свойство, чтобы установить тип выбора, и создайте процедуру для события `CheckedChanged` по каждому переключателю.  
  
#### <a name="to-create-an-event-and-property-on-a-user-control"></a>Создание события и свойства по пользовательскому элементу управления  
  
1.  В **обозревателе решений**, щелкните правой кнопкой мыши пользовательский элемент управления и нажмите кнопку **Просмотр кода**.  
  
2.  Добавьте код, чтобы создать событие `SelectionChanged` и свойство `Selection` в классе `ChartOptions`.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#9](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs#9)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#9](../vsto/codesnippet/VisualBasic/my chart options/ChartOptions.vb#9)]  
  
#### <a name="to-handle-the-checkedchange-event-of-the-radio-buttons"></a>Обработка события переключателей CheckedChange  
  
1.  Установите тип диаграммы в обработчике событий `CheckedChanged` переключателя `areaBlockChart`, а затем породите событие.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#10](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs#10)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#10](../vsto/codesnippet/VisualBasic/my chart options/ChartOptions.vb#10)]  
  
2.  Установите тип диаграммы в обработчик событий `CheckedChanged` переключателя `barChart`.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#11](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs#11)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#11](../vsto/codesnippet/VisualBasic/my chart options/ChartOptions.vb#11)]  
  
3.  Установите тип диаграммы в обработчик событий `CheckedChanged` переключателя `columnChart`.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#12](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs#12)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#12](../vsto/codesnippet/VisualBasic/my chart options/ChartOptions.vb#12)]  
  
4.  Установите тип диаграммы в обработчик событий `CheckedChanged` переключателя `lineChart`.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#13](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs#13)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#13](../vsto/codesnippet/VisualBasic/my chart options/ChartOptions.vb#13)]  
  
5.  В языке программирования C# для переключателей должны быть добавлены обработчики событий. Код можно добавить в конструктор `ChartOptions` под вызовом `InitializeComponent`. Сведения о создании обработчиков событий см. в разделе [как: Создание обработчиков событий в проектах Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#14](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ChartOptions.cs#14)]  
  
## <a name="adding-the-user-control-to-the-document"></a>Добавление пользовательского элемента управления в документ  
 При построении решения новый пользовательский элемент управления автоматически добавляется **элементов**. Затем можно перетащить элемент управления, **элементов** в документе.  
  
#### <a name="to-add-the-user-control-your-document"></a>Добавление пользовательского элемента управления в документ  
  
1.  В меню **Сборка** выберите **Собрать решение**.  
  
     **ChartOptions** пользовательский элемент управления добавляется к **элементов**.  
  
2.  В **обозревателе решений**, щелкните правой кнопкой мыши **ThisDocument.vb** или **ThisDocument.cs**, а затем нажмите кнопку **конструктор представлений**.  
  
3.  Перетащите `ChartOptions` управления из **элементов** в документ.  
  
     В **свойства** окна, имя элемента управления, который только что добавлен в документ `ChartOptions1`.  
  
## <a name="changing-the-chart-type"></a>Изменение типа диаграммы  
 Создайте обработчик событий, чтобы изменить тип диаграммы в соответствии с параметром, выбранным в пользовательском элементе управления.  
  
#### <a name="to-change-the-type-of-chart-that-is-displayed-in-the-document"></a>Изменение типа диаграммы, отображаемой в документе  
  
1.  Добавьте следующий обработчик событий в класс `ThisDocument`.  
  
     [!code-vb[Trin_VstcoreProgrammingControlsWord#15](../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb#15)]
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#15](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#15)]  
  
2.  В языке программирования C# в событие <xref:Microsoft.Office.Tools.Word.Document.Startup> должен быть добавлен обработчик события для пользовательского элемента управления.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#16](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#16)]  
  
## <a name="testing-the-application"></a>Тестирование приложения  
 Теперь можно проверить документ и убедиться, что при выборе переключателя стиль диаграммы обновляется правильно.  
  
#### <a name="to-test-your-document"></a>Проверка документа  
  
1.  Нажмите клавишу F5 для запуска проекта.  
  
2.  Выберите различные переключатели.  
  
3.  Подтвердите, что изменения стиля диаграммы соответствуют выбору.  
  
## <a name="next-steps"></a>Следующие шаги  
 Ниже приводятся некоторые из возможных последующих задач.  
  
-   Использование кнопки для заполнения текстового поля. Дополнительные сведения см. в разделе [Пошаговое руководство: отображение текста в текстовом поле в документ с помощью кнопки](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-document-using-a-button.md).  
  
-   Изменение форматирования путем выбора стиля из поля со списком. Дополнительные сведения см. в разделе [Пошаговое руководство: изменение документов форматирования с помощью элементов управления CheckBox](../vsto/walkthrough-changing-document-formatting-using-checkbox-controls.md).  
  
## <a name="see-also"></a>См. также  
 [Пошаговые руководства с использованием Word](../vsto/walkthroughs-using-word.md)   
 [Примеры разработки решений Office и пошаговые руководства](../vsto/office-development-samples-and-walkthroughs.md)   
 [Ограничения по использованию элементов управления Windows Forms в документах Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)  
  
  