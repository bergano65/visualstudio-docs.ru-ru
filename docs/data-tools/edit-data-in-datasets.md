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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: b51b5b4be12f76e2237ff93659617e1c1843722a
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/01/2020
ms.locfileid: "75586657"
---
# <a name="edit-data-in-datasets"></a>Изменение данных в наборах данных
Изменение данных в таблицах данных аналогично изменению данных в таблице в любой базе данных. Процесс может включать в себя вставку, обновление и удаление записей в таблице. В форме с привязкой к данным можно указать, какие поля доступны для изменения пользователем. В таких случаях инфраструктура привязки данных обрабатывает все отслеживание изменений, чтобы изменения можно было отправить обратно в базу данных позже. Если вы собираетесь вносить изменения в данные программными средствами и планируете их отправить обратно в базу данных, необходимо использовать объекты и методы, которые выполняют отслеживание изменений.

Помимо изменения фактических данных, можно также запросить <xref:System.Data.DataTable>, чтобы получить определенные строки данных. Например, можно запрашивать отдельные строки, отдельные версии строк (исходные и предложенные), строки, которые были изменены, или строки с ошибками.

## <a name="to-edit-rows-in-a-dataset"></a>Изменение строк в наборе данных
Чтобы изменить существующую строку в <xref:System.Data.DataTable>, необходимо выбрать <xref:System.Data.DataRow>, который требуется изменить, а затем назначить обновленные значения нужным столбцам.

Если вы не знакомы с индексом строки, которую нужно изменить, используйте метод `FindBy` для поиска по первичному ключу:

