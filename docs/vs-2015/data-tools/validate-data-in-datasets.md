---
title: Проверка данных в наборах данных | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
f1_keywords:
- DataTable.ColumnChanging
- System.Data.DataTable.ColumnChanging
- System.Data.DataTable.RowChanging
- DataTable.RowChanging
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data validation, datasets
- data validation
- validating data, datasets
- updating datasets, validating data
ms.assetid: 79500596-1e4d-478e-a991-a636fd73a622
caps.latest.revision: 27
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 1740e9d7668101911862c91457a2c81c48f7b72d
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58992864"
---
# <a name="validate-data-in-datasets"></a>Проверка данных в наборах данных
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Проверка данных представляет собой процесс подтверждения того, что значения, вводимые в объекты данных, соответствуют ограничениям в схеме набора данных. Процесс проверки также подтверждает, что эти значения приведены ниже правила, которые были определены для вашего приложения. Рекомендуется проверить данные перед отправкой обновлений в основную базу данных. Это уменьшает ошибки, а также потенциальное количество циклов обработки между приложением и базе данных.  
  
 Можно подтвердить правильность данных, записываемых в набор данных, создав проверки допустимости в сам набор данных. Набор данных может проверить данные независимо от того, как выполняется обновление — как непосредственно по элементам управления в форме, в пределах компонента, или иным способом. Так как набор данных является частью приложения (в отличие от серверной части базы данных), это логичным местом для построения приложения проверок.  
  
 Лучшее место для добавления проверки в приложение находится в разделяемом классе файла набора данных. В [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] или [!INCLUDE[csprcs](../includes/csprcs-md.md)]откройте **конструктор наборов данных** и дважды щелкните столбец или таблица, для которого вы хотите создать проверку. Это действие автоматически создает <xref:System.Data.DataTable.ColumnChanging> или <xref:System.Data.DataTable.RowChanging> обработчик событий. Дополнительные сведения см. в разделе [Как Проверка данных в ходе изменения столбцов](http://msdn.microsoft.com/library/a2680600-67b6-4a40-a77e-b5bc638281c5) или [как: Проверка данных в ходе изменения строк](http://msdn.microsoft.com/library/afc03c77-dfed-4302-9376-929400468ecc). Полный пример см. в разделе [Пошаговое руководство: Добавление проверки к набору данных](http://msdn.microsoft.com/library/09351fab-d670-45e3-b53a-a944eff717e7).  
  
## <a name="validate-data"></a>Проверка данных  
 Проверки в объекте dataset, можно выполнить одним из следующих способов:  
  
- Путем создания собственных проверок конкретного приложения, можно проверить значения в отдельных столбцах во время изменения.  Дополнительные сведения см. в разделе [Как Проверка данных в ходе изменения столбцов](http://msdn.microsoft.com/library/a2680600-67b6-4a40-a77e-b5bc638281c5).  
  
- Путем создания собственных проверок конкретного приложения, которые могут проверять данные значений при данных целиком изменении строки. Дополнительные сведения см. в разделе [Как Проверка данных в ходе изменения строк](http://msdn.microsoft.com/library/afc03c77-dfed-4302-9376-929400468ecc).  
  
- Как часть определения действительной схемы набора данных, создав ключи, ограничения уникальности, и т. д. Дополнительные сведения о включении проверки в определение схемы, см. в разделе [ограничение DataColumn, чтобы содержать уникальные значения](http://msdn.microsoft.com/library/8ca21f77-b99a-47a7-a656-7cfd7a1bd9df).  
  
- Задав свойства <xref:System.Data.DataColumn> объекта, такие как <xref:System.Data.DataColumn.MaxLength%2A>, <xref:System.Data.DataColumn.AllowDBNull%2A>, и <xref:System.Data.DataColumn.Unique%2A>.  
  
  Несколько событий, вызываемых <xref:System.Data.DataTable> объекта при внесении изменений в записи:  
  
- <xref:System.Data.DataTable.ColumnChanging> И <xref:System.Data.DataTable.ColumnChanged> события вызываются во время и после каждого изменения отдельных столбцов. <xref:System.Data.DataTable.ColumnChanging> Событие полезно, если вы хотите проверить изменения в отдельных столбцах. Сведения о предлагаемом изменении передается как аргумент с событием. Дополнительные сведения см. в разделе [Как Проверка данных в ходе изменения столбцов](http://msdn.microsoft.com/library/a2680600-67b6-4a40-a77e-b5bc638281c5).  
  
- <xref:System.Data.DataTable.RowChanging> И <xref:System.Data.DataTable.RowChanged> события вызываются во время и после любых изменений в строке. <xref:System.Data.DataTable.RowChanging> Событие является более общим. Он указывает, где происходит изменение в строке, что вы не знаете, какой столбец был изменен. Дополнительные сведения см. в разделе [Как Проверка данных в ходе изменения строк](http://msdn.microsoft.com/library/afc03c77-dfed-4302-9376-929400468ecc).  
  
  По умолчанию каждое изменение столбцом инициирует четыре события. Во-первых, <xref:System.Data.DataTable.ColumnChanging> и <xref:System.Data.DataTable.ColumnChanged> события для конкретного столбца, которое необходимо изменить. Далее идут <xref:System.Data.DataTable.RowChanging> и <xref:System.Data.DataTable.RowChanged> события. Если несколько изменения вносятся в строку, событий возникает для каждого изменения.  
  
> [!NOTE]
>  Строки данных <xref:System.Data.DataRow.BeginEdit%2A> метод приводит к отключению <xref:System.Data.DataTable.RowChanging> и <xref:System.Data.DataTable.RowChanged> события после каждого изменения отдельных столбцов. В этом случае событие не инициируется до <xref:System.Data.DataRow.EndEdit%2A> метод был вызван, когда <xref:System.Data.DataTable.RowChanging> и <xref:System.Data.DataTable.RowChanged> событий только один раз. Дополнительные сведения см. в разделе [отключение ограничений при заполнении набора данных](../data-tools/turn-off-constraints-while-filling-a-dataset.md).  
  
 Выбор события зависит от того, насколько детальным необходимо проверки. Если важно перехватить ошибку сразу же при изменении столбца, проверкой сборки с помощью <xref:System.Data.DataTable.ColumnChanging> событий. В противном случае используйте <xref:System.Data.DataTable.RowChanging> событие, которое может перехватывать сразу несколько ошибок. Кроме того, если данные структурированы, чтобы проверки значения одного столбца на основе содержимого другого столбца, затем выполните проверку во время <xref:System.Data.DataTable.RowChanging> событий.  
  
 При обновлении записей, <xref:System.Data.DataTable> объект инициирует события, которые можно ответить на как появляются изменения, и после внесения изменений.  
  
 Если приложение использует типизированный набор данных, можно создать строго типизированные обработчики событий. Это добавит четыре дополнительных типизированных события, которые можно создать обработчики для: `dataTableNameRowChanging`, `dataTableNameRowChanged`, `dataTableNameRowDeleting`, и `dataTableNameRowDeleted`. Эти обработчики событий типизированный передать аргумент, который включает имена столбцов таблицы, которые упрощают код для записи и чтения.  
  
## <a name="data-update-events"></a>События обновления данных  
  
|событие|Описание|  
|-----------|-----------------|  
|<xref:System.Data.DataTable.ColumnChanging>|Изменяется значение в столбце. Событие передает строк и столбцов, а также предложенное новое значение.|  
|<xref:System.Data.DataTable.ColumnChanged>|Значение в столбце было изменено. Событие передает строк и столбцов, а также предложенное значение.|  
|<xref:System.Data.DataTable.RowChanging>|Изменения, внесенные в <xref:System.Data.DataRow> объекта должны быть зафиксированы в наборе данных. Если не был вызван <xref:System.Data.DataRow.BeginEdit%2A> метод, <xref:System.Data.DataTable.RowChanging> событие вызывается для каждого изменения столбец сразу после <xref:System.Data.DataTable.ColumnChanging> события. Если вызван <xref:System.Data.DataRow.BeginEdit%2A> перед внесением изменений, <xref:System.Data.DataTable.RowChanging> события только в том случае, когда вы вызываете <xref:System.Data.DataRow.EndEdit%2A> метод.<br /><br /> Событие передает строку, а также значение, указывающее, какой тип действия (изменения, вставки и т. д.) выполняется.|  
|<xref:System.Data.DataTable.RowChanged>|Строка изменялась. Событие передает строку, а также значение, указывающее, какой тип действия (изменения, вставки и т. д.) выполняется.|  
|<xref:System.Data.DataTable.RowDeleting>|Удаляется строка. Событие передает строку, а также значение, указывающее, какой тип действия (delete) выполняется.|  
|<xref:System.Data.DataTable.RowDeleted>|Строка была удалена. Событие передает строку, а также значение, указывающее, какой тип действия (delete) выполняется.|  
  
 <xref:System.Data.DataTable.ColumnChanging>, <xref:System.Data.DataTable.RowChanging>, И <xref:System.Data.DataTable.RowDeleting> событий во время обновления. Эти события можно использовать для проверки данных или выполнять другие виды обработки. Так как обновление выполняется во время этих событий, отмените его путем создания исключения, что предотвращает обновление завершение.  
  
 <xref:System.Data.DataTable.ColumnChanged>, <xref:System.Data.DataTable.RowChanged> И <xref:System.Data.DataTable.RowDeleted> события, события уведомления, возникающим, когда обновление успешно завершено. Эти события полезны в тех случаях, когда требуется предпринять дальнейшие действия на основе успешного обновления.  
  
## <a name="validate-data-during-column-changes"></a>Проверка данных в ходе изменения столбцов  
  
> [!NOTE]
>  **Конструктор наборов данных** создает разделяемый класс, в какие проверки логику можно добавить к набору данных. Набор данных созданного конструктором не удалить или изменить любой код в разделяемом классе.  
  
 Можно проверять данные при изменении значения в столбце данных, отвечая на <xref:System.Data.DataTable.ColumnChanging> событий. При возникновении это событие передает аргумент события (<xref:System.Data.DataColumnChangeEventArgs.ProposedValue%2A>), содержащий значение, предлагаемых для текущего столбца. На основе содержимого из `e.ProposedValue`, вы можете:  
  
- Примите предложенное значение, ничего делать не требуется.  
  
- Отклонить предложенное значение, задав ошибку столбца (<xref:System.Data.DataRow.SetColumnError%2A>) из обработчика событий изменения столбца.  
  
- При необходимости использовать <xref:System.Windows.Forms.ErrorProvider> управления для отображения сообщения об ошибке для пользователя. Дополнительные сведения см. в разделе [компонент ErrorProvider](http://msdn.microsoft.com/library/c0f2e231-c5c9-413d-a507-75af2db499b6).  
  
  Также можно выполнить проверку во время <xref:System.Data.DataTable.RowChanging> событий. Дополнительные сведения см. в разделе [Как Проверка данных в ходе изменения строк](http://msdn.microsoft.com/library/afc03c77-dfed-4302-9376-929400468ecc).  
  
## <a name="validate-data-during-row-changes"></a>Проверка данных в ходе изменения строк  
 Можно написать код, чтобы убедиться, что каждый столбец, который вы хотите проверить содержит данные, которые удовлетворяют требованиям приложения. Для этого путем присвоения столбцу, чтобы указать, что он содержит ошибку, если предложенное значение является недопустимым. В следующем примере задается ошибка столбца при `Quantity` столбца меньше или равно 0. Обработчики событий изменения строки должно выглядеть как в приведенных ниже примерах.  
  
#### <a name="to-validate-data-when-a-row-changes-visual-basic"></a>Проверка данных при изменении строки изменяется (Visual Basic)  
  
1.  Откройте свой набор данных в **Конструкторе наборов данных**. Дополнительные сведения см. в разделе [Как Откройте набор данных в конструкторе наборов данных](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).  
  
2.  Дважды щелкните заголовок таблицы, которую вы хотите проверить. Это действие автоматически создает <xref:System.Data.DataTable.RowChanging> обработчик событий <xref:System.Data.DataTable> в файле разделяемого класса набора данных.  
  
    > [!TIP]
    >  Дважды щелкните слева от имени таблицы, чтобы создать обработчик событий изменения строки. Если дважды щелкнуть имя таблицы, его можно изменить.  
  
     [!code-vb[VbRaddataValidating#3](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataValidating/VB/NorthwindDataSet.vb#3)]  
  
#### <a name="to-validate-data-when-a-row-changes-c"></a>Проверка данных при изменении строки (C#)  
  
1.  Откройте свой набор данных в **Конструкторе наборов данных**. Дополнительные сведения см. в разделе [Как Откройте набор данных в конструкторе наборов данных](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).  
  
2.  Дважды щелкните заголовок таблицы, которую вы хотите проверить. Это действие создает файл разделяемого класса для <xref:System.Data.DataTable>.  
  
    > [!NOTE]
    >  **Конструктор наборов данных** не создает автоматически обработчик событий для <xref:System.Data.DataTable.RowChanging> событий. Необходимо создать метод для обработки <xref:System.Data.DataTable.RowChanging> событие, а также выполнения код, чтобы подключить событие в методе инициализации таблицы.  
  
3.  Скопируйте следующий код в разделяемый класс:  
  
    ```  
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
 Каждая строка в таблице данных имеет <xref:System.Data.DataRow.RowState%2A> свойство, которое отслеживает текущее состояние этой строки, используя значения в <xref:System.Data.DataRowState> перечисления. Может возвращать измененных строк из таблицы набора данных или данных, вызвав `GetChanges` метод <xref:System.Data.DataSet> или <xref:System.Data.DataTable>. Убедитесь, что существуют изменения, перед вызовом метода `GetChanges` путем вызова <xref:System.Data.DataSet.HasChanges%2A> метод набора данных. Дополнительные сведения об использовании <xref:System.Data.DataSet.HasChanges%2A> см. в разделе [Практическое руководство. Проверка измененных строк](http://msdn.microsoft.com/library/af160d20-472b-4c13-8f15-75480c39a653).  
  
> [!NOTE]
>  После фиксации изменений в таблицу данных или набора данных (путем вызова <xref:System.Data.DataSet.AcceptChanges%2A> метод), `GetChanges` метод не возвращает никаких данных. Если приложению для обработки измененных строк, необходимо обработать изменения перед вызовом `AcceptChanges` метод.  
  
 Вызов <xref:System.Data.DataSet.GetChanges%2A> метод таблицы набора данных или данных возвращает новую таблицу данных или набора данных, которая содержит только записи, которые были изменены. Если вы хотите получить определенные записи — например, только новые записи или только измененные записи — можно передать значение из <xref:System.Data.DataRowState> перечисления в качестве параметра `GetChanges` метод.  
  
 Используйте <xref:System.Data.DataRowVersion> перечисления для доступа к другой версии строки (например, исходные значения, которые были в строке до его обработки).  
  
#### <a name="to-get-all-changed-records-from-a-dataset"></a>Чтобы получить все измененные записи из набора данных  
  
-   Вызовите <xref:System.Data.DataSet.GetChanges%2A> метод набора данных.  
  
     В следующем примере создается новый набор данных с именем `changedRecords` и заполняет все измененные записи из другой набор данных с именем `dataSet1`.  
  
     [!code-csharp[VbRaddataEditing#14](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#14)]
     [!code-vb[VbRaddataEditing#14](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#14)]  
  
#### <a name="to-get-all-changed-records-from-a-data-table"></a>Чтобы получить все измененные записи из таблицы данных  
  
-   Вызовите <xref:System.Data.DataTable.GetChanges%2A> метод объекта DataTable.  
  
     В следующем примере создается новая таблица данных с именем `changedRecordsTable` и заполняет все измененные записи из другой таблицы данных с именем `dataTable1`.  
  
     [!code-csharp[VbRaddataEditing#15](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#15)]
     [!code-vb[VbRaddataEditing#15](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#15)]  
  
#### <a name="to-get-all-records-that-have-a-specific-row-state"></a>Чтобы получить все записи, имеющие определенное состояние строки  
  
-   Вызовите `GetChanges` метод из набора данных или таблицы данных и передайте <xref:System.Data.DataRowState> значение перечисления в качестве аргумента.  
  
     В следующем примере показано, как создать новый набор данных с именем `addedRecords` и заполнить ее только записи, которые были добавлены `dataSet1` набора данных.  
  
     [!code-csharp[VbRaddataEditing#16](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#16)]
     [!code-vb[VbRaddataEditing#16](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#16)]  
  
-   В следующем примере показано, как вернуть все записи, которые были недавно добавлены в `Customers` таблицы:  
  
     [!code-csharp[VbRaddataEditing#17](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#17)]
     [!code-vb[VbRaddataEditing#17](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#17)]  
  
## <a name="access-the-original-version-of-a-datarow"></a>Доступ к исходной версии DataRow  
 При внесении изменений в строки данных, набора данных сохраняет исходные (<xref:System.Data.DataRowVersion>) и new (<xref:System.Data.DataRowVersion>) версии строки. Например, перед вызовом `AcceptChanges` метод, приложение может получить доступ в разных версиях запись (как определено в <xref:System.Data.DataRowVersion> перечисления) и соответственно обрабатывать изменения.  
  
> [!NOTE]
>  Существуют различные версии строки, только в том случае, после его изменения и до ее `AcceptChanges` был вызван метод. После `AcceptChanges` был вызван метод, текущие и исходные версии ничем не отличаются.  
  
 Передача <xref:System.Data.DataRowVersion> значение вместе с индексом столбца (или имя столбца в виде строки) возвращает значение из версии конкретной строки этого столбца. Измененный столбец определяется во время <xref:System.Data.DataTable.ColumnChanging> и <xref:System.Data.DataTable.ColumnChanged> события. Это хорошая возможность проверить различные версии строк для целей проверки. Тем не менее если ограничения временно приостановлена, эти события не будет вызываться, необходимо программным образом определите, какие столбцы были изменены. Это можно сделать с помощью итерации <xref:System.Data.DataTable.Columns%2A> сбора и сравнения различных <xref:System.Data.DataRowVersion> значения.  
  
#### <a name="to-get-the-original-version-of-a-record"></a>Чтобы просмотреть его исходную версию записи  
  
-   Доступ к значению столбца, передав <xref:System.Data.DataRowVersion> строки, который необходимо вернуть.  
  
     В следующем примере показано, как использовать <xref:System.Data.DataRowVersion> значение, чтобы получить исходное значение `CompanyName` в <xref:System.Data.DataRow>:  
  
     [!code-csharp[VbRaddataEditing#21](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#21)]
     [!code-vb[VbRaddataEditing#21](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#21)]  
  
## <a name="access-the-current-version-of-a-datarow"></a>Доступ к текущей версии DataRow  
  
#### <a name="to-get-the-current-version-of-a-record"></a>Для получения текущей версии записи  
  
-   Доступ к значению столбца, а затем добавьте параметр к индексу, который указывает, какая версия строки необходимо вернуть.  
  
     В следующем примере показано, как использовать <xref:System.Data.DataRowVersion> значение, чтобы получить текущее значение `CompanyName` в <xref:System.Data.DataRow>:  
  
     [!code-csharp[VbRaddataEditing#22](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#22)]
     [!code-vb[VbRaddataEditing#22](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#22)]  
  
## <a name="see-also"></a>См. также

- [Практическое руководство. Проверка данных в элементе управления DataGridView Windows Forms](http://msdn.microsoft.com/library/d10aef35-701e-4a3c-a684-2a2ed1aeaca6)   
- [Практическое руководство. Отображение значков ошибок для проверки формы с помощью компонента ErrorProvider в Windows Forms](http://msdn.microsoft.com/library/3b681a32-9db4-497b-a34b-34980eabee46)