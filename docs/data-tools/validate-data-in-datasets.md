---
title: Проверка данных в наборах данных
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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: ed115e851e9c2291dfc9d00f4bb36f670a7f3e00
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/01/2020
ms.locfileid: "75586072"
---
# <a name="validate-data-in-datasets"></a>Проверка данных в наборах данных
Проверка данных — это процесс подтверждения того, что значения, вводимые в объекты данных, соответствуют ограничениям в схеме набора данных. Процесс проверки также подтверждает, что эти значения относятся к правилам, установленным для приложения. Перед отправкой обновлений в основную базу данных рекомендуется проверять данные. Это сокращает число ошибок, а также потенциальное количество циклов обработки между приложением и базой данных.

Вы можете убедиться, что данные, записываемые в набор данных, являются допустимыми, создавая проверки в самом наборе данных. Набор данных может проверять данные независимо от того, как выполняется обновление — непосредственно с помощью элементов управления в форме, внутри компонента или каким-либо другим способом. Поскольку набор данных является частью приложения (в отличие от серверной части базы данных), это логическое место для создания проверки, зависящей от приложения.

Лучшим местом для добавления проверки в приложение является файл разделяемого класса набора данных. В [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] или [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]откройте **Конструктор наборов данных** и дважды щелкните столбец или таблицу, для которых необходимо создать проверку. Это действие автоматически создает <xref:System.Data.DataTable.ColumnChanging> или <xref:System.Data.DataTable.RowChanging> обработчик событий.

## <a name="validate-data"></a>Проверка данных
Проверка в наборе данных выполняется следующим образом.

- Путем создания собственной проверки для конкретного приложения, которая может проверять значения в отдельном столбце данных во время внесения изменений. Дополнительные сведения см. [в разделе инструкции. Проверка данных при изменении столбцов](validate-data-in-datasets.md).

- Путем создания собственной проверки для конкретного приложения, которая может проверять данные на значения во время изменения всей строки данных. Дополнительные сведения см. [в разделе как проверить данные при изменении строк](validate-data-in-datasets.md).

- Путем создания ключей, ограничений UNIQUE и т. д. в рамках фактического определения схемы набора данных.

- Путем задания свойств объекта <xref:System.Data.DataColumn>, например <xref:System.Data.DataColumn.MaxLength%2A>, <xref:System.Data.DataColumn.AllowDBNull%2A>и <xref:System.Data.DataColumn.Unique%2A>.

Объект <xref:System.Data.DataTable> вызывает несколько событий при возникновении изменения в записи:

- События <xref:System.Data.DataTable.ColumnChanging> и <xref:System.Data.DataTable.ColumnChanged> возникают во время и после каждого изменения в отдельном столбце. Событие <xref:System.Data.DataTable.ColumnChanging> полезно, если требуется проверить изменения в конкретных столбцах. Сведения о предложенном изменении передаются в качестве аргумента для события.
- События <xref:System.Data.DataTable.RowChanging> и <xref:System.Data.DataTable.RowChanged> вызываются во время и после любого изменения в строке. <xref:System.Data.DataTable.RowChanging> событие является более общим. Оно указывает на то, что в строке происходит изменение, но неизвестно, какой столбец был изменен.

По умолчанию каждое изменение в столбце вызывает четыре события. Первый — это <xref:System.Data.DataTable.ColumnChanging> и <xref:System.Data.DataTable.ColumnChanged> события для конкретного столбца, который изменяется. Далее следует <xref:System.Data.DataTable.RowChanging> и <xref:System.Data.DataTable.RowChanged> события. При внесении нескольких изменений в строку события будут вызываться для каждого изменения.

> [!NOTE]
> Метод <xref:System.Data.DataRow.BeginEdit%2A> строки данных отключает <xref:System.Data.DataTable.RowChanging> и <xref:System.Data.DataTable.RowChanged> события после каждого изменения каждого отдельного столбца. В этом случае событие не вызывается до тех пор, пока не будет вызван метод <xref:System.Data.DataRow.EndEdit%2A>, когда события <xref:System.Data.DataTable.RowChanging> и <xref:System.Data.DataTable.RowChanged> вызываются только один раз. Дополнительные сведения см. в разделе [Отключение ограничений при заполнении набора данных](../data-tools/turn-off-constraints-while-filling-a-dataset.md).

