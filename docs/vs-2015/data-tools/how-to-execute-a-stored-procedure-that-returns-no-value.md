---
title: 'Практическое: выполнение хранимой процедуры, не возвращающей значения | Документация Майкрософт'
ms.custom: ''
ms.date: 2018-06-30
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
- ExecuteNonQuery method
- stored procedures, creating
- stored procedures, executing
ms.assetid: 8a929e96-2cf5-43a5-b5b7-c0a5a397bbc5
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 0a9c80f37e5d569fd3a257f678256f01aba44925
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47572138"
---
# <a name="how-to-execute-a-stored-procedure-that-returns-no-value"></a>Практическое руководство. Выполнение хранимой процедуры, не возвращающей значения
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Чтобы выполнить хранимую процедуру, которая не возвращает значение, можно выполнить запрос TableAdapter, настроенный для запуска хранимой процедуры (например, `CustomersTableAdapter.UpdateTableData(CustomersDataTable)`).  
  
 Если приложение не использует адаптеры таблиц, вызовите `ExecuteNonQuery` метод объекта команды, присвоив его `CommandType` свойства <xref:System.Data.CommandType>. («Объект команды» относится к определенной команды для [поставщик данных .NET Framework](http://msdn.microsoft.com/library/03a9fc62-2d24-491a-9fe6-d6bdb6dcb131) используемого приложением. Например, если приложение использует поставщик данных .NET Framework для SQL Server, то объект команды будет <xref:System.Data.SqlClient.SqlCommand>.)  
  
 В следующих примерах показано выполнение хранимых процедур, которые не возвращают значений из базы данных с помощью адаптеров таблиц или объектов команд. Дополнительные сведения о запросах с адаптеров таблиц TableAdapter и команд, см. в разделе [заполнения набора данных с помощью адаптера таблицы](../data-tools/fill-datasets-by-using-tableadapters.md).  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="executing-stored-procedures-that-return-no-values-using-a-tableadapter"></a>Выполнение хранимых процедур, которые не возвращают никаких значений, с помощью адаптера таблицы  
 В этом примере показано, как создание запроса адаптера таблицы с помощью [редактирования TableAdapters](../data-tools/editing-tableadapters.md), а также приводятся сведения о том, как объявить экземпляр адаптера таблицы и выполнить запрос.  
  
#### <a name="to-create-a-stored-procedure-that-returns-no-value-using-a-tableadapter"></a>Чтобы создать хранимую процедуру, которая не возвращает значение с помощью адаптера таблицы  
  
1.  Откройте набор данных в **конструктор наборов данных**. Дополнительные сведения см. в разделе [как: Открытие набора данных в конструкторе наборов данных](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).  
  
2.  Если вы не еще нет, создайте адаптера таблицы. Дополнительные сведения о создании адаптеров таблиц см. в разделе [Создание и настройка адаптеров таблиц](../data-tools/create-and-configure-tableadapters.md).  
  
3.  Если вас уже есть запрос на адаптер таблицы, использует хранимую процедуру, которая не возвращает значение, перейдите к следующей процедуре «для объявления экземпляра адаптера таблицы и выполнить запрос». В противном случае перейдите к шагу 4, чтобы создать новый запрос, не возвращающих значения.  
  
4.  Щелкните правой кнопкой мыши TableAdapter, который будет и используйте контекстное меню для добавления запроса.  
  
     **Мастер настройки запроса TableAdapter** открывает.  
  
5.  Выберите **использовать существующую хранимую процедуру**, а затем нажмите кнопку **Далее**.  
  
6.  Выберите хранимую процедуру из раскрывающегося списка и нажмите кнопку **Далее**.  
  
7.  Выберите параметр, чтобы возвратить **значение не**, а затем нажмите кнопку **Далее**.  
  
8.  Укажите имя для запроса.  
  
9. Нажмите кнопку **Далее**, или **Готово** для завершения работы мастера; запрос добавляется в адаптер таблицы.  
  
10. Построить проект.  
  
#### <a name="to-declare-an-instance-of-the-tableadapter-and-execute-the-query"></a>Для объявления экземпляра адаптера таблицы и выполнения запроса  
  
1.  Объявите экземпляр адаптера таблицы, содержащий запрос, который требуется выполнить.  
  
    -   Для создания экземпляра с помощью средств разработки, перетащите TableAdapter из **элементов**. (Компоненты в проекте теперь отображаются в **элементов** под заголовком, совпадающим с именем проекта.) Если адаптер таблицы не отображается в **элементов**, возможно, потребуется выполнить сборку проекта.  
  
         - или -  
  
    -   Для создания экземпляра в коде, замените следующий код имена вашей <xref:System.Data.DataSet> и TableAdapter.  
  
         `Dim tableAdapter As New DataSetTableAdapters.TableAdapter`  
  
        > [!NOTE]
        >  Адаптеры таблицы на самом деле не располагаются внутри своих классов связанного набора данных. Каждый набор данных имеет соответствующую коллекцию адаптеров таблиц TableAdapter в своем собственном пространстве имен. Например, если у вас есть набор данных с именем `SalesDataSet`, а затем будет `SalesDataSetTableAdapters` пространство имен, содержащее его адаптеры таблиц.  
  
2.  Вызовите запрос, как и любой другой метод в коде. Запрос — это метод в TableAdapter. Замените следующий код с именами адаптера таблицы и имя запроса. Также необходимо будет передать параметры, необходимые запросу. Если вы не уверены в том случае, если запрос требует параметров, какие параметры требуются, затем проверить IntelliSense обязательную сигнатуру запроса. В зависимости от того, является ли запрос использует параметры, или нет код будет выглядеть похожее на одно из следующих примеров:  
  
     `TableAdapter.Query()`  
  
     `TableAdapter.Query(Parameters)`  
  
     Полный код для объявления экземпляра адаптера таблицы и выполнить запрос должен выглядеть следующим образом:  
  
     [!code-csharp[VbRaddataFillingAndExecuting#11](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form2.cs#11)]
     [!code-vb[VbRaddataFillingAndExecuting#11](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form2.vb#11)]  
  
## <a name="executing-stored-procedures-that-return-no-value-using-a-command-object"></a>Выполнение хранимых процедур, которые не возвращают значений с помощью объекта команды  
 Приведенный ниже показано, как создать команду и выполните хранимую процедуру, которая не возвращает значения. Сведения об установке и получении значения параметров для команды, см. в разделе [как: набор и получение параметров командных объектов](http://msdn.microsoft.com/library/10110ecc-d2ed-4796-bb8f-74f2ecd40787).  
  
 В этом примере используется <xref:System.Data.SqlClient.SqlCommand> объекта и требуется:  
  
-   Ссылки на <xref:System>, <xref:System.Data>, и <xref:System.Xml> пространства имен.  
  
#### <a name="to-execute-a-stored-procedure-that-returns-no-value-using-a-datacommand"></a>Чтобы выполнить хранимую процедуру, которая не возвращает значение с помощью DataCommand  
  
-   Добавьте следующий код в метод, который вы хотите выполнить хранимую процедуру из. Вызовите `ExecuteNonQuery` метод команды нет значения (например, <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A>).  
  
     [!code-csharp[VbRaddataFillingAndExecuting#15](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form2.cs#15)]
     [!code-vb[VbRaddataFillingAndExecuting#15](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form2.vb#15)]  
  
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