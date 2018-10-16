---
title: 'Практическое: Создание и выполнение инструкций SQL, не возвращающих значения | Документация Майкрософт'
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
- method calls, examples
- calling methods, examples
- SQL statements, executing
- SQL statements, creating
ms.assetid: 612d3046-0cfa-4d90-be6e-c4d6bcbd5aee
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 1768db097d2555726b17862c9c4a4b82a3e2a6a8
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49188608"
---
# <a name="how-to-create-and-execute-an-sql-statement-that-returns-no-value"></a>Практическое руководство. Создание и выполнение инструкций SQL, не возвращающих значения
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Для выполнения инструкции SQL, не возвращающих значения, можно запустить запрос TableAdapter, который настроен для выполнения инструкции SQL (например, `CustomersTableAdapter.UpdateTableData(CustomersDataTable)`).  
  
 Если приложение не использует адаптеры таблиц, вызовите `ExecuteNonQuery` метод объекта команды, присвоив его `CommandType` свойства <xref:System.Data.CommandType>. («Объект команды» относится к определенной команды для [поставщик данных .NET Framework](http://msdn.microsoft.com/library/03a9fc62-2d24-491a-9fe6-d6bdb6dcb131) используемого приложением. Например, если приложение использует поставщик данных .NET Framework для SQL Server, объект команды будет <xref:System.Data.SqlClient.SqlCommand>.)  
  
 В следующих примерах показано выполнение инструкций SQL, которые не возвращают значений из базы данных с помощью адаптеров таблиц или объектов команд. Дополнительные сведения о запросах с адаптеров таблиц TableAdapter и команд, см. в разделе [заполнения набора данных с помощью адаптера таблицы](../data-tools/fill-datasets-by-using-tableadapters.md).  
  
## <a name="executing-sql-statements-that-return-no-values-using-a-tableadapter"></a>Выполнение инструкций SQL, которые не возвращают никаких значений, с помощью адаптера таблицы  
 В этом примере показано, как создание запроса адаптера таблицы с помощью [редактирования TableAdapters](../data-tools/editing-tableadapters.md), а также приводятся сведения о том, как объявить экземпляр адаптера таблицы и выполнить запрос.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
#### <a name="to-create-an-sql-statement-that-returns-no-value-using-a-tableadapter"></a>Чтобы создать инструкцию SQL, не возвращающей значения с помощью адаптера таблицы  
  
1.  Откройте набор данных в **конструктор наборов данных**. Дополнительные сведения см. в разделе [как: Открытие набора данных в конструкторе наборов данных](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).  
  
2.  Если вы не еще нет, создайте адаптера таблицы. Дополнительные сведения о создании адаптеров таблиц см. в разделе [Создание и настройка адаптеров таблиц](../data-tools/create-and-configure-tableadapters.md).  
  
3.  Если уже имеется запрос, использующий инструкцию SQL, не возвращающих значения адаптера, перейдите к следующему этапу, «объявление экземпляра адаптера таблицы и выполнить запрос». В противном случае перейдите к шагу 4, чтобы создать новый запрос, не возвращающих значения.  
  
4.  Щелкните правой кнопкой мыши TableAdapter, который будет и используйте контекстное меню для добавления запроса.  
  
     **Мастер настройки запроса TableAdapter** открывает.  
  
5.  Оставьте значение по умолчанию **использовать инструкции SQL**, а затем нажмите кнопку **Далее**.  
  
6.  Выберите **обновление**, **вставить** или **удалить** , а затем щелкните **Далее**.  
  
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
        >  Адаптеры таблицы на самом деле не располагаются внутри своих классов связанного набора данных. Каждый набор данных имеет соответствующую коллекцию адаптеров таблиц TableAdapter в своем собственном пространстве имен. Например, если у вас есть набор данных с именем `SalesDataSet`, будет `SalesDataSetTableAdapters` пространство имен, содержащее его адаптеры таблиц.  
  
2.  Вызовите запрос, как и любой другой метод в коде. Запрос — это метод в TableAdapter. Замените следующий код с именами адаптера таблицы и имя запроса. Необходимо также передать параметры, необходимые запросу. Если вы не уверены в том случае, если запрос требует параметров, какие параметры требуются, затем проверить IntelliSense обязательную сигнатуру запроса. В зависимости от того, является ли запрос использует параметры, или нет код будет выглядеть похожее на одно из следующих примеров:  
  
     `TableAdapter.Query()`  
  
     `TableAdapter.Query(Parameters)`  
  
     Запросы, которые мы рассматривали как не возвращающей никакого значения, в действительности возвращают значение — целое число, содержащее количество строк, затронутых запросом. Полный код для объявления экземпляра адаптера таблицы и выполнить запрос должен выглядеть следующим образом:  
  
     [!code-csharp[VbRaddataFillingAndExecuting#11](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form2.cs#11)]
     [!code-vb[VbRaddataFillingAndExecuting#11](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form2.vb#11)]  
  
## <a name="executing-sql-statements-that-return-no-value-using-a-command-object"></a>Выполнение инструкций SQL, не возвращающих никаких значений, с помощью объекта команды  
 Приведенный ниже показано, как создать команду и выполнение инструкций SQL, не возвращающих значения. Сведения об установке и получении значения параметров для команды, см. в разделе [как: набор и получение параметров командных объектов](http://msdn.microsoft.com/library/10110ecc-d2ed-4796-bb8f-74f2ecd40787).  
  
 В этом примере используется <xref:System.Data.SqlClient.SqlCommand> объекта и требуется:  
  
-   Ссылки на <xref:System>, <xref:System.Data>, и <xref:System.Xml> пространства имен.  
  
-   Подключение к данным с именем `SqlConnection1`.  
  
-   Таблица с именем `Customers` в источнике данных, `SqlConnection1` подключается к. (В противном случае потребуется допустимую инструкцию SQL для источника данных).  
  
#### <a name="to-execute-an-sql-statement-that-returns-no-value-using-a-datacommand"></a>Чтобы выполнить инструкцию SQL, не возвращающей значения с помощью DataCommand  
  
-   Добавьте следующий код в метод, который вы хотите выполнить инструкцию SQL из. Вызовите `ExecuteNonQuery` метод команды нет значения (например, <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A?displayProperty=fullName>).  
  
     [!code-csharp[VbRaddataFillingAndExecuting#12](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form2.cs#12)]
     [!code-vb[VbRaddataFillingAndExecuting#12](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form2.vb#12)]  
  
## <a name="net-framework-security"></a>Безопасность платформы .NET Framework  
 Приложению требуется разрешение на доступ к базе данных и выполнение инструкции SQL.  
  
## <a name="see-also"></a>См. также  
 <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A?displayProperty=fullName>   
 <xref:System.Data.OleDb.OleDbCommand.ExecuteNonQuery%2A?displayProperty=fullName>   
 <xref:System.Data.Odbc.OdbcCommand.ExecuteNonQuery%2A?displayProperty=fullName>   
 <xref:System.Data.OracleClient.OracleCommand.ExecuteNonQuery%2A?displayProperty=fullName>   
 [Практическое: создание запросов TableAdapter](../data-tools/how-to-create-tableadapter-queries.md)   
 [Практическое: изменение запросов TableAdapter](../data-tools/how-to-edit-tableadapter-queries.md)   
 [Практическое: заполнения набора данных с данными](../data-tools/how-to-fill-a-dataset-with-data.md)   
 [Заполнение наборов данных с помощью адаптера таблицы](../data-tools/fill-datasets-by-using-tableadapters.md)   
 [Практическое: Установка и получение параметров командных объектов](http://msdn.microsoft.com/library/10110ecc-d2ed-4796-bb8f-74f2ecd40787)