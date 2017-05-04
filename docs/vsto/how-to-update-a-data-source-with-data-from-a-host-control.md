---
title: "Практическое руководство. Обновление источника данных с помощью данных из элемента управления ведущего приложения | Microsoft Docs"
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
  - "документы [разработка решений Office в Visual Studio], обновления источников данных"
  - "данные [разработка решений Office в Visual Studio], обновление источника данных из документа"
  - "элементы управления [разработка решений Office в Visual Studio], обновления источников данных"
  - "документы Office [разработка решений Office в Visual Studio], источники данных"
ms.assetid: b91025af-1eaa-44ee-88f2-71ecaa7a0440
caps.latest.revision: 53
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 52
---
# Практическое руководство. Обновление источника данных с помощью данных из элемента управления ведущего приложения
  Вы можете привязать элемент управления ведущего приложения к источнику данных и обновлять источник данных с помощью изменений, внесенных в данные в элементе управления. Этот процесс включает два основных этапа.  
  
1.  Обновление источника данных в памяти с использованием измененных данных в элементе управления. Как правило, источник данных в памяти — это <xref:System.Data.DataSet>, <xref:System.Data.DataTable> или какой\-либо другой объект данных.  
  
2.  Обновление базы данных с использованием измененных данных в источнике данных в памяти. Это применимо только в том случае, если источник данных подключен к внутренней базе данных, например к базе данных SQL Server или Microsoft Office Access.  
  
 Дополнительные сведения об элементах управления ведущего приложения и привязке данных см. в разделах [Общие сведения о ведущих элементах и элементах управления ведущего приложения](../vsto/host-items-and-host-controls-overview.md) и [Привязка данных к элементам управления в решениях Office](../vsto/binding-data-to-controls-in-office-solutions.md).  
  
 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]  
  
## Обновление источника данных в памяти  
 По умолчанию элементы управления ведущего приложения с поддержкой простой привязки данных \(например, элементы управления содержимым в документе Word или элемент управления диапазона на листе Excel\) не сохраняют изменения данных в источнике данных в памяти. То есть когда пользователь изменяет значение в элементе управления ведущего приложения и затем выходит из этого элемента управления, новое значение в элементе управления не сохраняется автоматически в источнике данных.  
  
 Для сохранения данных в источник данных можно написать код, который обновляет источник данных в ответ на определенное событие во время выполнения, или можно настроить элемент управления так, чтобы источник данных обновлялся автоматически при изменении значения в элементе управления.  
  
 Нет необходимости сохранять изменения <xref:Microsoft.Office.Tools.Excel.ListObject> в источнике данных в памяти. При привязке элемента управления <xref:Microsoft.Office.Tools.Excel.ListObject> к данным элемент управления <xref:Microsoft.Office.Tools.Excel.ListObject> автоматически сохраняет изменения в источнике данных в памяти без необходимости написания дополнительного кода.  
  
#### Обновление источника данных в памяти во время выполнения  
  
