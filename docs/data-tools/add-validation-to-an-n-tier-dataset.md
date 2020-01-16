---
title: Добавление проверки в n-уровневом наборе данных
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- n-tier applications, validating
- validation [Visual Basic], n-tier data applications
- validating n-tier data applications
ms.assetid: 34ce4db6-09bb-4b46-b435-b2514aac52d3
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 426399022c2484dca28bb4f4e1f26c14783a3d19
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/16/2020
ms.locfileid: "76113311"
---
# <a name="add-validation-to-an-n-tier-dataset"></a>Добавление проверки в n-уровневом наборе данных
Добавление проверки в набор данных, разделенный на n-уровневое решение, по сути является тем же самым, что и Добавление проверки в набор данных с одним файлом (набор данных в одном проекте). Рекомендуемое расположение для выполнения проверки данных — во время <xref:System.Data.DataTable.ColumnChanging> и (или) <xref:System.Data.DataTable.RowChanging> событий таблицы данных.

Набор данных предоставляет функциональные возможности для создания разделяемых классов, к которым можно добавить пользовательский код для событий изменения столбцов и строк в таблицах данных в наборе данных. Дополнительные сведения о добавлении кода в набор данных в n-уровневого решения см. в разделе [Добавление кода к наборам в многоуровневых приложениях](../data-tools/add-code-to-datasets-in-n-tier-applications.md)и [Добавление кода в адаптеры таблиц в многоуровневых приложениях](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md). Дополнительные сведения о разделяемых классах см. в разделе [как разделить класс на разделяемые классы (конструктор классов)](../ide/class-designer/how-to-split-a-class-into-partial-classes.md) или [разделяемые классы и методы](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods).

> [!NOTE]
> При разделении наборов данных из TableAdapter (путем установки свойства **проекта набора данных** ) существующие классы частичного набора данных в проекте не перемещаются автоматически. Существующие классы частичного набора данных необходимо вручную переместить в проект набора данных.

> [!NOTE]
> Конструктор наборов данных не создает обработчики событий автоматически в C# для событий <xref:System.Data.DataTable.ColumnChanging> и <xref:System.Data.DataTable.RowChanging>. Необходимо вручную создать обработчик событий и подключить обработчик событий к базовому событию. В следующих процедурах описывается создание необходимых обработчиков событий в Visual Basic и C#.

## <a name="validate-changes-to-individual-columns"></a>Проверка изменений в отдельных столбцах
Проверьте значения в отдельных столбцах, обрабатывая событие <xref:System.Data.DataTable.ColumnChanging>. Событие <xref:System.Data.DataTable.ColumnChanging> возникает при изменении значения в столбце. Создайте обработчик событий для события <xref:System.Data.DataTable.ColumnChanging>, дважды щелкнув нужный столбец в **Конструктор наборов данных**.

При первом двойном щелчке столбца конструктор создает обработчик событий для события <xref:System.Data.DataTable.ColumnChanging>. Также создается инструкция `If...Then`, которая проверяет конкретный столбец. Например, следующий код создается при двойном щелчке столбца **ДатаНазначения** в таблице "заказы" Northwind:

```vb
Private Sub OrdersDataTable_ColumnChanging(ByVal sender As System.Object, ByVal e As System.Data.DataColumnChangeEventArgs) Handles Me.ColumnChanging
    If (e.Column.ColumnName = Me.RequiredDateColumn.ColumnName) Then
        ' Add validation code here.
    End If
End Sub
```

> [!NOTE]
> В C# проектах конструктор наборов данных создает разделяемые классы для набора данных и отдельных таблиц в наборе данных. Конструктор наборов данных не создает автоматически обработчики событий для <xref:System.Data.DataTable.ColumnChanging> и <xref:System.Data.DataTable.RowChanging> событий, C# как это происходит в Visual Basic. В C# проектах необходимо вручную создать метод для обработки события и подключения метода к базовому событию. Следующая процедура описывает действия по созданию необходимых обработчиков событий в Visual Basic и C#.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

#### <a name="to-add-validation-during-changes-to-individual-column-values"></a>Добавление проверки во время внесения изменений в значения отдельных столбцов

1. Откройте набор данных, дважды щелкнув *XSD* -файл в **Обозреватель решений**. Дополнительные сведения см. [в разделе Пошаговое руководство. Создание набора данных в конструктор наборов данных](walkthrough-creating-a-dataset-with-the-dataset-designer.md).

2. Дважды щелкните столбец, который необходимо проверить. Это действие создает обработчик событий <xref:System.Data.DataTable.ColumnChanging>.

    > [!NOTE]
    > Конструктор наборов данных не создает обработчик событий для C# события автоматически. Код, необходимый для работы с событием в C# , включен в следующий раздел. `SampleColumnChangingEvent` создается, а затем присоединяется к событию <xref:System.Data.DataTable.ColumnChanging> в методе <xref:System.Data.DataTable.EndInit%2A>.

