---
title: 'Как: обновления источника данных с данными из элемента управления ведущего приложения'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], data source updates
- data [Office development in Visual Studio], updating a data source from a document
- host controls [Office development in Visual Studio], data source updates
- Office documents [Office development in Visual Studio, data sources
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 5603b1661a1b329692508eb43a629919f2f5d14e
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/17/2018
---
# <a name="how-to-update-a-data-source-with-data-from-a-host-control"></a>Как: обновления источника данных с данными из элемента управления ведущего приложения
  Вы можете привязать элемент управления ведущего приложения к источнику данных и обновлять источник данных с помощью изменений, внесенных в данные в элементе управления. Этот процесс включает два основных этапа.  
  
1.  Обновление источника данных в памяти с использованием измененных данных в элементе управления. Как правило, источник данных в памяти — это <xref:System.Data.DataSet>, <xref:System.Data.DataTable>или какой-либо другой объект данных.  
  
2.  Обновление базы данных с использованием измененных данных в источнике данных в памяти. Это применимо только в том случае, если источник данных подключен к внутренней базе данных, например к базе данных SQL Server или Microsoft Office Access.  
  
 Дополнительные сведения об элементах управления ведущего приложения и привязке данных см. в разделе [ведущие элементы и размещать элементы управления](../vsto/host-items-and-host-controls-overview.md) и [привязывать данные к элементам управления в решениях Office](../vsto/binding-data-to-controls-in-office-solutions.md).  
  
 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]  
  
## <a name="update-the-in-memory-data-source"></a>Обновление источника данных в памяти  
 По умолчанию элементы управления ведущего приложения с поддержкой простой привязки данных (например, элементы управления содержимым в документе Word или элемент управления диапазона на листе Excel) не сохраняют изменения данных в источнике данных в памяти. То есть когда пользователь изменяет значение в элементе управления ведущего приложения и затем выходит из этого элемента управления, новое значение в элементе управления не сохраняется автоматически в источнике данных.  
  
 Чтобы сохранить данные в источник данных, можно написать код, который обновляет источник данных в ответ на определенное событие во время выполнения или можно настроить элемент управления для автоматического обновления источника данных при изменении значения в элементе управления.  
  
 Нет необходимости сохранять изменения <xref:Microsoft.Office.Tools.Excel.ListObject> в источнике данных в памяти. При привязке элемента управления <xref:Microsoft.Office.Tools.Excel.ListObject> к данным элемент управления <xref:Microsoft.Office.Tools.Excel.ListObject> автоматически сохраняет изменения в источнике данных в памяти без необходимости написания дополнительного кода.  
  
### <a name="to-update-the-in-memory-data-source-at-runtime"></a>Для обновления источника данных в памяти во время выполнения  
  