Выбранное событие зависит от того, насколько детализирована проверка. Если важно перехватить ошибку сразу же после изменения столбца, создайте проверку с помощью <xref:System.Data.DataTable.ColumnChanging> события. В противном случае используйте событие <xref:System.Data.DataTable.RowChanging>, которое может привести к перехвату нескольких ошибок одновременно. Кроме того, если данные структурированы таким образом, что значение одного столбца проверяется на основе содержимого другого столбца, выполните проверку во время <xref:System.Data.DataTable.RowChanging> события.

При обновлении записей объект <xref:System.Data.DataTable> создает события, на которые можно реагировать по мере внесения изменений и после внесения изменений.

Если приложение использует типизированный набор данных, можно создать строго типизированные обработчики событий. При этом добавляются четыре дополнительных типизированных события, для которых можно создавать обработчики: `dataTableNameRowChanging`, `dataTableNameRowChanged`, `dataTableNameRowDeleting`и `dataTableNameRowDeleted`. Эти типизированные обработчики событий передают аргумент, включающий имена столбцов таблицы, которые упрощают запись и чтение кода.

## <a name="data-update-events"></a>События обновления данных

|Event|Описание|
|-----------|-----------------|
|<xref:System.Data.DataTable.ColumnChanging>|Значение в столбце изменяется. Событие передает строку и столбец, а также предлагаемое новое значение.|
|<xref:System.Data.DataTable.ColumnChanged>|Значение в столбце изменено. Событие передает строку и столбец, а также предлагаемое значение.|
|<xref:System.Data.DataTable.RowChanging>|Изменения, внесенные в объект <xref:System.Data.DataRow>, будут зафиксированы обратно в набор данных. Если метод <xref:System.Data.DataRow.BeginEdit%2A> не вызывался, событие <xref:System.Data.DataTable.RowChanging> вызывается для каждого изменения в столбце сразу после возникновения события <xref:System.Data.DataTable.ColumnChanging>. Если вы вызывали <xref:System.Data.DataRow.BeginEdit%2A> перед внесением изменений, событие <xref:System.Data.DataTable.RowChanging> возникает только при вызове метода <xref:System.Data.DataRow.EndEdit%2A>.<br /><br /> Событие передает строку пользователю, а также значение, показывающее, какой тип действия (изменение, вставка и т. д.) выполняется.|
|<xref:System.Data.DataTable.RowChanged>|Строка была изменена. Событие передает строку пользователю, а также значение, показывающее, какой тип действия (изменение, вставка и т. д.) выполняется.|
|<xref:System.Data.DataTable.RowDeleting>|Удаляется строка. Событие передает строку вам вместе со значением, указывающим, какой тип действия (Delete) выполняется.|
|<xref:System.Data.DataTable.RowDeleted>|Строка была удалена. Событие передает строку вам вместе со значением, указывающим, какой тип действия (Delete) выполняется.|

События <xref:System.Data.DataTable.ColumnChanging>, <xref:System.Data.DataTable.RowChanging>и <xref:System.Data.DataTable.RowDeleting> создаются во время процесса обновления. Эти события можно использовать для проверки данных или выполнения других типов обработки. Поскольку обновление обрабатывается во время этих событий, его можно отменить, вызывая исключение, которое предотвращает завершение обновления.

События <xref:System.Data.DataTable.ColumnChanged>, <xref:System.Data.DataTable.RowChanged> и <xref:System.Data.DataTable.RowDeleted> — это события уведомления, возникающие при успешном завершении обновления. Эти события полезны, если требуется выполнить дальнейшие действия на основе успешного обновления.

## <a name="validate-data-during-column-changes"></a>Проверять данные при изменении столбцов

> [!NOTE]
> **Конструктор наборов данных** создает разделяемый класс, в котором логика проверки может быть добавлена в набор данных. Созданный конструктором набор данных не удаляет или не изменяет код в разделяемом классе.

Можно проверить данные при изменении значения в столбце данных, отменив ответ на событие <xref:System.Data.DataTable.ColumnChanging>. При возникновении это событие передает аргумент события (<xref:System.Data.DataColumnChangeEventArgs.ProposedValue%2A>), который содержит значение, предлагаемое для текущего столбца. Основываясь на содержимом `e.ProposedValue`, вы можете:

- Примите предложенное значение, не выполняя никаких действий.

- Отклоните предложенное значение, задав ошибку столбца (<xref:System.Data.DataRow.SetColumnError%2A>) в обработчике событий изменения столбца.

- При необходимости используйте элемент управления <xref:System.Windows.Forms.ErrorProvider>, чтобы отобразить сообщение об ошибке для пользователя. Дополнительную информацию см. в разделе [Компонент ErrorProvider](/dotnet/framework/winforms/controls/errorprovider-component-windows-forms).

