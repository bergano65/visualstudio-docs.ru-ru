---
title: Проверка данных в наборах данных | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- DataTable.ColumnChanging
- System.Data.DataTable.ColumnChanging
- System.Data.DataTable.RowChanging
- DataTable.RowChanging
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data validation, datasets
- data validation
- validating data, datasets
- updating datasets, validating data
ms.assetid: 79500596-1e4d-478e-a991-a636fd73a622
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: a85e7b429300ce86290e707bb612d778b8fbb20e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="validate-data-in-datasets"></a>Проверка данных в наборах данных
Проверка данных представляет собой процесс подтверждения того, что значения, вводимые в объекты данных, соответствуют ограничениям в схеме набора данных. Также процесс проверки подтверждает, что эти значения можно выполнять следующие правила, которые были установлены для вашего приложения. Это хороший способ проверить данные перед отправкой обновлений в основную базу данных. Это сокращает ошибки, а также потенциальное количество циклов приема-передачи между приложением и базы данных.  
  
Можно проверить правильность данных, записываемых в набор данных при построении проверку в сам набор данных. Набор данных может проверить данные независимо от того, как выполняется обновление — как непосредственно по элементам управления в форме, в пределах компонента, или иным способом. Поскольку набор данных является частью приложения (в отличие от серверной базы данных), вполне логично будет построить приложения проверок.  
  
Лучше всего подходит для добавления проверки в приложение находится в файле разделяемого класса набора данных. В [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] или [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]откройте **конструктора наборов данных** и дважды щелкните столбец или таблица, для которой требуется создать проверку. Это действие автоматически создает <xref:System.Data.DataTable.ColumnChanging> или <xref:System.Data.DataTable.RowChanging> обработчика событий. 
  
## <a name="validate-data"></a>Проверка данных  
 Проверка в наборе данных можно выполнить одним из следующих способов:  
  
-   Путем создания собственного приложения проверок, проверять значения в отдельных столбцах во время изменения.  Дополнительные сведения см. в разделе [как: проверка данных во время изменения столбцов](validate-data-in-datasets.md).  
  
-   Строки изменяется путем создания собственных проверок конкретного приложения, которые могут проверять данные значений при данных целиком. Дополнительные сведения см. в разделе [как: проверка данных во время изменения строк](validate-data-in-datasets.md).  
  
-   Путем создания ключей, ограничений уникальности и т. д как часть определения действительной схемы набора данных. 
  
-   Задав свойства <xref:System.Data.DataColumn> объектов, таких как <xref:System.Data.DataColumn.MaxLength%2A>, <xref:System.Data.DataColumn.AllowDBNull%2A>, и <xref:System.Data.DataColumn.Unique%2A>.  
  
Несколько событий вызванных <xref:System.Data.DataTable> объекта при внесении изменений в записи:  
  
-   <xref:System.Data.DataTable.ColumnChanging> И <xref:System.Data.DataTable.ColumnChanged> событий во время и после каждого изменения отдельных столбцов. <xref:System.Data.DataTable.ColumnChanging> Событие полезно, когда требуется проверить изменения в отдельных столбцах. Сведения о Предлагаемое изменение передается как аргумент с событием. 
-   <xref:System.Data.DataTable.RowChanging> И <xref:System.Data.DataTable.RowChanged> события вызываются во время и после любого изменения в строке. <xref:System.Data.DataTable.RowChanging> Событие является более общим. Указывает, где происходит изменение в строке, что вы не знаете, какой столбец был изменен.  
  
По умолчанию каждое изменение столбца инициирует четыре события. Во-первых, <xref:System.Data.DataTable.ColumnChanging> и <xref:System.Data.DataTable.ColumnChanged> событий для конкретного столбца, которое необходимо изменить. Далее идут <xref:System.Data.DataTable.RowChanging> и <xref:System.Data.DataTable.RowChanged> события. Если несколько изменения производятся на строку, событий возникает для каждого изменения.  
  