3. Добавьте код, чтобы убедиться, что `e.ProposedValue` содержит данные, соответствующие требованиям приложения. Если предложенное значение недопустимо, установите столбец, чтобы указать, что он содержит ошибку.

     В следующем примере кода проверяется, что столбец **Quantity** содержит значение больше 0. Если **Quantity** меньше или равно 0, в столбце задается ошибка. Предложение `Else` очищает ошибку, если **Quantity** больше 0. Код в обработчике событий изменения столбца должен выглядеть следующим образом:

    ```vb
    If (e.Column.ColumnName = Me.QuantityColumn.ColumnName) Then
        If CType(e.ProposedValue, Short) <= 0 Then
            e.Row.SetColumnError(e.Column, "Quantity must be greater than 0")
        Else
            e.Row.SetColumnError(e.Column, "")
        End If
    End If
    ```

    ```csharp
    // Add this code to the DataTable partial class.

    public override void EndInit()
    {
        base.EndInit();
        // Hook up the ColumnChanging event
        // to call the SampleColumnChangingEvent method.
        ColumnChanging += SampleColumnChangingEvent;
    }

    public void SampleColumnChangingEvent(object sender, System.Data.DataColumnChangeEventArgs e)
    {
        if (e.Column.ColumnName == QuantityColumn.ColumnName)
        {
            if ((short)e.ProposedValue <= 0)
            {
                e.Row.SetColumnError("Quantity", "Quantity must be greater than 0");
            }
            else
            {
                e.Row.SetColumnError("Quantity", "");
            }
        }
    }
    ```

## <a name="validate-changes-to-whole-rows"></a>Проверка изменений в целых строках
Проверьте значения в целых строках, обрабатывая событие <xref:System.Data.DataTable.RowChanging>. Событие <xref:System.Data.DataTable.RowChanging> возникает при фиксации значений во всех столбцах. Необходимо проверить в событии <xref:System.Data.DataTable.RowChanging>, когда значение в одном столбце зависит от значения в другом столбце. Например, рассмотрим OrderDate и ДатаНазначения в таблице Orders в Northwind.

При указании заказов проверка гарантирует, что заказ не будет добавлен в поле ДатаРазмещения, которое находится в или до значения OrderDate. В этом примере необходимо сравнить значения столбцов ДатаНазначения и OrderDate, поэтому проверка изменения отдельного столбца не имеет смысла.

Создайте обработчик событий для <xref:System.Data.DataTable.RowChanging> события, дважды щелкнув имя таблицы в строке заголовка таблицы на **Конструктор наборов данных**.

#### <a name="to-add-validation-during-changes-to-whole-rows"></a>Добавление проверки во время изменений в целых строках

1. Откройте набор данных, дважды щелкнув *XSD* -файл в **Обозреватель решений**. Дополнительные сведения см. [в разделе Пошаговое руководство. Создание набора данных в конструктор наборов данных](walkthrough-creating-a-dataset-with-the-dataset-designer.md).

2. Дважды щелкните заголовок окна таблицы данных в конструкторе.

     Разделяемый класс создается с помощью обработчика событий `RowChanging` и открывается в редакторе кода.

    > [!NOTE]
    > Конструктор наборов данных не создает автоматически обработчик событий для события <xref:System.Data.DataTable.RowChanging> в C# проектах. Необходимо создать метод для обработки события <xref:System.Data.DataTable.RowChanging> и выполнения кода, а затем подключить событие в методе инициализации таблицы.

3. Добавьте пользовательский код внутри объявления разделяемого класса.

4. В следующем коде показано, куда добавить пользовательский код для проверки во время события <xref:System.Data.DataTable.RowChanging>. C# Пример также включает код для подключения метода обработчика событий к событию `OrdersRowChanging`.

    ```vb
    Partial Class OrdersDataTable
        Private Sub OrdersDataTable_OrdersRowChanging(ByVal sender As System.Object, ByVal e As OrdersRowChangeEvent) Handles Me.OrdersRowChanging
            ' Add logic to validate columns here.
            If e.Row.RequiredDate <= e.Row.OrderDate Then
                ' Set the RowError if validation fails.
                e.Row.RowError = "Required Date cannot be on or before the OrderDate"
            Else
                ' Clear the RowError when validation passes.
                e.Row.RowError = ""
            End If
        End Sub
    End Class
    ```

    ```csharp
    partial class OrdersDataTable
    {
        public override void EndInit()
        {
            base.EndInit();
            // Hook up the event to the
            // RowChangingEvent method.
            OrdersRowChanging += RowChangingEvent;
        }

        public void RowChangingEvent(object sender, OrdersRowChangeEvent e)
        {
            // Perform the validation logic.
            if (e.Row.RequiredDate <= e.Row.OrderDate)
            {
                // Set the row to an error when validation fails.
                e.Row.RowError = "Required Date cannot be on or before the OrderDate";
            }
            else
            {
                // Clear the RowError if validation passes.
                e.Row.RowError = "";
            }
        }
    }
    ```

## <a name="see-also"></a>См. также:

- [Общие сведения об n-уровневых приложениях](../data-tools/n-tier-data-applications-overview.md)
- [Пошаговое руководство. Создание n-уровневого приложения для работы с данными](../data-tools/walkthrough-creating-an-n-tier-data-application.md)
- [Проверка данных в наборах данных](../data-tools/validate-data-in-datasets.md)
