---
title: Изменение данных в наборах данных | Документация Майкрософт
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 7cbc9519c86b2bf4967e567b29355eb6d8a176a4
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65699771"
---
# <a name="edit-data-in-datasets"></a>Изменение данных в наборах данных
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Изменение данных в таблицах данных, примерно так же, что изменения данных в таблице в любой базе данных. Процесс может включать Вставка, обновление и удаление записей в таблице. В форме привязкой к данным можно указать, какие поля являются изменяемых пользователем. В этом случае инфраструктура привязки данных обрабатывает все отслеживания изменений, чтобы изменения могли быть отправлены в базу данных более поздней версии. Если предполагается передавать эти изменения в базе данных программным способом внесения изменений в данных, необходимо использовать объекты и методы, выполняющие отслеживание изменений для вас.  
  
 Помимо изменения фактических данных, можно также выполнить запрос <xref:System.Data.DataTable> позволит возвращать конкретные строки данных. Например вы может запрашивать отдельных строк, определенных версий строк (исходное и предложенное), строк, которые были изменены или строки, содержащие ошибки.  
  
## <a name="to-edit-rows-in-a-dataset"></a>Для изменения строк в наборе данных  
 Чтобы изменить существующую строку в <xref:System.Data.DataTable>, вам нужно найти <xref:System.Data.DataRow> вы хотите изменить, а затем назначьте обновленные значения в столбцах.  
  
 Если вы не знаете индекс строки, вы хотите изменить, используйте `FindBy` метод для поиска по первичному ключу:  
  
 [!code-csharp[VbRaddataEditing#3](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#3)]
 [!code-vb[VbRaddataEditing#3](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#3)]  
  
 Если вы знаете индекс строки, вы может получить доступ к и изменяет строк следующим образом:  
  
 [!code-csharp[VbRaddataEditing#5](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#5)]
 [!code-vb[VbRaddataEditing#5](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#5)]  
  
## <a name="to-insert-new-rows-into-a-dataset"></a>Для вставки новых строк в набор данных  
 Приложения, использующие элементы управления с привязкой к данным обычно Добавление новых записей с помощью **Add New** кнопку [элемент управления BindingNavigator](https://msdn.microsoft.com/library/18c1e2a5-9834-40d3-9b2e-2b545e4e769e).  
  
 Чтобы вручную добавить новые записи в набор данных, создания новой строки данных путем вызова метода в таблице. Затем добавьте строки <xref:System.Data.DataRow> коллекции (<xref:System.Data.DataTable.Rows%2A>) из <xref:System.Data.DataTable>:  
  
 [!code-csharp[VbRaddataEditing#1](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#1)]
 [!code-vb[VbRaddataEditing#1](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#1)]  
  
 Для сохранения сведений, что набор данных требуется для отправки обновлений в источник данных, используйте <xref:System.Data.DataRow.Delete%2A> метод для удаления строк в таблице данных. Например, если приложение использует адаптер таблицы (или <xref:System.Data.Common.DataAdapter>), TableAdapter `Update` метод удаляет строки в базе данных, имеющие <xref:System.Data.DataRow.RowState%2A> из <xref:System.Data.DataRowState>.  
  
 Если приложение не требуется отправлять обновления обратно к источнику данных, то это можно удалить записи путем прямого доступа к коллекции строк данных (<xref:System.Data.DataRowCollection.Remove%2A>).  
  
#### <a name="to-delete-records-from-a-data-table"></a>Для удаления записей из таблицы данных  
  
- Вызовите <xref:System.Data.DataRow.Delete%2A> метод <xref:System.Data.DataRow>.  
  
     Этот метод не удаляет записи физически. Вместо этого он помечает записи для удаления.  
  
    > [!NOTE]
    > Если вы получаете свойство count <xref:System.Data.DataRowCollection>, результирующее значение включает записи, которые были помечены для удаления. Чтобы получить точное число записей, которые не помечены для удаления, можно организовать цикл по коллекции, просмотрев <xref:System.Data.DataRow.RowState%2A> свойство каждой записи. (Имеют помеченные на удаление записи <xref:System.Data.DataRow.RowState%2A> из <xref:System.Data.DataRowState>.) Кроме того можно создать представление данных набора данных, фильтры на основе состояния строки и получить свойство count оттуда.  
  
     В следующем примере показан вызов <xref:System.Data.DataRow.Delete%2A> метод, чтобы пометить первую строку в `Customers` таблицу как удаленный:  
  
     [!code-csharp[VbRaddataEditing#8](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#8)]
     [!code-vb[VbRaddataEditing#8](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#8)]  
  
## <a name="determine-if-there-are-changed-rows"></a>Определить наличие измененных строк  
 При изменении записей в наборе данных, сведения об этих изменениях хранятся до их фиксации. Внесенные изменения фиксируются при вызове `AcceptChanges` метод таблицы набора данных или данных, или при вызове `Update` метод адаптера TableAdapter или данных.  
  
 Изменения отслеживаемых двумя способами в каждой строке данных.  
  
- Каждая строка данных содержит сведения, относящиеся к его <xref:System.Data.DataRow.RowState%2A> (например, <xref:System.Data.DataRowState>, <xref:System.Data.DataRowState>, <xref:System.Data.DataRowState>, или <xref:System.Data.DataRowState>).  
  
- Каждая строка измененных данных содержит несколько версий этой строки (<xref:System.Data.DataRowVersion>), исходной версии (до изменений) и текущей версии (после изменений). В течение периода, если ожидается изменение (время, когда можно ответить на <xref:System.Data.DataTable.RowChanging> событий) третья версия — предложенная — также доступен.
  
  <xref:System.Data.DataSet.HasChanges%2A> Метод набора данных возвращает `true` Если были внесены изменения в наборе данных. После определения существования измененных строк, можно вызвать `GetChanges` метод <xref:System.Data.DataSet> или <xref:System.Data.DataTable> для возвращения набора измененных строк. Дополнительные сведения см. в разделе [Практическое руководство. Получение измененных строк](https://msdn.microsoft.com/library/6ff0cbd0-5253-48e7-888a-144d56c2e0a9).  
  
#### <a name="to-determine-if-changes-have-been-made-to-any-rows"></a>Чтобы определить, были ли внесены изменения в строки  
  
- Вызовите <xref:System.Data.DataSet.HasChanges%2A> метод набора данных для проверки измененных строк.  
  
     Приведенный ниже показано, как проверить значение, возвращаемое <xref:System.Data.DataSet.HasChanges%2A> метод для выявления измененных строк в наборе данных с именем `NorthwindDataset1`:  
  
     [!code-csharp[VbRaddataEditing#12](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#12)]
     [!code-vb[VbRaddataEditing#12](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#12)]  
  
## <a name="determine-the-type-of-changes"></a>Определить тип изменений  
 Вы также можете проверить, чтобы увидеть, какой тип изменения были внесены в наборе данных, передав значение из <xref:System.Data.DataRowState> перечисления <xref:System.Data.DataSet.HasChanges%2A> метод.  
  
#### <a name="to-determine-what-type-of-changes-have-been-made-to-a-row"></a>Чтобы определить тип изменений были внесены в строку  
  
- Передайте <xref:System.Data.DataRowState> значение <xref:System.Data.DataSet.HasChanges%2A> метод.  
  
     В следующем примере показано, как проверить набор данных с именем `NorthwindDataset1` для определения того, если к нему были добавлены все новые строки:  
  
     [!code-csharp[VbRaddataEditing#13](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#13)]
     [!code-vb[VbRaddataEditing#13](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#13)]  
  
## <a name="to-locate-rows-that-have-errors"></a>Чтобы найти строки, содержащие ошибки  
 При работе с отдельных столбцов и строк данных, могут возникнуть ошибки. Вы можете проверить `HasErrors` свойства, чтобы определить наличие ошибок <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, или <xref:System.Data.DataRow>.  
  
1. Проверьте `HasErrors` свойство, чтобы увидеть, если в наборе данных имеются ошибки.  
  
2. Если `HasErrors` свойство `true`, итерации по коллекции таблиц, а затем через строки, чтобы найти строку с ошибкой.  
  
     [!code-csharp[VbRaddataEditing#23](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#23)]
     [!code-vb[VbRaddataEditing#23](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#23)]