[!code-csharp[VbRaddataEditing#3](../data-tools/codesnippet/CSharp/edit-data-in-datasets_1.cs)]
[!code-vb[VbRaddataEditing#3](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_1.vb)]

Если вы знакомы с индексом строки, можно получить доступ к строкам и отредактировать ее следующим образом:

[!code-csharp[VbRaddataEditing#5](../data-tools/codesnippet/CSharp/edit-data-in-datasets_2.cs)]
[!code-vb[VbRaddataEditing#5](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_2.vb)]

## <a name="to-insert-new-rows-into-a-dataset"></a>Вставка новых строк в набор данных
Приложения, использующие привязанные к данным элементы управления, обычно добавляют новые записи с помощью кнопки **Добавить новую** в [элементе управления BindingNavigator](/dotnet/framework/winforms/controls/bindingnavigator-control-windows-forms).

Чтобы вручную добавить новые записи в набор данных, создайте новую строку данных, вызвав метод для DataTable. Затем добавьте строку в коллекцию <xref:System.Data.DataRow> (<xref:System.Data.DataTable.Rows%2A>) <xref:System.Data.DataTable>:

[!code-csharp[VbRaddataEditing#1](../data-tools/codesnippet/CSharp/edit-data-in-datasets_3.cs)]
[!code-vb[VbRaddataEditing#1](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_3.vb)]

Чтобы хранить сведения, необходимые набору данных для отправки обновлений в источник данных, используйте метод <xref:System.Data.DataRow.Delete%2A> для удаления строк из таблицы данных. Например, если приложение использует TableAdapter (или <xref:System.Data.Common.DataAdapter>), метод `Update` TableAdapter удаляет строки в базе данных, в которой есть <xref:System.Data.DataRow.RowState%2A> <xref:System.Data.DataRowState.Deleted>.

Если приложению не требуется отсылать обновления обратно в источник данных, можно удалить записи путем прямого доступа к коллекции строк данных (<xref:System.Data.DataRowCollection.Remove%2A>).

#### <a name="to-delete-records-from-a-data-table"></a>Удаление записей из таблицы данных

- Вызовите метод <xref:System.Data.DataRow.Delete%2A> <xref:System.Data.DataRow>.

     Этот метод не удаляет запись физически. Вместо этого он помечает запись для удаления.

    > [!NOTE]
    > Если вы получаете свойство Count <xref:System.Data.DataRowCollection>, полученное число включает записи, которые были помечены для удаления. Чтобы получить точное число записей, которые не отмечены для удаления, можно выполнить цикл по коллекции, просмотрев свойство <xref:System.Data.DataRow.RowState%2A> каждой записи. (Записи, помеченные для удаления, имеют <xref:System.Data.DataRow.RowState%2A> <xref:System.Data.DataRowState.Deleted>.) Кроме того, можно создать представление данных для набора данных, которое фильтруется на основе состояния строки и получает из него свойство Count.

В следующем примере показано, как вызвать метод <xref:System.Data.DataRow.Delete%2A>, чтобы пометить первую строку в `Customers` таблице как удаленную:

[!code-csharp[VbRaddataEditing#8](../data-tools/codesnippet/CSharp/edit-data-in-datasets_4.cs)]
[!code-vb[VbRaddataEditing#8](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_4.vb)]

## <a name="determine-if-there-are-changed-rows"></a>Определение наличия измененных строк
При внесении изменений в записи в наборе данных сведения об этих изменениях сохраняются до их фиксации. Изменения фиксируются при вызове метода `AcceptChanges` набора данных или таблицы данных, а также при вызове метода `Update` адаптеров TableAdapter или адаптера данных.

Изменения записываются двумя способами в каждой строке данных:

- Каждая строка данных содержит сведения, относящиеся к его <xref:System.Data.DataRow.RowState%2A> (например, <xref:System.Data.DataRowState.Added>, <xref:System.Data.DataRowState.Modified>, <xref:System.Data.DataRowState.Deleted>или <xref:System.Data.DataRowState.Unchanged>).

- Каждая измененная строка данных содержит несколько версий этой строки (<xref:System.Data.DataRowVersion>), исходную версию (до изменений) и текущую версию (после изменений). В течение периода, когда ожидается изменение (время, когда вы можете ответить на событие <xref:System.Data.DataTable.RowChanging>), также доступен третья версия — предложенная версия.

Метод <xref:System.Data.DataSet.HasChanges%2A> набора данных возвращает `true`, если в наборе данных были внесены изменения. Определив, что измененные строки существуют, можно вызвать метод `GetChanges` <xref:System.Data.DataSet> или <xref:System.Data.DataTable>, чтобы вернуть набор измененных строк.

#### <a name="to-determine-if-changes-have-been-made-to-any-rows"></a>Определение того, были ли внесены изменения в строки

- Вызовите метод <xref:System.Data.DataSet.HasChanges%2A> набора данных, чтобы проверить наличие измененных строк.

В следующем примере показано, как проверить возвращаемое значение метода <xref:System.Data.DataSet.HasChanges%2A>, чтобы определить, имеются ли измененные строки в наборе данных с именем `NorthwindDataset1`.

[!code-csharp[VbRaddataEditing#12](../data-tools/codesnippet/CSharp/edit-data-in-datasets_5.cs)]
[!code-vb[VbRaddataEditing#12](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_5.vb)]

## <a name="determine-the-type-of-changes"></a>Определение типа изменений
Можно также проверить, какие типы изменений были сделаны в наборе данных, передав значение из перечисления <xref:System.Data.DataRowState> в метод <xref:System.Data.DataSet.HasChanges%2A>.

#### <a name="to-determine-what-type-of-changes-have-been-made-to-a-row"></a>Определение типа изменений, внесенных в строку

- Передайте значение <xref:System.Data.DataRowState> в метод <xref:System.Data.DataSet.HasChanges%2A>.

В следующем примере показано, как проверить набор данных с именем `NorthwindDataset1`, чтобы определить, были ли добавлены новые строки.

[!code-csharp[VbRaddataEditing#13](../data-tools/codesnippet/CSharp/edit-data-in-datasets_6.cs)]
[!code-vb[VbRaddataEditing#13](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_6.vb)]

## <a name="to-locate-rows-that-have-errors"></a>Обнаружение строк с ошибками
При работе с отдельными столбцами и строками данных могут возникнуть ошибки. Можно проверить свойство `HasErrors`, чтобы определить, существуют ли ошибки в <xref:System.Data.DataSet>, <xref:System.Data.DataTable>или <xref:System.Data.DataRow>.

1. Проверьте свойство `HasErrors`, чтобы проверить наличие ошибок в наборе данных.

2. Если свойство `HasErrors` `true`, выполните итерацию по коллекциям таблиц, а затем по строкам, чтобы найти строку с ошибкой.

[!code-csharp[VbRaddataEditing#23](../data-tools/codesnippet/CSharp/edit-data-in-datasets_7.cs)]
[!code-vb[VbRaddataEditing#23](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_7.vb)]

## <a name="see-also"></a>См. также:

- [Инструменты для работы с наборами данных в Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)