> [!NOTE]
>  Строка данных <xref:System.Data.DataRow.BeginEdit%2A> отключает метод <xref:System.Data.DataTable.RowChanging> и <xref:System.Data.DataTable.RowChanged> события, произошедшие после каждого изменения отдельных столбцов. В этом случае событие не инициируется до <xref:System.Data.DataRow.EndEdit%2A> метод был вызван, когда <xref:System.Data.DataTable.RowChanging> и <xref:System.Data.DataTable.RowChanged> события вызываются только один раз. Дополнительные сведения см. в разделе [отключения ограничений при заполнении набора данных](../data-tools/turn-off-constraints-while-filling-a-dataset.md).  
  
Выбор события в зависимости от того, насколько детальным проверки. Если важно перехватить ошибку непосредственно при изменении столбца, построить проверку с помощью <xref:System.Data.DataTable.ColumnChanging> событий. В противном случае используйте <xref:System.Data.DataTable.RowChanging> событие, которое может перехватывать сразу несколько ошибок. Кроме того, если данные структурированы так, что значение одного столбца проверяется на основе содержимого другого столбца, затем выполните проверку во время <xref:System.Data.DataTable.RowChanging> событий.
  
При обновлении записей, <xref:System.Data.DataTable> объект инициирует события, которые могут реагировать на как появляются изменения, и после внесения изменений.  
  
Если приложение использует типизированный набор данных, можно создать обработчики событий со строгим типом. При этом будет добавлено четыре дополнительных типизированных события, которые можно создать обработчики: `dataTableNameRowChanging`, `dataTableNameRowChanged`, `dataTableNameRowDeleting`, и `dataTableNameRowDeleted`. Эти обработчики типизированных событий передают аргумент, который включает имена столбцов таблицы, которые упрощают код для записи и чтения.  
  
## <a name="data-update-events"></a>События обновления данных  
  
|событие|Описание|  
|-----------|-----------------|  
|<xref:System.Data.DataTable.ColumnChanging>|Изменяется значение в столбце. Событие передает строк и столбцов, а также предложенное новое значение.|  
|<xref:System.Data.DataTable.ColumnChanged>|Было изменено значение в столбце. Событие передает строк и столбцов, а также предложенное значение.|  
|<xref:System.Data.DataTable.RowChanging>|Изменения, внесенные в <xref:System.Data.DataRow> объекта должны быть зафиксированы в наборе данных. Если вы не вызвали <xref:System.Data.DataRow.BeginEdit%2A> метода <xref:System.Data.DataTable.RowChanging> событие вызывается для каждого изменения в столбце сразу после <xref:System.Data.DataTable.ColumnChanging> события. Если вызван <xref:System.Data.DataRow.BeginEdit%2A> перед внесением изменений, <xref:System.Data.DataTable.RowChanging> событие возникает только при вызове <xref:System.Data.DataRow.EndEdit%2A> метода.<br /><br /> Событие передает строку, и значение, указывающее, какой тип действия (изменения, вставки и т. д) выполняется.|  
|<xref:System.Data.DataTable.RowChanged>|Изменения строки. Событие передает строку, и значение, указывающее, какой тип действия (изменения, вставки и т. д) выполняется.|  
|<xref:System.Data.DataTable.RowDeleting>|Удаляется строка. Событие передает строку, и значение, указывающее, какой тип действия (delete) выполняется.|  
|<xref:System.Data.DataTable.RowDeleted>|Строка была удалена. Событие передает строку, и значение, указывающее, какой тип действия (delete) выполняется.|  
  
<xref:System.Data.DataTable.ColumnChanging>, <xref:System.Data.DataTable.RowChanging>, И <xref:System.Data.DataTable.RowDeleting> событий во время обновления. Эти события можно использовать для проверки данных или выполнения других операций обработки. Поскольку обновление находится в процессе во время этих событий, его можно отменить, создавая исключение, что предотвращает обновление из завершения.  
  