-   Вызовите метод <xref:System.Windows.Forms.Binding.WriteValue%2A> объекта <xref:System.Windows.Forms.Binding>, который привязывает элемент управления к источнику данных.  
  
     В следующем примере выполняется сохранение изменений, внесенных в элемент управления <xref:Microsoft.Office.Tools.Excel.NamedRange> в листе Excel, в источнике данных. В этом примере предполагается, что имеется элемент управления <xref:Microsoft.Office.Tools.Excel.NamedRange> с именем `namedRange1`, свойство <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> которого привязано к полю в источнике данных.  
  
     [!code-csharp[Trin_VstcoreDataExcel#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet1.cs#1)]
     [!code-vb[Trin_VstcoreDataExcel#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet1.vb#1)]  
  
### Автоматическое обновление источника данных в памяти  
 Вы также можете настроить элемент управления, чтобы он автоматически обновлял источник данных в памяти. В проекте уровня документа это можно сделать с помощью кода или конструктора. В проекте надстройки VSTO необходимо использовать код.  
  
##### Установка автоматического обновления источника данных в памяти элементом управления с помощью кода  
  
1.  Используйте режим System.Windows.Forms.DataSourceUpdateMode.OnPropertyChanged  объекта <xref:System.Windows.Forms.Binding>, который привязывает элемент управления к источнику данных. Обновлять источник данных можно двумя способами.  
  
    -   Для обновления источника данных при проверке элемента управления установите это свойство в значение System.Windows.Forms.DataSourceUpdateMode.OnValidation.  
  
    -   Для обновления источника данных при изменении значения свойства привязки к данным элемента управления установите это свойство в значение System.Windows.Forms.DataSourceUpdateMode.OnPropertyChanged.  
  
        > [!NOTE]  
        >  Способ с System.Windows.Forms.DataSourceUpdateMode.OnPropertyChanged не применяется для элементов управления ведущего приложения Word, поскольку Word не предоставляет уведомления об изменении документа или изменении элемента управления. Однако этот вариант можно использовать для элементов управления Windows Forms в документах Word.  
  
     В следующем примере элемент управления <xref:Microsoft.Office.Tools.Excel.NamedRange> настраивается для автоматического обновления источника данных при изменении значения в этом элементе управления. В этом примере предполагается, что имеется элемент управления <xref:Microsoft.Office.Tools.Excel.NamedRange> с именем `namedRange1`, свойство <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> которого привязано к полю в источнике данных.  
  
     [!code-csharp[Trin_VstcoreDataExcel#19](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet1.cs#19)]
     [!code-vb[Trin_VstcoreDataExcel#19](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet1.vb#19)]  
  
##### Установка автоматического обновления источника данных в памяти элементом управления с помощью конструктора  
  
1.  В Visual Studio откройте документ Word или книгу Excel в конструкторе.  
  
2.  Щелкните элемент управления, который вы хотите настроить для автоматического обновления источника данных.  
  
3.  В окне **Свойства** разверните свойство **\(DataBindings\)**.  
  
4.  Рядом со свойством **\(Дополнительно\)** нажмите кнопку с многоточием \(![Снимок экрана VisualStudioEllipsesButton](../vsto/media/vbellipsesbutton.png "Снимок экрана VisualStudioEllipsesButton")\).  
  
5.  В диалоговом окне **Форматирование и дополнительная привязка** щелкните раскрывающийся список **Режим обновления источника данных** и выберите одно из следующих значений.  
  
    -   Для обновления источника данных при проверке элемента управления выберите значение **OnValidation**.  
  
    -   Для обновления источника данных при изменении значения свойства привязки к данным элемента управления выберите значение **OnPropertyChanged**.  
  
        > [!NOTE]  
        >  Вариант с **OnPropertyChanged** не применяется для элементов управления ведущего приложения Word, поскольку Word не предоставляет уведомления об изменении документа или изменении элемента управления. Однако этот вариант можно использовать для элементов управления Windows Forms в документах Word.  
  
6.  Закройте диалоговое окно **Форматирование и дополнительная привязка**.  
  
## Обновление базы данных  
 Если источник данных в памяти связан с базой данных, необходимо обновить базу данных с использованием изменений в источнике данных. Дополнительные сведения об обновлении базы данных см. в разделах [Сохранение данных в наборах данных](../Topic/Saving%20data%20back%20to%20the%20database.md) и [Практическое руководство. Обновление данных с помощью адаптера таблицы](../data-tools/update-data-by-using-a-tableadapter.md).  
  
#### Обновление базы данных  
  
1.  Вызовите метод <xref:System.Windows.Forms.BindingSource.EndEdit%2A> объекта <xref:System.Windows.Forms.BindingSource> для элемента управления.  
  
     Объект <xref:System.Windows.Forms.BindingSource> создается автоматически при добавлении элемента управления с привязкой к данным в документ или книгу во время разработки. Объект <xref:System.Windows.Forms.BindingSource> подключает элемент управления к типизированному набору данных. Для получения дополнительной информации см. [Общие сведения о компоненте BindingSource](../Topic/BindingSource%20Component%20Overview.md).  
  
     В следующем примере кода предполагается, что проект содержит <xref:System.Windows.Forms.BindingSource> с именем `customersBindingSource`.  
  
     [!code-csharp[Trin_VstcoreDataExcel#20](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet1.cs#20)]
     [!code-vb[Trin_VstcoreDataExcel#20](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet1.vb#20)]  
  
2.  Вызовите метод `Update` созданного объекта TableAdapter в проекте.  
  
     Объект TableAdapter создается автоматически при добавлении элемента управления с привязкой к данным в документ или книгу во время разработки. Объект TableAdapter подключает элемент управления в вашем проекте к базе данных. Дополнительные сведения см. в разделе [Общие сведения об адаптере таблиц](/visual-studio/data-tools/tableadapter-overview).  
  
     В следующем примере кода предполагается, что имеется подключение к таблице Customers в базе данных Northwind, а проект содержит TableAdapter с именем `customersTableAdapter` и типизированный набор данных с именем `northwindDataSet`.  
  
     [!code-csharp[Trin_VstcoreDataExcel#21](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet1.cs#21)]
     [!code-vb[Trin_VstcoreDataExcel#21](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet1.vb#21)]  
  
## См. также  
 [Привязка данных к элементам управления в решениях Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Сохранение данных в наборах данных](../Topic/Saving%20data%20back%20to%20the%20database.md)   
 [Практическое руководство. Обновление данных с помощью адаптера таблицы](../data-tools/update-data-by-using-a-tableadapter.md)   
 [Практическое руководство. Прокрутка записей базы данных на листе](../vsto/how-to-scroll-through-database-records-in-a-worksheet.md)   
 [Практическое руководство. Заполнение листов данными из базы данных](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)   
 [Практическое руководство. Заполнение документов данными из объектов](../vsto/how-to-populate-documents-with-data-from-objects.md)   
 [Практическое руководство. Заполнение документов данными из базы данных](../vsto/how-to-populate-documents-with-data-from-a-database.md)   
 [Практическое руководство. Заполнение документов данными из служб](../vsto/how-to-populate-documents-with-data-from-services.md)  
  
  