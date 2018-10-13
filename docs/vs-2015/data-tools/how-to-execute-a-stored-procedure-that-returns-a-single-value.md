---
title: 'Практическое: выполнение хранимой процедуры, возвращающей одиночное значение | Документация Майкрософт'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CommandType.StoredProcedure
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- ExecuteReader method example [Visual Basic]
- stored procedures, examples
- stored procedures, executing
ms.assetid: ecf8c262-58ca-4a69-a82c-916c0c061422
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 2c27c8e0fca1393e097f1244a01988052911f73a
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49281012"
---
# <a name="how-to-execute-a-stored-procedure-that-returns-a-single-value"></a>Практическое руководство. Выполнение хранимой процедуры, возвращающей одиночное значение
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Для выполнения хранимой процедуры, возвращающей одиночное значение, можно запустить запрос TableAdapter, который настроен для запуска хранимой процедуры (например, `CustomersTableAdapter.CustomerCount()`).  
  
 Если приложение не использует адаптеры таблиц, вызовите `ExecuteScalar` метод объекта команды, присвоив его `CommandType` свойства <xref:System.Data.CommandType>. («Объект команды» относится к определенной команды для [поставщик данных .NET Framework](http://msdn.microsoft.com/library/03a9fc62-2d24-491a-9fe6-d6bdb6dcb131) используемого приложением. Например, если приложение использует поставщик данных .NET Framework для SQL Server, объект команды будет <xref:System.Data.SqlClient.SqlCommand>.)  
  
 Следующие примеры показывают, как выполнять хранимые процедуры, возвращающей одиночное значение из базы данных с помощью адаптеров таблиц или объектов команд. Дополнительные сведения о запросах с адаптеров таблиц TableAdapter и команд, см. в разделе [заполнения набора данных с помощью адаптера таблицы](../data-tools/fill-datasets-by-using-tableadapters.md).  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="executing-stored-procedures-that-return-single-values-using-a-tableadapter"></a>Выполнение хранимых процедур, которые возвращают одиночное значение, с помощью адаптера таблицы  
 В этом примере показано, как создание запроса адаптера таблицы с помощью [редактирования TableAdapters](../data-tools/editing-tableadapters.md), а также приводятся сведения о том, как объявить экземпляр адаптера таблицы и выполнить запрос.  
  
#### <a name="to-execute-a-stored-procedure-that-returns-a-single-value-using-a-tableadapter"></a>Для выполнения хранимой процедуры, возвращающей одиночное значение, с помощью адаптера таблицы  
  
1.  Откройте набор данных в **конструктор наборов данных**. Дополнительные сведения см. в разделе [как: Открытие набора данных в конструкторе наборов данных](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).  
  
2.  Если вы не еще нет, создайте адаптера таблицы. Дополнительные сведения о создании адаптеров таблиц см. в разделе [Создание и настройка адаптеров таблиц](../data-tools/create-and-configure-tableadapters.md).  
  
3.  При наличии запроса адаптера, использующего хранимой процедуры для возврата одного значения, перейдите к следующему этапу, «объявление экземпляра адаптера таблицы и выполнить запрос». В противном случае перейдите к шагу 4, чтобы создать новый запрос, возвращающий одиночное значение.  
  
4.  Щелкните правой кнопкой мыши TableAdapter, который будет и используйте контекстное меню для добавления запроса.  
  
     **Мастер настройки запроса TableAdapter** открывает.  
  
5.  Выберите **использовать существующую хранимую процедуру**, а затем нажмите кнопку **Далее**.  
  
6.  Выберите хранимую процедуру из раскрывающегося списка и нажмите кнопку **Далее**.  
  
7.  Выберите параметр, чтобы возвратить **одно значение**, а затем нажмите кнопку **Далее**.  
  
8.  Укажите имя для запроса.  
  
9. Нажмите кнопку **Далее** или **Готово** для завершения работы мастера; запрос добавляется в адаптер таблицы.  
  
10. Построить проект.  
  
#### <a name="to-declare-an-instance-of-the-tableadapter-and-execute-the-query"></a>Для объявления экземпляра адаптера таблицы и выполнения запроса  
  
1.  Объявите экземпляр TableAdapter, который содержит запрос, который требуется выполнить.  
  
    -   Для создания экземпляра с помощью средств разработки, перетащите TableAdapter из **элементов**. (Компоненты в проекте теперь отображаются в **элементов** под заголовком, совпадающим с именем проекта.) Если адаптер таблицы не отображается в **элементов**, возможно, потребуется выполнить сборку проекта.  
  
         - или -  
  
    -   Для создания экземпляра в коде, замените следующий код имена вашей <xref:System.Data.DataSet> и TableAdapter.  
  
         `Dim tableAdapter As New DataSetTableAdapters.TableAdapter`  
  
        > [!NOTE]
        >  Адаптеры таблицы на самом деле не располагаются внутри своих классов связанного набора данных. Каждый набор данных имеет соответствующую коллекцию адаптеров таблиц TableAdapter в своем собственном пространстве имен. Например, если у вас есть набор данных с именем `SalesDataSet`, будет `SalesDataSetTableAdapters` пространство имен, содержащее его адаптеры таблиц.  
  
2.  Вызовите запрос, как и любой другой метод в коде. Запрос — это метод в TableAdapter. Замените следующий код с именами адаптера таблицы и имя запроса. Также необходимо будет передать параметры, необходимые запросу. Если вы не уверены в том случае, если запрос требует параметров, какие параметры требуются, затем проверить IntelliSense обязательную сигнатуру запроса. В зависимости от того, является ли запрос использует параметры, или нет код будет выглядеть похожее на одно из следующих примеров:  
  
     `TableAdapter.Query()`  
  
     `TableAdapter.Query(Parameters)`  
  
     Полный код для объявления экземпляра адаптера таблицы и выполнить запрос должен выглядеть следующим образом:  
  
     [!code-csharp[VbRaddataFillingAndExecuting#9](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form2.cs#9)]
     [!code-vb[VbRaddataFillingAndExecuting#9](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form2.vb#9)]  
  
## <a name="executing-stored-procedures-that-return-single-values-using-a-command-object"></a>Выполнение хранимых процедур, которые возвращают одиночное значение, с помощью объекта команды  
 В следующем примере показано, как для создания команды и выполнения хранимой процедуры, возвращающей одиночное значение. Сведения об установке и получении значения параметров для команды, см. в разделе [как: набор и получение параметров командных объектов](http://msdn.microsoft.com/library/10110ecc-d2ed-4796-bb8f-74f2ecd40787).  
  
 В этом примере используется <xref:System.Data.SqlClient.SqlCommand> объекта и требуется:  
  
-   Ссылки на <xref:System>, <xref:System.Data>, и <xref:System.Xml> пространства имен.  
  
-   Подключение к данным с именем `SqlConnection1`.  
  
-   Таблица с именем `Customers` в источнике данных, `SqlConnection1` подключается к. (В противном случае потребуется допустимую инструкцию SQL для источника данных).  
  
#### <a name="to-execute-a-stored-procedure-that-returns-a-single-value-using-a-datacommand"></a>Для выполнения хранимой процедуры, возвращающей одиночное значение, с помощью DataCommand  
  
-   Добавьте следующий код в метод, чтобы выполнить код из. Возвращать одиночные значения путем вызова `ExecuteScalar` метод команды (например, <xref:System.Data.SqlClient.SqlCommand.ExecuteScalar%2A>). Данные возвращаются в `object`.  
  
     [!code-csharp[VbRaddataFillingAndExecuting#14](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form2.cs#14)]
     [!code-vb[VbRaddataFillingAndExecuting#14](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form2.vb#14)]  
  
## <a name="see-also"></a>См. также  
 <xref:System.Data.SqlClient.SqlCommand.ExecuteScalar%2A?displayProperty=fullName>   
 <xref:System.Data.OleDb.OleDbCommand.ExecuteScalar%2A?displayProperty=fullName>   
 <xref:System.Data.Odbc.OdbcCommand.ExecuteScalar%2A?displayProperty=fullName>   
 <xref:System.Data.OracleClient.OracleCommand.ExecuteScalar%2A?displayProperty=fullName>   
 [Практическое: создание запросов TableAdapter](../data-tools/how-to-create-tableadapter-queries.md)   
 [Практическое: изменение запросов TableAdapter](../data-tools/how-to-edit-tableadapter-queries.md)   
 [Практическое: заполнения набора данных с данными](../data-tools/how-to-fill-a-dataset-with-data.md)   
 [Заполнение наборов данных с помощью адаптера таблицы](../data-tools/fill-datasets-by-using-tableadapters.md)   
 [Практическое: Установка и получение параметров командных объектов](http://msdn.microsoft.com/library/10110ecc-d2ed-4796-bb8f-74f2ecd40787)