<xref:System.Data.DataTable.ColumnChanged>, <xref:System.Data.DataTable.RowChanged> И <xref:System.Data.DataTable.RowDeleted> события, события уведомления, возникающим, когда обновление успешно завершено. Эти события полезны в тех случаях, когда требуется выполнить дополнительные действия в успешное обновление.  
  
## <a name="validate-data-during-column-changes"></a>Проверка данных в ходе изменения столбцов  
  
> [!NOTE]
>  **Конструктора наборов данных** создает разделяемый класс, в какие проверки логику можно добавить в набор данных. Набор данных, автоматически созданный конструктором не удалить или изменить любой код в разделяемый класс.  
  
Вы можете проверять данные при изменении значения в столбце данных, реагируя на <xref:System.Data.DataTable.ColumnChanging> событий. При возникновении это событие передает аргумент события (<xref:System.Data.DataColumnChangeEventArgs.ProposedValue%2A>), содержащий значение, которое предлагается для текущего столбца. Зависимости от содержимого `e.ProposedValue`, вы можете:  
  
-   Примите предложенное значение, не выполняя никаких действий.  
  
-   Отклонить предложенное значение, задав ошибку столбца (<xref:System.Data.DataRow.SetColumnError%2A>) из обработчика событий изменения столбца.  
  
-   При необходимости использовать <xref:System.Windows.Forms.ErrorProvider> управления, чтобы отобразить сообщение об ошибке для пользователя. Дополнительные сведения см. в разделе [компонент ErrorProvider](/dotnet/framework/winforms/controls/errorprovider-component-windows-forms).  
  
Можно также выполнять во время проверки <xref:System.Data.DataTable.RowChanging> событий. 
  
## <a name="validate-data-during-row-changes"></a>Проверка данных в ходе изменения строк  
Можно написать код, чтобы убедиться, что для каждого столбца, который нужно проверить содержит данные, которые удовлетворяют требованиям приложения. Для этого необходимо задать столбец для указания, что он содержит ошибку, если предложенное значение является недопустимым. В следующем примере задается ошибка столбца при `Quantity` столбца меньше или равно 0. Обработчики событий изменения строк должны напоминать следующие примеры.  
  
#### <a name="to-validate-data-when-a-row-changes-visual-basic"></a>Для проверки данных при изменении строки изменяется (Visual Basic)  
  
1.  Откройте свой набор данных в **конструктора наборов данных**. Дополнительные сведения см. в разделе [Пошаговое руководство: Создание набора данных в конструкторе наборов данных](walkthrough-creating-a-dataset-with-the-dataset-designer.md).  
  
