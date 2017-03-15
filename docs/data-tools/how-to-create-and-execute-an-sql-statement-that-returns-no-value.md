---
title: "Практическое руководство. Создание и выполнение инструкций SQL, не возвращающих значения | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "вызов методов, примеры"
  - "вызовы метода, примеры"
  - "инструкции SQL, создание"
  - "инструкции SQL, выполнение"
ms.assetid: 612d3046-0cfa-4d90-be6e-c4d6bcbd5aee
caps.latest.revision: 23
caps.handback.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Практическое руководство. Создание и выполнение инструкций SQL, не возвращающих значения
Для выполнения инструкции SQL, не возвращающей значения, можно запустить запрос адаптера таблицы TableAdapter, настроенный для выполнения инструкции SQL \(например `CustomersTableAdapter.UpdateTableData(CustomersDataTable)`\).  
  
 Если приложение не использует адаптеры таблиц TableAdapter, вызовите метод `ExecuteNonQuery` объекта команды, присвоив его свойству `CommandType` значение <xref:System.Data.CommandType>.  \("Объектом команды" называется определенная команда для [поставщика данных платформы .NET Framework](../Topic/.NET%20Framework%20Data%20Providers.md), используемого приложением.  Например, если приложение использует поставщик данных платформы .NET Framework для SQL Server, объектом команды будет <xref:System.Data.SqlClient.SqlCommand>\).  
  
 В следующих примерах показано, как с помощью адаптеров таблиц TableAdapter или объектов команд выполнить инструкции SQL, не возвращающие значений.  Дополнительные сведения о запросах с использованием адаптеров таблиц и команд содержатся в разделе [Заполнение набора данных](../data-tools/fill-datasets-by-using-tableadapters.md).  
  
## Выполнение инструкций SQL, не возвращающих значений, с помощью адаптера таблицы TableAdapter  
 В этом примере показано создание запроса адаптера таблицы с помощью [мастер настройки запроса TableAdapter](../data-tools/editing-tableadapters.md), а также приводятся сведения об объявлении экземпляра адаптера таблицы и выполнении запроса.  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### Чтобы создать инструкцию SQL, не возвращающую значения, с помощью адаптера таблицы TableAdapter  
  
1.  Откройте набор данных в **Конструкторе наборов данных**.  Дополнительные сведения см. в разделе [Практическое руководство. Открытие набора данных в конструкторе наборов данных](../Topic/How%20to:%20Open%20a%20Dataset%20in%20the%20Dataset%20Designer.md).  
  
2.  Создайте адаптер таблицы, если не сделали этого ранее.  Дополнительные сведения о создании адаптеров таблиц см. в разделе [Практическое руководство. Создание адаптера таблицы](../data-tools/create-and-configure-tableadapters.md).  
  
3.  Если в адаптере таблицы TableAdapter уже имеется запрос, использующий инструкцию SQL, не возвращающую значение, то перейдите к процедуре "Чтобы объявить экземпляр адаптера таблиц TableAdapter и выполнить запрос". В противном случае необходимо продолжить выполнение шага 4, чтобы создать новый запрос, не возвращающий значение.  
  
4.  Щелкните требуемый адаптер таблиц правой кнопкой мыши и используйте контекстное меню для добавления запроса.  
  
     Откроется **Мастер настройки запроса адаптера таблицы**.  
  
5.  Оставьте значение по умолчанию для элемента **Использовать SQL\-инструкции** и нажмите кнопку **Далее**.  
  
6.  Выберите параметр **UPDATE**, **INSERT** или **DELETE** и нажмите кнопку **Далее**.  
  
7.  Введите инструкцию SQL или воспользуйтесь **Построителем запросов** для упрощения создания, затем нажмите кнопку **Далее**.  
  
8.  Введите имя для запроса.  
  
9. Завершите работу мастера; запрос добавляется к адаптеру таблицы.  
  
10. Построить проект.  
  
#### Чтобы объявить экземпляр адаптера таблиц и выполнить запрос:  
  
1.  Объявите экземпляр адаптера таблиц, содержащий запрос, который требуется выполнить.  
  
    -   Для создания экземпляра с помощью средств времени проектирования, перетащите нужный адаптер таблицы TableAdapter с **Панели элементов**.  \(Компонент в проекте теперь отображается в **Панели элементов** под заголовком, совпадающим с именем проекта.\) Если адаптер таблиц не отображается в **Панели элементов**, может потребоваться скомпилировать проект.  
  
         \-или\-  
  
    -   Чтобы создать экземпляр в коде, подставьте в следующий код имена <xref:System.Data.DataSet> и адаптера таблиц.  
  
         `Dim tableAdapter As New DataSetTableAdapters.TableAdapter`  
  
        > [!NOTE]
        >  Адаптеры таблиц на самом деле не располагаются внутри связанных с ними классов наборов данных.  Каждый набор данных имеет соответствующую коллекцию адаптеров таблиц в своих собственных пространствах имен.  Например, если у вас есть набор данных с именем `SalesDataSet`, то будет существовать пространство имен `SalesDataSetTableAdapters`, содержащее его адаптеры таблиц.  
  
