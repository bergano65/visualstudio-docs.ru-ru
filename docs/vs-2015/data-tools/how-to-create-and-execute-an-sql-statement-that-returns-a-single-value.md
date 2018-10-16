---
title: 'Практическое: Создание и выполнение инструкций SQL, возвращающей одиночное значение | Документация Майкрософт'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data reader
- scalar values
- stored procedures, returning single value
- SQL statements, data commands
- DataReader object
- data commands, returning scalar values
ms.assetid: eb366496-69e5-4462-8683-653054165c5c
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 7d5d57637a25db62832ad535bbad60214a0aa4ad
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49192157"
---
# <a name="how-to-create-and-execute-an-sql-statement-that-returns-a-single-value"></a>Практическое руководство. Создание и выполнение инструкции SQL, возвращающей одиночное значение
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Для выполнения инструкции SQL, возвращающей одиночное значение, можно запустить запрос TableAdapter, который настроен для выполнения инструкции SQL (например, `CustomersTableAdapter.CustomerCount()`).  
  
 Если приложение не использует адаптеры таблиц, вызовите `ExecuteScalar` метод объекта команды, присвоив его `CommandType` свойства <xref:System.Data.CommandType>. («Объект команды» относится к определенной команды для [поставщик данных .NET Framework](http://msdn.microsoft.com/library/03a9fc62-2d24-491a-9fe6-d6bdb6dcb131) используемого приложением. Например, если приложение использует поставщик данных .NET Framework для SQL Server, объект команды будет <xref:System.Data.SqlClient.SqlCommand>.)  
  
 В следующих примерах показано выполнение инструкций SQL, возвращающей одиночное значение из базы данных с помощью адаптеров таблиц или объектов команд. Дополнительные сведения о запросах с адаптеров таблиц TableAdapter и команд, см. в разделе [заполнения набора данных с помощью адаптера таблицы](../data-tools/fill-datasets-by-using-tableadapters.md).  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="executing-sql-statements-that-return-single-values-using-a-tableadapter"></a>Выполнение инструкций SQL, которые возвращают одиночное значение, с помощью адаптера таблицы  
 В этом примере показано, как создание запроса адаптера таблицы с помощью [редактирования TableAdapters](../data-tools/editing-tableadapters.md), а также приводятся сведения о том, как объявить экземпляр адаптера таблицы и выполнить запрос.  
  
#### <a name="to-create-an-sql-statement-returning-a-single-value-using-a-tableadapter"></a>Чтобы создать инструкцию SQL, возвращающий единичное значение, с помощью адаптера таблицы  
  
1.  Откройте набор данных в **конструктор наборов данных**. Дополнительные сведения см. в разделе [как: Открытие набора данных в конструкторе наборов данных](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).  
  
2.  Если вы не еще нет, создайте адаптера таблицы. Дополнительные сведения о создании адаптеров таблиц см. в разделе [Создание и настройка адаптеров таблиц](../data-tools/create-and-configure-tableadapters.md).  
  
3.  Если вас уже есть запрос на адаптер таблицы, инструкция SQL используется для возвращения одиночного значения, затем переходите к следующему этапу, «объявление экземпляра адаптера таблицы и выполнить запрос». В противном случае перейдите к шагу 4, чтобы создать новый запрос, возвращающий одиночное значение.  
  
4.  Щелкните правой кнопкой мыши TableAdapter, который будет и используйте контекстное меню для добавления запроса.  
  
     **Мастер настройки запроса TableAdapter** открывает.  
  
5.  Оставьте значение по умолчанию **использовать инструкции SQL**, а затем нажмите кнопку **Далее**.  
  
6.  Выберите **SELECT, возвращающая одиночное значение** , а затем щелкните **Далее**.  
  
7.  Введите инструкцию SQL или используйте **построитель запросов** для упрощения создания, а затем нажмите кнопку **Далее**.  
  
8.  Укажите имя для запроса.  
  
9. Завершите работу мастера; запрос добавляется в адаптер таблицы.  
  
10. Построить проект.  
  
#### <a name="to-declare-an-instance-of-the-tableadapter-and-execute-the-query"></a>Для объявления экземпляра адаптера таблицы и выполнения запроса  
  
1.  Объявите экземпляр TableAdapter, который содержит запрос, который требуется выполнить.  
  
    -   Для создания экземпляра с помощью средств разработки, перетащите TableAdapter из **элементов**. (Компоненты в проекте теперь отображаются в **элементов** под заголовком, совпадающим с именем проекта.) Если адаптер таблицы не отображается в **элементов**, возможно, потребуется выполнить сборку проекта.  
  
         - или -  
  
    -   Для создания экземпляра в коде, замените следующий код имена вашей <xref:System.Data.DataSet> и TableAdapter.  
  
         `Dim tableAdapter As New DataSetTableAdapters.TableAdapter`  
  
        > [!NOTE]
        >  Адаптеры таблицы на самом деле не располагаются внутри своих классов связанного набора данных. Каждый набор данных имеет соответствующую коллекцию адаптеров таблиц TableAdapter в своем собственном пространстве имен. Например, если у вас есть набор данных с именем `SalesDataSet`, а затем будет `SalesDataSetTableAdapters` пространство имен, содержащее его адаптеры таблиц.  
  
2.  Вызовите запрос, как и любой другой метод в коде. Запрос — это метод в TableAdapter. Замените следующий код с именами адаптера таблицы и имя запроса. Необходимо также передать параметры, необходимые запросу и как-то возвращаемое значение (например, назначьте его переменной). Если вы не уверены в том случае, если запрос требует параметров, какие параметры требуются, затем проверить IntelliSense обязательную сигнатуру запроса. В зависимости от того, является ли запрос использует параметры, или нет код будет выглядеть похожее на одно из следующих примеров:  
  
     `TableAdapter.Query()`  
  
     `TableAdapter.Query(Parameters)`  
  
3.  Скорее всего, потребуется назначить значение, возвращаемое запросом к переменной. Запросы TableAdapter, возвращают одиночное значение возвращают тип данных, на основе запроса (в отличие от `ExecuteScalar` метод, возвращающий объект). Например если запрос TableAdapter выбирает один столбец, тип данных которого является целое число, возвращаемое значение запроса — это целое число. Если столбец допускает значения null, возвращаемое значение является одним из таких типов (например, `Nullable(Of Integer)`). Дополнительные сведения по обнуляемые типы, см. в разделе <xref:System.Nullable>. Полный код для объявления экземпляра адаптера таблицы и выполнить запрос должен выглядеть следующим образом (в этом примере предполагается, что возвращаемое значение должно быть целым числом; измените код в соответствии с типом данных, возвращенного запросом):  
  
     [!code-csharp[VbRaddataFillingAndExecuting#9](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form2.cs#9)]
     [!code-vb[VbRaddataFillingAndExecuting#9](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form2.vb#9)]  
  
## <a name="executing-sql-statements-that-return-single-values-using-a-command-object"></a>Выполнение инструкций SQL, которые возвращают одиночное значение, с помощью объекта команды  
 В следующем примере показано, как для создания команды и выполнения инструкции SQL, возвращающей одиночное значение. Сведения об установке и получении значения параметров для команды, см. в разделе [как: набор и получение параметров командных объектов](http://msdn.microsoft.com/library/10110ecc-d2ed-4796-bb8f-74f2ecd40787).  
  
 В этом примере используется <xref:System.Data.SqlClient.SqlCommand> объекта и требуется:  
  
-   Ссылки на <xref:System>, <xref:System.Data>, и <xref:System.Xml> пространства имен.  
  
-   Подключение к данным с именем `SqlConnection1`.  
  
-   Таблица с именем `Customers` в источнике данных, `SqlConnection1` подключается к. (В противном случае потребуется допустимую инструкцию SQL для источника данных).  
  
#### <a name="to-execute-an-sql-statement-returning-a-single-value-using-a-datacommand"></a>Чтобы выполнить инструкцию SQL, возвращающий единичное значение, с помощью DataCommand  
  
-   Добавьте следующий код в метод, чтобы выполнить код из. Возвращать одиночное значение путем вызова `ExecuteScalar` метод команды (например, <xref:System.Data.SqlClient.SqlCommand.ExecuteScalar%2A>). Данные возвращаются в <xref:System.Object>.  
  
     [!code-csharp[VbRaddataFillingAndExecuting#10](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form2.cs#10)]
     [!code-vb[VbRaddataFillingAndExecuting#10](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form2.vb#10)]  
  
## <a name="net-framework-security"></a>Безопасность платформы .NET Framework  
 Приложению требуется разрешение на доступ к базе данных и выполнение инструкции SQL.  
  
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