2.  Дважды щелкните заголовок таблицы, которую требуется проверить. Это действие автоматически создает <xref:System.Data.DataTable.RowChanging> обработчик событий <xref:System.Data.DataTable> в файле разделяемого класса набора данных.  
  
    > [!TIP]
    >  Дважды щелкните значок слева от имени таблицы для создания обработчика событий изменения строки. Если дважды щелкнуть имя таблицы, его можно изменить.  
  
     [!code-vb[VbRaddataValidating#3](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_1.vb)]  
  
#### <a name="to-validate-data-when-a-row-changes-c"></a>Для проверки данных при изменении строки (C#)  
  
1.  Откройте свой набор данных в **конструктора наборов данных**. Дополнительные сведения см. в разделе [Пошаговое руководство: Создание набора данных в конструкторе наборов данных](walkthrough-creating-a-dataset-with-the-dataset-designer.md).  
  
2.  Дважды щелкните заголовок таблицы, которую требуется проверить. Это действие создает файл разделяемого класса для <xref:System.Data.DataTable>.  
  
    > [!NOTE]
    >  **Конструктора наборов данных** не создает автоматически обработчик событий для <xref:System.Data.DataTable.RowChanging> события. Необходимо создать метод для обработки <xref:System.Data.DataTable.RowChanging> событий и выполнять код подключить событие в методе инициализации таблицы.  
  
3.  Скопируйте следующий код в разделяемый класс:  
  
    ```csharp  
    public override void EndInit()  
    {  
        base.EndInit();  
        Order_DetailsRowChanging += TestRowChangeEvent;  
    }  
  
    public void TestRowChangeEvent(object sender, Order_DetailsRowChangeEvent e)  
    {  
        if ((short)e.Row.Quantity <= 0)  
        {  
            e.Row.SetColumnError("Quantity", "Quantity must be greater than 0");  
        }  
        else  
        {  
            e.Row.SetColumnError("Quantity", "");  
        }  
    }  
    ```  
  
## <a name="to-retrieve-changed-rows"></a>Для получения измененных строк  
Каждая строка в таблице данных имеет <xref:System.Data.DataRow.RowState%2A> свойство, которое отслеживает текущее состояние этой строки, используя значения в <xref:System.Data.DataRowState> перечисления. Можно вернуть измененные строки из набора данных или таблицы данных путем вызова `GetChanges` метод <xref:System.Data.DataSet> или <xref:System.Data.DataTable>. Убедитесь, что существуют изменения до вызова метода `GetChanges` путем вызова <xref:System.Data.DataSet.HasChanges%2A> метод набора данных. 
  
> [!NOTE]
>  После фиксации изменений в таблицу набора данных или данных (путем вызова <xref:System.Data.DataSet.AcceptChanges%2A> метод), `GetChanges` метод не возвращает никаких данных. Если приложению нужно обработать измененные строки, необходимо обработать изменения перед вызовом `AcceptChanges` метод.  
  
Вызов <xref:System.Data.DataSet.GetChanges%2A> метод набора данных или таблицы данных возвращает новый набор данных или данных таблицы, содержащей только записи, которые были изменены. Если вы хотите получить определенные записи — например, только новые записи или только измененные записи — можно передать значение из <xref:System.Data.DataRowState> перечисления в качестве параметра `GetChanges` метод.  
  
Используйте <xref:System.Data.DataRowVersion> перечисления для доступа к другой версии строки (например, исходные значения, которые были в строке до ее обработки).  
  
#### <a name="to-get-all-changed-records-from-a-dataset"></a>Чтобы получить все измененные записи из набора данных  
  
-   Вызовите <xref:System.Data.DataSet.GetChanges%2A> метод набора данных.  
  
     В следующем примере создается новый набор данных с именем `changedRecords` и заполняет все измененные записи из другого набора данных `dataSet1`.  
  
     [!code-csharp[VbRaddataEditing#14](../data-tools/codesnippet/CSharp/validate-data-in-datasets_2.cs)]
     [!code-vb[VbRaddataEditing#14](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_2.vb)]  
  
#### <a name="to-get-all-changed-records-from-a-data-table"></a>Чтобы получить все измененные записи из таблицы данных  
  
-   Вызовите <xref:System.Data.DataTable.GetChanges%2A> метод объекта DataTable.  
  
     В следующем примере создается новая таблица данных с именем `changedRecordsTable` и заполняет все измененные записи из другой таблицы данных с именем `dataTable1`.  
  
     [!code-csharp[VbRaddataEditing#15](../data-tools/codesnippet/CSharp/validate-data-in-datasets_3.cs)]
     [!code-vb[VbRaddataEditing#15](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_3.vb)]  
  
#### <a name="to-get-all-records-that-have-a-specific-row-state"></a>Чтобы получить все записи, имеющие определенное состояние строки  
  
-   Вызовите `GetChanges` метод набора данных или таблицы данных и передайте <xref:System.Data.DataRowState> значение перечисления в качестве аргумента.  
  
     В следующем примере показано, как создать новый набор данных с именем `addedRecords` и заполнить ее только записи, которые были добавлены к `dataSet1` набора данных.  
  
     [!code-csharp[VbRaddataEditing#16](../data-tools/codesnippet/CSharp/validate-data-in-datasets_4.cs)]
     [!code-vb[VbRaddataEditing#16](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_4.vb)]  
  
     В следующем примере показано, как для возвращения всех записей, которые были недавно добавлены в `Customers` таблице:  
  
     [!code-csharp[VbRaddataEditing#17](../data-tools/codesnippet/CSharp/validate-data-in-datasets_5.cs)]
     [!code-vb[VbRaddataEditing#17](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_5.vb)]  
  
## <a name="access-the-original-version-of-a-datarow"></a>Доступ к исходной версии DataRow  
При внесении изменений в строки данных набор данных сохраняет исходные (<xref:System.Data.DataRowVersion.Original>) и новые (<xref:System.Data.DataRowVersion.Current>) версии строки. Например, перед вызовом `AcceptChanges` метода, приложение может получить доступ к различных версий записи (как определено в <xref:System.Data.DataRowVersion> перечисления) и соответствующим образом обрабатывать изменения.  
  
> [!NOTE]
>  Существуют различные версии строки, только после его изменения и перед его `AcceptChanges` был вызван метод. После `AcceptChanges` вызова метода, текущую и первоначальную версию совпадают.  
  
Передача <xref:System.Data.DataRowVersion> значение вместе с индексом столбца (или имя столбца в виде строки) возвращает значение от версии отдельной строки этого столбца. Измененный столбец определяется во время <xref:System.Data.DataTable.ColumnChanging> и <xref:System.Data.DataTable.ColumnChanged> события. Это подходящий момент, чтобы проверить различные версии строк для целей проверки. Если есть временно приостановленные ограничения, эти события не будут создаваться и необходимо программно Определите столбцы, которые были изменены. Это можно сделать с помощью итерации <xref:System.Data.DataTable.Columns%2A> коллекции и сравнения различных <xref:System.Data.DataRowVersion> значений.  
  
#### <a name="to-get-the-original-version-of-a-record"></a>Для получения исходной версии записи  
  
-   Доступ к значению столбца, передав ему <xref:System.Data.DataRowVersion> строки, которые необходимо вернуть.  
  
     В следующем примере показано, как использовать <xref:System.Data.DataRowVersion> значение для получения исходного значения `CompanyName` в <xref:System.Data.DataRow>:  
  
     [!code-csharp[VbRaddataEditing#21](../data-tools/codesnippet/CSharp/validate-data-in-datasets_6.cs)]
     [!code-vb[VbRaddataEditing#21](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_6.vb)]  
  
## <a name="access-the-current-version-of-a-datarow"></a>Доступ к текущей версии DataRow  
  
#### <a name="to-get-the-current-version-of-a-record"></a>Для получения текущей версии записи  
  
-   Доступ к значению столбца, а затем добавьте параметр в индекс, который указывает, какая версия строки необходимо вернуть.  
  
     В следующем примере показано, как использовать <xref:System.Data.DataRowVersion> значение, возвращаемое значение текущей `CompanyName` в <xref:System.Data.DataRow>:  
  
     [!code-csharp[VbRaddataEditing#22](../data-tools/codesnippet/CSharp/validate-data-in-datasets_7.cs)]
     [!code-vb[VbRaddataEditing#22](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_7.vb)]  
  
## <a name="see-also"></a>См. также
[Инструменты для работы с наборами данных в Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)  
[Как: проверка данных в элементе управления DataGridView Windows Forms](/dotnet/framework/winforms/controls/how-to-validate-data-in-the-windows-forms-datagridview-control)   
[Практическое руководство. Отображение значков ошибок при проверке введенных в форму данных с помощью компонента ErrorProvider в Windows Forms](/dotnet/framework/winforms/controls/display-error-icons-for-form-validation-with-wf-errorprovider)