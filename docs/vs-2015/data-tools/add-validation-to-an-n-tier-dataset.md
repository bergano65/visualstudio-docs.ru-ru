---
title: Добавление проверки в n уровневом наборе данных | Документация Майкрософт
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 94a8f4f8fe0d1f93ce3467291a20377234db29f4
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58992929"
---
# <a name="add-validation-to-an-n-tier-dataset"></a>Добавление проверки в n-уровневом наборе данных
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Добавление проверки к набору данных в n уровневого решения по сути является таким же, как добавление проверки к набору данных одного файла (набор данных в одном проекте). Предлагаемое местоположение для выполнения проверки данных — во время <xref:System.Data.DataTable.ColumnChanging> и/или <xref:System.Data.DataTable.RowChanging> события таблицы данных.  
  
Конструктор наборов данных предоставляет возможность создания разделяемых классов, к которым можно добавить пользовательский код для столбца и строки таблиц данных в набор данных событий изменения. Дополнительные сведения о добавлении кода в набор данных в n уровневого решения, см. в разделе [Добавление кода для наборов данных в n уровневых приложениях](../data-tools/add-code-to-datasets-in-n-tier-applications.md), и [добавьте код для объектов TableAdapter в многоуровневых приложениях](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md). Дополнительные сведения о разделяемых классах см. в разделе [как: Разделение класса на разделяемые классы (конструктор классов)](../ide/how-to-split-a-class-into-partial-classes-class-designer.md) или [разделяемые классы и методы](http://msdn.microsoft.com/library/804cecb7-62db-4f97-a99f-60975bd59fa1).  
  
> [!NOTE]
>  При разделении наборов данных из адаптеров таблиц (задавая **проект DataSet** свойство), существующие разделяемые классы наборов данных в проекте не перемещаются автоматически. Существующие разделяемые классы наборов данных должны быть вручную перемещены в проект набора данных.  
  
> [!NOTE]
>  Конструктор наборов данных не создает автоматически обработчики событий в C# для <xref:System.Data.DataTable.ColumnChanging> и <xref:System.Data.DataTable.RowChanging> события. Вам нужно вручную создать обработчик событий и подключить обработчик событий, соответствующем событии. Следующие процедуры описывают создание обработчиков событий в Visual Basic и C#.  
  
## <a name="validatechanges-to-individual-columns"></a>Validatechanges к отдельным столбцам  
 Проверка значений в отдельных столбцах при обработке <xref:System.Data.DataTable.ColumnChanging> событий. <xref:System.Data.DataTable.ColumnChanging> Событие возникает при изменении значения в столбце. Создайте обработчик событий для <xref:System.Data.DataTable.ColumnChanging> событий, дважды щелкнув требуемый столбец в наборе данных.  
  
 Первый раз, дважды щелкните столбец, конструктор создает обработчик событий для <xref:System.Data.DataTable.ColumnChanging> событий. `If…Then` Также создается инструкция, тесты для определенного столбца. Например при двойном щелчке в столбец RequiredDate таблицы Northwind Orders, создается следующий код:  
  
```vb  
Private Sub OrdersDataTable_ColumnChanging(ByVal sender As System.Object, ByVal e As System.Data.DataColumnChangeEventArgs) Handles Me.ColumnChanging  
    If (e.Column.ColumnName = Me.RequiredDateColumn.ColumnName) Then  
        ' Add validation code here.  
    End If  
End Sub  
```  
  
> [!NOTE]
>  В проектах C# конструктор наборов данных создает только разделяемые классы для набора данных и отдельные таблицы в наборе данных. Конструктор наборов данных не создает автоматически обработчики событий для <xref:System.Data.DataTable.ColumnChanging> и <xref:System.Data.DataTable.RowChanging> событий в C#, как и в Visual Basic. В проектах C# необходимо вручную создать метод для обработки события и подключить метод базового события. Ниже описывается, как создавать обработчики событий в Visual Basic и C#.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
#### <a name="to-add-validation-during-changes-to-individual-column-values"></a>Чтобы добавить проверку во время изменения к отдельным значениям в столбце  
  
1.  Откройте набор данных в конструкторе, дважды щелкнув **.xsd** файл **обозревателе решений**. Дополнительные сведения см. в разделе [Как Откройте набор данных в конструкторе наборов данных](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).  
  
2.  Дважды щелкните столбец, который требуется проверить. Это действие создает <xref:System.Data.DataTable.ColumnChanging> обработчик событий.  
  
    > [!NOTE]
    >  Конструктор наборов данных не создает автоматически обработчик событий для события C#. Код, который необходимо обработать событие в C# входит в следующем разделе. `SampleColumnChangingEvent` создается и затем подключается к <xref:System.Data.DataTable.ColumnChanging> событие в <xref:System.Data.DataTable.EndInit%2A> метод.  
  
3.  Добавьте код, чтобы убедиться, что `e.ProposedValue` содержит данные, которые удовлетворяют требованиям приложения. Если предложенное значение является недопустимым, задайте столбец для указания, что он содержит ошибку.  
  
     В следующем примере кода проверяет, что **количество** столбец содержит больше 0. Если **количество** меньше или равно 0, столбцу присваивается ошибку. `Else` Предложение ошибка устраняется, если **количество** больше, чем 0. Код в обработчик событий изменения столбца должен выглядеть следующим образом:  
  
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
  
## <a name="validatechanges-to-whole-rows"></a>Validatechanges всей строки  
 Проверка значений во всей строке при обработке <xref:System.Data.DataTable.RowChanging> событий. <xref:System.Data.DataTable.RowChanging> Событие возникает, когда значения во всех столбцах будут зафиксированы. Это необходимо для проверки в <xref:System.Data.DataTable.RowChanging> событие, когда значение в один столбец основывается на значении в другом столбце. Например рассмотрим OrderDate и RequiredDate в таблице Orders в Northwind.  
  
 После ввода заказов проверки гарантирует, что заказ не введен с RequiredDate, который во время или до OrderDate. В этом примере значения для столбцов OrderDate и RequiredDate необходимо сравнить, поэтому проверка изменения отдельных столбцов не имеет смысла.  
  
 Создайте обработчик событий для <xref:System.Data.DataTable.RowChanging> событий, дважды щелкнув имя таблицы в строке заголовка таблицы.  
  
#### <a name="to-add-validation-during-changes-to-whole-rows"></a>Чтобы добавить проверку во время изменения для всех строк  
  
1.  Откройте набор данных в конструкторе, дважды щелкнув **.xsd** файл **обозревателе решений**. Дополнительные сведения см. в разделе [Как Откройте набор данных в конструкторе наборов данных](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).  
  
2.  Дважды щелкните заголовок таблицы данных в конструкторе.  
  
     Разделяемый класс создается с `RowChanging` обработчик событий и откроется в редакторе кода.  
  
    > [!NOTE]
    >  Конструктор наборов данных не создает автоматически обработчик событий для <xref:System.Data.DataTable.RowChanging> событий в проектах C#. Необходимо создать метод для обработки <xref:System.Data.DataTable.RowChanging> события и выполнить код, чтобы подключить событие в методе инициализации таблицы.  
  
3.  Добавьте код внутри объявления частичного класса.  
  
4.  В следующем коде показано, где можно добавить пользовательский код для проверки во время <xref:System.Data.DataTable.RowChanging> событий для Visual Basic:  
  
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
  
5.  Ниже показано, как создать `RowChanging` обработчик событий и где можно добавить пользовательский код для проверки во время <xref:System.Data.DataTable.RowChanging> событий для C#:  
  
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
  
## <a name="see-also"></a>См. также  
 [Общие сведения о данных в N-уровневых приложениях](../data-tools/n-tier-data-applications-overview.md)   
 [Пошаговое руководство: Создание данных N-уровневого приложения](../data-tools/walkthrough-creating-an-n-tier-data-application.md)   
 [Проверка данных в наборах данных](../data-tools/validate-data-in-datasets.md)
