---
title: Изменить данные в наборах данных | Документация Майкрософт
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
- datasets [Visual Basic], editing data
- data [Visual Studio], editing in datasets
ms.assetid: 50d5c580-fbf7-408f-be70-e63ac4f4d0eb
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 699ee9b6e7a68c6a79f7f7dac526127206e8aa42
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672406"
---
# <a name="edit-data-in-datasets"></a>Изменение данных в наборах данных
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Изменение данных в таблицах данных аналогично изменению данных в таблице в любой базе данных. Процесс может включать в себя вставку, обновление и удаление записей в таблице. В форме с привязкой к данным можно указать, какие поля доступны для изменения пользователем. В таких случаях инфраструктура привязки данных обрабатывает все отслеживание изменений, чтобы изменения можно было отправить обратно в базу данных позже. Если вы собираетесь вносить изменения в данные программными средствами и планируете их отправить обратно в базу данных, необходимо использовать объекты и методы, которые выполняют отслеживание изменений.

 Помимо изменения фактических данных, можно также запросить <xref:System.Data.DataTable>, чтобы получить определенные строки данных. Например, можно запрашивать отдельные строки, отдельные версии строк (исходные и предложенные), строки, которые были изменены, или строки с ошибками.

## <a name="to-edit-rows-in-a-dataset"></a>Изменение строк в наборе данных
 Чтобы изменить существующую строку в <xref:System.Data.DataTable>, необходимо выбрать <xref:System.Data.DataRow>, который требуется изменить, а затем назначить обновленные значения нужным столбцам.

 Если вы не знакомы с индексом строки, которую нужно изменить, используйте метод `FindBy` для поиска по первичному ключу:

 [!code-csharp[VbRaddataEditing#3](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#3)]
 [!code-vb[VbRaddataEditing#3](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#3)]

 Если вы знакомы с индексом строки, можно получить доступ к строкам и отредактировать ее следующим образом:

 [!code-csharp[VbRaddataEditing#5](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#5)]
 [!code-vb[VbRaddataEditing#5](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#5)]

## <a name="to-insert-new-rows-into-a-dataset"></a>Вставка новых строк в набор данных
 Приложения, использующие привязанные к данным элементы управления, обычно добавляют новые записи с помощью кнопки **Добавить новую** в [элементе управления BindingNavigator](https://msdn.microsoft.com/library/18c1e2a5-9834-40d3-9b2e-2b545e4e769e).

 Чтобы вручную добавить новые записи в набор данных, создайте новую строку данных, вызвав метод для DataTable. Затем добавьте строку в коллекцию <xref:System.Data.DataRow> (<xref:System.Data.DataTable.Rows%2A>) <xref:System.Data.DataTable>:

 [!code-csharp[VbRaddataEditing#1](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#1)]
 [!code-vb[VbRaddataEditing#1](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#1)]

 Чтобы хранить сведения, необходимые набору данных для отправки обновлений в источник данных, используйте метод <xref:System.Data.DataRow.Delete%2A> для удаления строк из таблицы данных. Например, если приложение использует TableAdapter (или <xref:System.Data.Common.DataAdapter>), метод `Update` TableAdapter удаляет строки в базе данных, в которой есть <xref:System.Data.DataRow.RowState%2A> <xref:System.Data.DataRowState>.

 Если приложению не требуется отсылать обновления обратно в источник данных, можно удалить записи путем прямого доступа к коллекции строк данных (<xref:System.Data.DataRowCollection.Remove%2A>).

#### <a name="to-delete-records-from-a-data-table"></a>Удаление записей из таблицы данных

- Вызовите метод <xref:System.Data.DataRow.Delete%2A> <xref:System.Data.DataRow>.

     Этот метод не удаляет запись физически. Вместо этого он помечает запись для удаления.

    > [!NOTE]
    > Если вы получаете свойство Count <xref:System.Data.DataRowCollection>, полученное число включает записи, которые были помечены для удаления. Чтобы получить точное число записей, которые не отмечены для удаления, можно выполнить цикл по коллекции, просмотрев свойство <xref:System.Data.DataRow.RowState%2A> каждой записи. (Записи, помеченные для удаления, имеют <xref:System.Data.DataRow.RowState%2A> <xref:System.Data.DataRowState>.) Кроме того, можно создать представление данных для набора данных, которое фильтруется на основе состояния строки и получает из него свойство Count.

     В следующем примере показано, как вызвать метод <xref:System.Data.DataRow.Delete%2A>, чтобы пометить первую строку в `Customers` таблице как удаленную:

     [!code-csharp[VbRaddataEditing#8](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#8)]
     [!code-vb[VbRaddataEditing#8](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#8)]

## <a name="determine-if-there-are-changed-rows"></a>Определение наличия измененных строк
 При внесении изменений в записи в наборе данных сведения об этих изменениях сохраняются до их фиксации. Изменения фиксируются при вызове метода `AcceptChanges` набора данных или таблицы данных, а также при вызове метода `Update` адаптеров TableAdapter или адаптера данных.

 Изменения записываются двумя способами в каждой строке данных:

- Каждая строка данных содержит сведения, связанные с <xref:System.Data.DataRow.RowState%2A> (например, <xref:System.Data.DataRowState>, <xref:System.Data.DataRowState>, <xref:System.Data.DataRowState> или <xref:System.Data.DataRowState>).

- Каждая строка измененных данных содержит несколько версий этой строки (<xref:System.Data.DataRowVersion>), исходную версию (до изменений) и текущую версию (после изменений). В течение периода, когда ожидается изменение (время, когда вы можете ответить на событие <xref:System.Data.DataTable.RowChanging>), также доступен третья версия — предложенная версия.

  Метод <xref:System.Data.DataSet.HasChanges%2A> набора данных возвращает `true`, если в наборе данных были внесены изменения. Определив, что измененные строки существуют, можно вызвать метод `GetChanges` <xref:System.Data.DataSet> или <xref:System.Data.DataTable>, чтобы вернуть набор измененных строк. Дополнительные сведения см. [в разделе инструкции. извлечение измененных строк](https://msdn.microsoft.com/library/6ff0cbd0-5253-48e7-888a-144d56c2e0a9).

#### <a name="to-determine-if-changes-have-been-made-to-any-rows"></a>Определение того, были ли внесены изменения в строки

- Вызовите метод <xref:System.Data.DataSet.HasChanges%2A> набора данных, чтобы проверить наличие измененных строк.

     В следующем примере показано, как проверить возвращаемое значение метода <xref:System.Data.DataSet.HasChanges%2A>, чтобы определить, имеются ли измененные строки в наборе данных с именем `NorthwindDataset1`.

     [!code-csharp[VbRaddataEditing#12](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#12)]
     [!code-vb[VbRaddataEditing#12](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#12)]

## <a name="determine-the-type-of-changes"></a>Определение типа изменений
 Можно также проверить, какие типы изменений были сделаны в наборе данных, передав значение из перечисления <xref:System.Data.DataRowState> в метод <xref:System.Data.DataSet.HasChanges%2A>.

#### <a name="to-determine-what-type-of-changes-have-been-made-to-a-row"></a>Определение типа изменений, внесенных в строку

- Передайте значение <xref:System.Data.DataRowState> в метод <xref:System.Data.DataSet.HasChanges%2A>.

     В следующем примере показано, как проверить набор данных с именем `NorthwindDataset1`, чтобы определить, были ли добавлены новые строки.

     [!code-csharp[VbRaddataEditing#13](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#13)]
     [!code-vb[VbRaddataEditing#13](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#13)]

## <a name="to-locate-rows-that-have-errors"></a>Обнаружение строк с ошибками
 При работе с отдельными столбцами и строками данных могут возникнуть ошибки. Можно проверить свойство `HasErrors`, чтобы определить, существуют ли ошибки в <xref:System.Data.DataSet>, <xref:System.Data.DataTable> или <xref:System.Data.DataRow>.

1. Проверьте свойство `HasErrors`, чтобы проверить наличие ошибок в наборе данных.

2. Если свойство `HasErrors` `true`, выполните итерацию по коллекциям таблиц, а затем по строкам, чтобы найти строку с ошибкой.

     [!code-csharp[VbRaddataEditing#23](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#23)]
     [!code-vb[VbRaddataEditing#23](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#23)]
