---
title: Изменение данных в наборах данных
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- datasets [Visual Basic], editing data
- data [Visual Studio], editing in datasets
ms.assetid: 50d5c580-fbf7-408f-be70-e63ac4f4d0eb
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 256b22281f64a1a04f8d691f2f48cc7b0295b1a1
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
ms.locfileid: "31926383"
---
# <a name="edit-data-in-datasets"></a>Изменение данных в наборах данных
Изменение данных в таблицах данных, подобно изменить данные в таблице в любой базе данных. Процесс может включать вставки, обновления и удаления записей в таблице. В форму с привязкой к данным можно указать, какие поля являются изменяемые пользователем. В таких случаях инфраструктуры привязки данных обрабатывает все отслеживания изменений, чтобы эти изменения можно отправить в базу данных более поздней версии. Если предполагается передавать эти изменения в базе данных программным путем вносить изменения в данных, необходимо использовать объекты и методы, которые выполняют отслеживания изменений для вас.

Помимо изменения фактических данных, также можно запрашивать <xref:System.Data.DataTable> позволит возвращать конкретные строки данных. Например может запросить для отдельных строк, определенных версий строк (исходные и предложенные), измененных строк или строк с ошибками.

## <a name="to-edit-rows-in-a-dataset"></a>Для изменения строк в наборе данных
Чтобы изменить существующую строку в <xref:System.Data.DataTable>, вам нужно найти <xref:System.Data.DataRow> требуется изменить, а затем присвоить обновленные значения нужным столбцам.

Если вы не знаете индекс строки, вы хотите изменить, воспользуйтесь `FindBy` метод для поиска по первичному ключу:

[!code-csharp[VbRaddataEditing#3](../data-tools/codesnippet/CSharp/edit-data-in-datasets_1.cs)]
[!code-vb[VbRaddataEditing#3](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_1.vb)]

Если вы знаете индекс строки, доступны и изменяет строк следующим образом:

[!code-csharp[VbRaddataEditing#5](../data-tools/codesnippet/CSharp/edit-data-in-datasets_2.cs)]
[!code-vb[VbRaddataEditing#5](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_2.vb)]

## <a name="to-insert-new-rows-into-a-dataset"></a>Для вставки новых строк в набор данных
Приложения, использующие элементы управления с привязкой к данным обычно Добавление новых записей с помощью **добавить новое** кнопку [элемент управления BindingNavigator](/dotnet/framework/winforms/controls/bindingnavigator-control-windows-forms).

Для добавления новых записей в набор данных вручную, создайте новую строку данных путем вызова метода в DataTable. Затем добавьте строки <xref:System.Data.DataRow> коллекции (<xref:System.Data.DataTable.Rows%2A>) из <xref:System.Data.DataTable>:

[!code-csharp[VbRaddataEditing#1](../data-tools/codesnippet/CSharp/edit-data-in-datasets_3.cs)]
[!code-vb[VbRaddataEditing#1](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_3.vb)]

Чтобы сохранить сведения, что набор данных для отправки обновлений в источник данных, используйте <xref:System.Data.DataRow.Delete%2A> метод для удаления строк в таблице данных. Например, если приложение использует TableAdapter (или <xref:System.Data.Common.DataAdapter>), его `Update` метод удаляет строки в базе данных, содержащие <xref:System.Data.DataRow.RowState%2A> из <xref:System.Data.DataRowState.Deleted>.

Если приложению не требуется отправлять обновления обратно к источнику данных, то это можно удалить записи методом прямого доступа к коллекции строк данных (<xref:System.Data.DataRowCollection.Remove%2A>).

#### <a name="to-delete-records-from-a-data-table"></a>Для удаления записей из таблицы данных

-   Вызовите <xref:System.Data.DataRow.Delete%2A> метод <xref:System.Data.DataRow>.

     Этот метод не удаляет записи физически. Вместо этого он помечает записи для удаления.

    > [!NOTE]
    >  Если вы получаете свойство count <xref:System.Data.DataRowCollection>, результирующее значение включает записи, которые были помечены для удаления. Чтобы получить точное число записей, которые не помечены для удаления, можно использовать цикл по коллекции, просмотрев <xref:System.Data.DataRow.RowState%2A> свойства каждой записи. (Помеченные на удаление записи имеют <xref:System.Data.DataRow.RowState%2A> из <xref:System.Data.DataRowState.Deleted>.) Кроме того можно создать представление данных набора данных, фильтры на основе состояния строки и получить свойство count оттуда.

В следующем примере демонстрируется вызов <xref:System.Data.DataRow.Delete%2A> метод, чтобы пометить первую строку в `Customers` таблице как удаленные:

[!code-csharp[VbRaddataEditing#8](../data-tools/codesnippet/CSharp/edit-data-in-datasets_4.cs)]
[!code-vb[VbRaddataEditing#8](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_4.vb)]

## <a name="determine-if-there-are-changed-rows"></a>Определить наличие измененных строк
При изменении записи в наборе данных, сведения об этих изменениях хранятся до их фиксации. Внесенные изменения фиксируются при вызове `AcceptChanges` метод таблицы набора данных или данных или при вызове `Update` метод адаптера TableAdapter или данных.

Изменения отслеживаемых двумя способами в каждой строке данных.

-   Каждая строка данных содержит сведения, относящиеся к его <xref:System.Data.DataRow.RowState%2A> (например, <xref:System.Data.DataRowState.Added>, <xref:System.Data.DataRowState.Modified>, <xref:System.Data.DataRowState.Deleted>, или <xref:System.Data.DataRowState.Unchanged>).

-   Каждая строка измененных данных содержит несколько версий этой строки (<xref:System.Data.DataRowVersion>), исходной версии (до изменений) и текущую версию (после изменений). В период, когда изменения еще не завершены (время, когда можно ответить на <xref:System.Data.DataTable.RowChanging> событий), третий версия — предложенная — доступна также.

<xref:System.Data.DataSet.HasChanges%2A> Метод набора данных возвращает `true` Если были внесены изменения в наборе данных. После определения существования измененных строк, можно вызвать `GetChanges` метод <xref:System.Data.DataSet> или <xref:System.Data.DataTable> для возвращения набора измененных строк.

#### <a name="to-determine-if-changes-have-been-made-to-any-rows"></a>Чтобы определить, были ли внесены изменения в строки

-   Вызовите <xref:System.Data.DataSet.HasChanges%2A> метод набора данных для проверки измененных строк.

В следующем примере показано, как проверять возвращаемое значение из <xref:System.Data.DataSet.HasChanges%2A> метод для выявления измененных строк в наборе данных с именем `NorthwindDataset1`:

[!code-csharp[VbRaddataEditing#12](../data-tools/codesnippet/CSharp/edit-data-in-datasets_5.cs)]
[!code-vb[VbRaddataEditing#12](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_5.vb)]

## <a name="determine-the-type-of-changes"></a>Определение типа изменений
Можно также проверить, чтобы увидеть, какой тип изменения были внесены в наборе данных путем передачи значения из <xref:System.Data.DataRowState> перечисления <xref:System.Data.DataSet.HasChanges%2A> метод.

#### <a name="to-determine-what-type-of-changes-have-been-made-to-a-row"></a>Чтобы определить тип изменений были внесены в строку

-   Передайте <xref:System.Data.DataRowState> значение <xref:System.Data.DataSet.HasChanges%2A> метод.

В следующем примере показано, как проверить набор данных с именем `NorthwindDataset1` для определения, если к нему были добавлены никакие новые строки:

[!code-csharp[VbRaddataEditing#13](../data-tools/codesnippet/CSharp/edit-data-in-datasets_6.cs)]
[!code-vb[VbRaddataEditing#13](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_6.vb)]

## <a name="to-locate-rows-that-have-errors"></a>Чтобы найти строки, содержащие ошибки
При работе с отдельными столбцами и строками данных, могут возникнуть ошибки. Вы можете проверить `HasErrors` свойства, чтобы определить наличие ошибок <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, или <xref:System.Data.DataRow>.

1.  Проверьте `HasErrors` свойство, чтобы определить наличие ошибок в наборе данных.

2.  Если `HasErrors` свойство `true`, итерации по коллекции таблиц, а затем по строкам, чтобы найти строку с ошибкой.

[!code-csharp[VbRaddataEditing#23](../data-tools/codesnippet/CSharp/edit-data-in-datasets_7.cs)]
[!code-vb[VbRaddataEditing#23](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_7.vb)]

## <a name="see-also"></a>См. также

- [Инструменты для работы с наборами данных в Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)