-   Вызовите метод <xref:System.Windows.Forms.Binding.WriteValue%2A> объекта <xref:System.Windows.Forms.Binding> , который привязывает элемент управления к источнику данных.  
  
     В следующем примере выполняется сохранение изменений, внесенных в элемент управления <xref:Microsoft.Office.Tools.Excel.NamedRange> в листе Excel, в источнике данных. В этом примере предполагается, что имеется элемент управления <xref:Microsoft.Office.Tools.Excel.NamedRange> с именем `namedRange1` , свойство <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> которого привязано к полю в источнике данных.  
  
     [!code-csharp[Trin_VstcoreDataExcel#1](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#1)]
     [!code-vb[Trin_VstcoreDataExcel#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#1)]  
  
### <a name="automatically-update-the-in-memory-data-source"></a>Автоматическое обновление источника данных в памяти  
 Вы также можете настроить элемент управления, чтобы он автоматически обновлял источник данных в памяти. В проекте уровня документа это можно сделать с помощью кода или конструктора. В проекте надстройки VSTO необходимо использовать код.  
  
#### <a name="to-set-a-control-to-automatically-update-the-in-memory-data-source-by-using-code"></a>Установка автоматического обновления источника данных в памяти элементом управления с помощью кода  
  
1.  Используйте режим System.Windows.Forms.DataSourceUpdateMode.OnPropertyChanged <xref:System.Windows.Forms.Binding> объект, который привязывает элемент управления к источнику данных. Обновлять источник данных можно двумя способами.  
  
    -   Для обновления источника данных при проверке элемента управления установите это свойство проверке.  
  
    -   Для обновления источника данных при изменении значения свойства элемента управления с привязкой к данным, этому свойству присвоено System.Windows.Forms.DataSourceUpdateMode.OnPropertyChanged.  
  
        > [!NOTE]  
        >  Параметр System.Windows.Forms.DataSourceUpdateMode.OnPropertyChanged применяется для элементов управления ведущего приложения Word, поскольку Word не уведомления не предложение документа или изменение элемента управления. Однако этот вариант можно использовать для элементов управления Windows Forms в документах Word.  
  
     В следующем примере элемент управления <xref:Microsoft.Office.Tools.Excel.NamedRange> настраивается для автоматического обновления источника данных при изменении значения в этом элементе управления. В этом примере предполагается, что имеется элемент управления <xref:Microsoft.Office.Tools.Excel.NamedRange> с именем `namedRange1` , свойство <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> которого привязано к полю в источнике данных.  
  
     [!code-csharp[Trin_VstcoreDataExcel#19](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#19)]
     [!code-vb[Trin_VstcoreDataExcel#19](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#19)]  
  
#### <a name="to-set-a-control-to-automatically-update-the-in-memory-data-source-by-using-the-designer"></a>Установка автоматического обновления источника данных в памяти элементом управления с помощью конструктора  
  
1.  В Visual Studio откройте документ Word или книгу Excel в конструкторе.  
  
2.  Щелкните элемент управления, который вы хотите настроить для автоматического обновления источника данных.  
  
3.  В окне **Свойства** разверните свойство **(DataBindings)** .  
  
4.  Рядом с **(Дополнительно)** свойства, нажмите кнопку с многоточием (![экрана VisualStudioEllipsesButton](../vsto/media/vbellipsesbutton.png "экрана VisualStudioEllipsesButton")).  
  
5.  В диалоговом окне **Форматирование и дополнительная привязка** щелкните раскрывающийся список **Режим обновления источника данных** и выберите одно из следующих значений.  
  
    -   Для обновления источника данных при проверке элемента управления выберите значение **OnValidation**.  
  
    -   Для обновления источника данных при изменении значения свойства привязки к данным элемента управления выберите значение **OnPropertyChanged**.  
  
        > [!NOTE]  
        >  Вариант с **OnPropertyChanged** не применяется для элементов управления ведущего приложения Word, поскольку Word не предоставляет уведомления об изменении документа или изменении элемента управления. Однако этот вариант можно использовать для элементов управления Windows Forms в документах Word.  
  
6.  Закройте диалоговое окно **Форматирование и дополнительная привязка** .  
  
## <a name="update-the-database"></a>Обновление базы данных  
 Если источник данных в памяти связан с базой данных, необходимо обновить базу данных с использованием изменений в источнике данных. Дополнительные сведения об обновлении базы данных см. в разделе [сохранить данные в базе данных](../data-tools/save-data-back-to-the-database.md) и [обновления данных с помощью адаптера таблицы](../data-tools/update-data-by-using-a-tableadapter.md) .  
  
### <a name="to-update-the-database"></a>Обновление базы данных  
  
1.  Вызовите метод <xref:System.Windows.Forms.BindingSource.EndEdit%2A> объекта <xref:System.Windows.Forms.BindingSource> для элемента управления.  
  
     Объект <xref:System.Windows.Forms.BindingSource> создается автоматически при добавлении элемента управления с привязкой к данным в документ или книгу во время разработки. Объект <xref:System.Windows.Forms.BindingSource> подключает элемент управления к типизированному набору данных. Дополнительные сведения см. в разделе [Общие сведения о компоненте BindingSource](/dotnet/framework/winforms/controls/bindingsource-component-overview).  
  
     В следующем примере кода предполагается, что проект содержит <xref:System.Windows.Forms.BindingSource> с именем `customersBindingSource`.  
  
     [!code-csharp[Trin_VstcoreDataExcel#20](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#20)]
     [!code-vb[Trin_VstcoreDataExcel#20](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#20)]  
  
2.  Вызовите `Update` метод созданного адаптера таблицы в проекте.  
  
     Адаптер таблицы автоматически создается при добавлении элемента управления с привязкой к данным в документ или книгу во время разработки. Адаптер таблицы подключается типизированный набор данных в проекте базы данных. Дополнительные сведения см. в разделе [Общие сведения о TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md#tableadapter-overview).  
  
     В следующем примере кода предполагается, что имеется подключение к таблице Customers в базе данных Northwind и проект содержит адаптера таблицы с именем `customersTableAdapter` и типизированный набор данных с именем `northwindDataSet`.  
  
     [!code-csharp[Trin_VstcoreDataExcel#21](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#21)]
     [!code-vb[Trin_VstcoreDataExcel#21](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#21)]  
  
## <a name="see-also"></a>См. также  
 [Привязка данных к элементам управления в решениях Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Сохранить данные в базе данных](../data-tools/save-data-back-to-the-database.md)    
 [Обновление данных с помощью адаптера таблицы](../data-tools/update-data-by-using-a-tableadapter.md)    
 [Как: прокрутка записей базы данных на листе](../vsto/how-to-scroll-through-database-records-in-a-worksheet.md)   
 [Как: заполнение листов данными из базы данных](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)   
 [Как: Заполнение документов данными из объектов](../vsto/how-to-populate-documents-with-data-from-objects.md)   
 [Как: Заполнение документов данными из базы данных](../vsto/how-to-populate-documents-with-data-from-a-database.md)   
 [Как: Заполнение документов данными из служб](../vsto/how-to-populate-documents-with-data-from-services.md)  
  
  