Проверку также можно выполнить во время <xref:System.Data.DataTable.RowChanging> события.

## <a name="validate-data-during-row-changes"></a>Проверка данных при изменении строк
Можно написать код для проверки того, что каждый столбец, который необходимо проверить, содержит данные, соответствующие требованиям приложения. Это можно сделать, установив столбец, чтобы указать, что он содержит ошибку, если предлагаемое значение недопустимо. В следующих примерах задается ошибка столбца, если столбец `Quantity` имеет значение 0 или меньше. Обработчики событий изменения строк должны быть похожи на следующие примеры.

### <a name="to-validate-data-when-a-row-changes-visual-basic"></a>Проверка данных при изменении строки (Visual Basic)

1. Откройте свой набор данных в **Конструкторе наборов данных**. Дополнительные сведения см. [в разделе Пошаговое руководство. Создание набора данных в конструктор наборов данных](walkthrough-creating-a-dataset-with-the-dataset-designer.md).

2. Дважды щелкните строку заголовка таблицы, которую необходимо проверить. Это действие автоматически создает обработчик <xref:System.Data.DataTable.RowChanging> событий <xref:System.Data.DataTable> в файле разделяемого класса набора данных.

    > [!TIP]
    > Дважды щелкните слева от имени таблицы, чтобы создать обработчик событий изменения строк. Если дважды щелкнуть имя таблицы, его можно изменить.

     [!code-vb[VbRaddataValidating#3](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_1.vb)]

### <a name="to-validate-data-when-a-row-changes-c"></a>Проверка данных при изменении строки (C#)

1. Откройте свой набор данных в **Конструкторе наборов данных**. Дополнительные сведения см. [в разделе Пошаговое руководство. Создание набора данных в конструктор наборов данных](walkthrough-creating-a-dataset-with-the-dataset-designer.md).

2. Дважды щелкните строку заголовка таблицы, которую необходимо проверить. Это действие создает файл разделяемого класса для <xref:System.Data.DataTable>.

    > [!NOTE]
    > **Конструктор наборов данных** не создает автоматически обработчик событий для события <xref:System.Data.DataTable.RowChanging>. Необходимо создать метод для обработки события <xref:System.Data.DataTable.RowChanging> и выполнить код для подключения события в методе инициализации таблицы.

3. Скопируйте следующий код в разделяемый класс:

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

## <a name="to-retrieve-changed-rows"></a>Извлечение измененных строк
Каждая строка в таблице данных имеет свойство <xref:System.Data.DataRow.RowState%2A>, которое отслеживает текущее состояние этой строки с помощью значений перечисления <xref:System.Data.DataRowState>. Вы можете вернуть измененные строки из набора данных или таблицы данных, вызвав метод `GetChanges` <xref:System.Data.DataSet> или <xref:System.Data.DataTable>. Чтобы убедиться, что изменения существуют до вызова `GetChanges`, вызовите метод <xref:System.Data.DataSet.HasChanges%2A> набора данных.

> [!NOTE]
> После фиксации изменений в наборе данных или таблице данных (путем вызова метода <xref:System.Data.DataSet.AcceptChanges%2A>) метод `GetChanges` не возвращает никаких данных. Если приложению необходимо обработать измененные строки, необходимо обработать изменения перед вызовом метода `AcceptChanges`.

Вызов метода <xref:System.Data.DataSet.GetChanges%2A> набора данных или таблицы данных возвращает новый набор данных или таблицу данных, содержащие только измененные записи. Если требуется получить конкретные записи (например, только новые записи или только измененные записи), можно передать значение из перечисления <xref:System.Data.DataRowState> в качестве параметра в метод `GetChanges`.

Используйте перечисление <xref:System.Data.DataRowVersion> для доступа к разным версиям строки (например, исходным значениям, которые были в строке перед обработкой).

### <a name="to-get-all-changed-records-from-a-dataset"></a>Получение всех измененных записей из набора данных

- Вызовите метод <xref:System.Data.DataSet.GetChanges%2A> набора данных.

     В следующем примере создается новый набор данных с именем `changedRecords` и заполняется всеми измененными записями из другого набора данных с именем `dataSet1`.

     [!code-csharp[VbRaddataEditing#14](../data-tools/codesnippet/CSharp/validate-data-in-datasets_2.cs)]
     [!code-vb[VbRaddataEditing#14](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_2.vb)]

### <a name="to-get-all-changed-records-from-a-data-table"></a>Получение всех измененных записей из таблицы данных

- Вызовите метод <xref:System.Data.DataTable.GetChanges%2A> объекта DataTable.

     В следующем примере создается новая таблица данных с именем `changedRecordsTable` и заполняется всеми измененными записями из другой таблицы данных с именем `dataTable1`.

     [!code-csharp[VbRaddataEditing#15](../data-tools/codesnippet/CSharp/validate-data-in-datasets_3.cs)]
     [!code-vb[VbRaddataEditing#15](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_3.vb)]

### <a name="to-get-all-records-that-have-a-specific-row-state"></a>Получение всех записей, имеющих определенное состояние строки

- Вызовите метод `GetChanges` набора данных или таблицы данных и передайте значение перечисления <xref:System.Data.DataRowState> в качестве аргумента.

     В следующем примере показано, как создать новый набор данных с именем `addedRecords` и заполнить его только записями, добавленным в набор данных `dataSet1`.

     [!code-csharp[VbRaddataEditing#16](../data-tools/codesnippet/CSharp/validate-data-in-datasets_4.cs)]
     [!code-vb[VbRaddataEditing#16](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_4.vb)]

     В следующем примере показано, как вернуть все записи, которые были недавно добавлены в таблицу `Customers`:

     [!code-csharp[VbRaddataEditing#17](../data-tools/codesnippet/CSharp/validate-data-in-datasets_5.cs)]
     [!code-vb[VbRaddataEditing#17](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_5.vb)]

## <a name="access-the-original-version-of-a-datarow"></a>Доступ к исходной версии DataRow
При внесении изменений в строки данных набор данных будет хранить как исходную (<xref:System.Data.DataRowVersion.Original>), так и новую (<xref:System.Data.DataRowVersion.Current>) версию строки. Например, перед вызовом метода `AcceptChanges` приложение может получить доступ к различным версиям записи (как определено в перечислении <xref:System.Data.DataRowVersion>) и соответствующим образом обработать изменения.

> [!NOTE]
> Разные версии строки существуют только после редактирования и до вызова метода `AcceptChanges`. После вызова метода `AcceptChanges` текущая и исходная версии будут одинаковыми.

Передача значения <xref:System.Data.DataRowVersion> вместе с индексом столбца (или именем столбца в виде строки) возвращает значение из конкретной версии строки этого столбца. Измененный столбец определяется во время событий <xref:System.Data.DataTable.ColumnChanging> и <xref:System.Data.DataTable.ColumnChanged>. Это хороший момент для проверки различных версий строк в целях тестирования. Однако при наличии временно приостановленных ограничений эти события не будут вызываться, и необходимо будет программно определять, какие столбцы были изменены. Для этого можно выполнить итерацию по коллекции <xref:System.Data.DataTable.Columns%2A> и сравнить различные значения <xref:System.Data.DataRowVersion>.

### <a name="to-get-the-original-version-of-a-record"></a>Получение исходной версии записи

- Получите доступ к значению столбца, передав <xref:System.Data.DataRowVersion> строки, которую необходимо вернуть.

     В следующем примере показано, как использовать значение <xref:System.Data.DataRowVersion> для получения исходного значения поля `CompanyName` в <xref:System.Data.DataRow>:

     [!code-csharp[VbRaddataEditing#21](../data-tools/codesnippet/CSharp/validate-data-in-datasets_6.cs)]
     [!code-vb[VbRaddataEditing#21](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_6.vb)]

## <a name="access-the-current-version-of-a-datarow"></a>Доступ к текущей версии DataRow

### <a name="to-get-the-current-version-of-a-record"></a>Получение текущей версии записи

- Получите доступ к значению столбца, а затем добавьте в индекс параметр, указывающий, какую версию строки нужно вернуть.

     В следующем примере показано, как использовать значение <xref:System.Data.DataRowVersion> для получения текущего значения поля `CompanyName` в <xref:System.Data.DataRow>:

     [!code-csharp[VbRaddataEditing#22](../data-tools/codesnippet/CSharp/validate-data-in-datasets_7.cs)]
     [!code-vb[VbRaddataEditing#22](../data-tools/codesnippet/VisualBasic/validate-data-in-datasets_7.vb)]

## <a name="see-also"></a>См. также:

- [Инструменты для работы с наборами данных в Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)
- [Практическое руководство. Проверка данных элемента управления DataGridView в Windows Forms](/dotnet/framework/winforms/controls/how-to-validate-data-in-the-windows-forms-datagridview-control)
- [Практическое руководство. Отображение значков ошибок при проверке введенных в форму данных с помощью компонента ErrorProvider в Windows Forms](/dotnet/framework/winforms/controls/display-error-icons-for-form-validation-with-wf-errorprovider)
