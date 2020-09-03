---
title: Добавление проверки в n-уровневый набор данных | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- n-tier applications, validating
- validation [Visual Basic], n-tier data applications
- validating n-tier data applications
ms.assetid: 34ce4db6-09bb-4b46-b435-b2514aac52d3
caps.latest.revision: 27
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b03f1e85140d62d84ae7c706a9bfee6a7c515abb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72673053"
---
# <a name="add-validation-to-an-n-tier-dataset"></a>Добавление проверки в n-уровневом наборе данных
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Добавление проверки в набор данных, разделенный на n-уровневое решение, по сути является тем же самым, что и Добавление проверки в набор данных с одним файлом (набор данных в одном проекте). Рекомендуемое расположение для выполнения проверки данных — во время <xref:System.Data.DataTable.ColumnChanging> событий и (или <xref:System.Data.DataTable.RowChanging> ) таблиц данных.

Конструктор наборов данных предоставляет функциональные возможности для создания разделяемых классов, к которым можно добавить пользовательский код для событий изменения столбцов и строк в таблицах данных в наборе данных. Дополнительные сведения о добавлении кода в набор данных в n-уровневого решения см. в разделе [Добавление кода к наборам в многоуровневых приложениях](../data-tools/add-code-to-datasets-in-n-tier-applications.md)и [Добавление кода в адаптеры таблиц в многоуровневых приложениях](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md). Дополнительные сведения о разделяемых классах см. в разделе [как разделить класс на разделяемые классы (конструктор классов)](../ide/how-to-split-a-class-into-partial-classes-class-designer.md) или [разделяемые классы и методы](https://msdn.microsoft.com/library/804cecb7-62db-4f97-a99f-60975bd59fa1).

> [!NOTE]
> При разделении наборов данных из TableAdapter (путем установки свойства **проекта набора данных** ) существующие классы частичного набора данных в проекте не перемещаются автоматически. Существующие разделяемые классы наборов данных необходимо вручную переместить в проект набора данных.

> [!NOTE]
> Конструктор наборов данных не создает автоматически обработчики событий в C# для <xref:System.Data.DataTable.ColumnChanging> <xref:System.Data.DataTable.RowChanging> событий и. Необходимо вручную создать обработчик событий и подключить обработчик событий к базовому событию. В следующих процедурах описывается создание необходимых обработчиков событий в Visual Basic и C#.

## <a name="validatechanges-to-individual-columns"></a>Валидатечанжес к отдельным столбцам
 Проверьте значения в отдельных столбцах, обрабатывая <xref:System.Data.DataTable.ColumnChanging> событие. <xref:System.Data.DataTable.ColumnChanging>Событие возникает при изменении значения в столбце. Создайте обработчик событий для <xref:System.Data.DataTable.ColumnChanging> события, дважды щелкнув нужный столбец в наборе данных.

 При первом двойном щелчке столбца конструктор создает обработчик событий для <xref:System.Data.DataTable.ColumnChanging> события. `If…Then`Кроме того, создается инструкция, которая проверяет конкретный столбец. Например, следующий код создается при двойном щелчке столбца ДатаНазначения в таблице "заказы" Northwind:

```vb
Private Sub OrdersDataTable_ColumnChanging(ByVal sender As System.Object, ByVal e As System.Data.DataColumnChangeEventArgs) Handles Me.ColumnChanging
    If (e.Column.ColumnName = Me.RequiredDateColumn.ColumnName) Then
        ' Add validation code here.
    End If
End Sub
```

> [!NOTE]
> В проектах C# конструктор наборов данных создает разделяемые классы для набора данных и отдельных таблиц в наборе данных. Конструктор наборов данных не создает автоматически обработчики событий для <xref:System.Data.DataTable.ColumnChanging> <xref:System.Data.DataTable.RowChanging> событий и в C#, как это происходит в Visual Basic. В проектах C# необходимо вручную создать метод для обработки события и подключения метода к базовому событию. Следующая процедура описывает создание необходимых обработчиков событий в Visual Basic и C#.

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

#### <a name="to-add-validation-during-changes-to-individual-column-values"></a>Добавление проверки во время внесения изменений в значения отдельных столбцов

1. Откройте набор данных в конструкторе, дважды щелкнув **XSD** -файл в **Обозреватель решений**. Дополнительные сведения см. в разделе [как открыть набор данных в конструктор наборов данных](https://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).

2. Дважды щелкните столбец, который необходимо проверить. Это действие создает <xref:System.Data.DataTable.ColumnChanging> обработчик событий.

    > [!NOTE]
    > Конструктор наборов данных не создает обработчик событий для события C# автоматически. Код, необходимый для работы с событием в C#, включен в следующий раздел. `SampleColumnChangingEvent` создается, а затем присоединяется к <xref:System.Data.DataTable.ColumnChanging> событию в <xref:System.Data.DataTable.EndInit%2A> методе.

3. Добавьте код для проверки того, что `e.ProposedValue` содержит данные, соответствующие требованиям приложения. Если предложенное значение недопустимо, установите столбец, чтобы указать, что он содержит ошибку.

     В следующем примере кода проверяется, что столбец **Quantity** содержит больше 0. Если **Quantity** меньше или равно 0, в столбце задается ошибка. `Else`Предложение очищает ошибку, если **Quantity** больше 0. Код в обработчике событий изменения столбца должен выглядеть следующим образом:

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
    // C#
    // Add this code to the DataTable
    // partial class.

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

## <a name="validatechanges-to-whole-rows"></a>Валидатечанжес в целые строки
 Проверьте значения в целых строках, обрабатывая <xref:System.Data.DataTable.RowChanging> событие. <xref:System.Data.DataTable.RowChanging>Событие возникает при фиксации значений во всех столбцах. Необходимо проверить в <xref:System.Data.DataTable.RowChanging> событии, когда значение в одном столбце зависит от значения в другом столбце. Например, рассмотрим OrderDate и ДатаНазначения в таблице Orders в Northwind.

 При указании заказов проверка гарантирует, что заказ не будет добавлен в поле ДатаРазмещения, которое находится в или до значения OrderDate. В этом примере необходимо сравнить значения столбцов ДатаНазначения и OrderDate, поэтому проверка изменения отдельного столбца не имеет смысла.

 Создайте обработчик событий для <xref:System.Data.DataTable.RowChanging> события, дважды щелкнув имя таблицы в строке заголовка таблицы.

#### <a name="to-add-validation-during-changes-to-whole-rows"></a>Добавление проверки во время изменений в целых строках

1. Откройте набор данных в конструкторе, дважды щелкнув **XSD** -файл в **Обозреватель решений**. Дополнительные сведения см. в разделе [как открыть набор данных в конструктор наборов данных](https://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).

2. Дважды щелкните заголовок окна таблицы данных в конструкторе.

     Разделяемый класс создается с помощью `RowChanging` обработчика событий и открывается в редакторе кода.

    > [!NOTE]
    > Конструктор наборов данных не создает обработчик событий для <xref:System.Data.DataTable.RowChanging> события в проектах C# автоматически. Необходимо создать метод для обработки <xref:System.Data.DataTable.RowChanging> события и выполнения кода для подключения события в методе инициализации таблицы.

3. Добавьте пользовательский код внутри объявления разделяемого класса.

4. В следующем коде показано, куда добавить пользовательский код для проверки во время <xref:System.Data.DataTable.RowChanging> события для Visual Basic:

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

5. В следующем коде показано, как создать `RowChanging` обработчик событий и добавить в него пользовательский код для проверки во время <xref:System.Data.DataTable.RowChanging> события для C#:

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
 [Обзор многоуровневых приложений для данных](../data-tools/n-tier-data-applications-overview.md) [. Пошаговое руководство. Создание n-уровневого приложения](../data-tools/walkthrough-creating-an-n-tier-data-application.md) [для проверки данных в наборах](../data-tools/validate-data-in-datasets.md) данных