2.  Вызовите запрос, как вызвали бы любой другой метод в коде.  Запрос представляет собой метод адаптера таблиц.  Подставьте в следующий код имя адаптера таблиц и имя запроса.  Кроме того, необходимо передать параметры, требуемые запросом.  Если вы не уверены в том, что запросу необходимы параметры, и какие именно параметры требуются, то проверьте в IntelliSense требуемую сигнатуру запроса.  В зависимости то того, принимает ли запрос параметры или нет, код будет выглядеть аналогично одному из следующих примеров:  
  
     `TableAdapter.Query()`  
  
     `TableAdapter.Query(Parameters)`  
  
     Запросы, которые мы рассматривали как не возвращающие значений, на самом деле возвращают значение — целое число, содержащее число строк, затронутых запросом.  Полный код объявления экземпляра адаптера таблицы TableAdapter и выполнения запроса должен выглядеть примерно следующим образом:  
  
     [!code-cs[VbRaddataFillingAndExecuting#11](../data-tools/codesnippet/CSharp/how-to-create-and-execute-an-sql-statement-that-returns-no-value_1.cs)]
     [!code-vb[VbRaddataFillingAndExecuting#11](../data-tools/codesnippet/VisualBasic/how-to-create-and-execute-an-sql-statement-that-returns-no-value_1.vb)]  
  
## Выполнение инструкций SQL, не возвращающих значений, с помощью объекта команды  
 В следующем примере демонстрируется способ создания команды и выполнения инструкции SQL, не возвращающей значения.  Сведения об установке и получении значений параметров для команды см. в разделе [Практическое руководство. Установка и получение параметров командных объектов](../Topic/How%20to:%20Set%20and%20Get%20Parameters%20for%20Command%20Objects.md).  
  
 Этот пример использует объект <xref:System.Data.SqlClient.SqlCommand> и требует:  
  
-   Ссылки на пространства имен <xref:System>, <xref:System.Data> и <xref:System.Xml>.  
  
-   Подключение к данным с именем `SqlConnection1`.  
  
-   Таблицу с именем `Customers` в источнике данных, к которому подключается `SqlConnection1`.  \(В противном случае необходима допустимая инструкция SQL для источника данных\).  
  
#### Чтобы выполнить инструкцию SQL, не возвращающую значения, с помощью объекта DataCommand  
  
-   Добавьте следующий код к методу, из которого должна выполняться инструкция SQL.  Вызовите метод `ExecuteNonQuery` команды без возврата значения \(например <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A?displayProperty=fullName>\).  
  
     [!code-cs[VbRaddataFillingAndExecuting#12](../data-tools/codesnippet/CSharp/how-to-create-and-execute-an-sql-statement-that-returns-no-value_2.cs)]
     [!code-vb[VbRaddataFillingAndExecuting#12](../data-tools/codesnippet/VisualBasic/how-to-create-and-execute-an-sql-statement-that-returns-no-value_2.vb)]  
  
## Безопасность платформы .NET Framework  
 Для доступа к базе данных и выполнения инструкции SQL приложению требуется разрешение.  
  
## См. также  
 <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A?displayProperty=fullName>   
 <xref:System.Data.OleDb.OleDbCommand.ExecuteNonQuery%2A?displayProperty=fullName>   
 <xref:System.Data.Odbc.OdbcCommand.ExecuteNonQuery%2A?displayProperty=fullName>   
 <xref:System.Data.OracleClient.OracleCommand.ExecuteNonQuery%2A?displayProperty=fullName>   
 [Практическое руководство. Создание запросов TableAdapter](../data-tools/how-to-create-tableadapter-queries.md)   
 [Практическое руководство. Изменение запросов TableAdapter](../data-tools/how-to-edit-tableadapter-queries.md)   
 [Практическое руководство. Заполнение данными набора данных](../data-tools/how-to-fill-a-dataset-with-data.md)   
 [Заполнение набора данных](../data-tools/fill-datasets-by-using-tableadapters.md)   
 [Практическое руководство. Установка и получение параметров командных объектов](../Topic/How%20to:%20Set%20and%20Get%20Parameters%20for%20Command%20Objects.md)