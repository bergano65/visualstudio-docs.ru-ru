---
title: Общие сведения о TableAdapter | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vbData.Microsoft.VSDesigner.DataSource.DataAccessor
- vbdata.Microsoft.VSDesigner.DataSource.DataAccessor
- TableAdapter
- vs.data.TableAdapter
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data [Visual Studio], table adapters
- TableAdapters, queries
- data [Visual Studio], TableAdapters
- query data in Visual Studio
- TableAdapter.GetData
- TableAdapter.Fill
- data [Visual Studio], datasets
- TableAdapters
- table adapters
ms.assetid: a87c46a0-52ab-432a-a864-9ba55069f9eb
caps.latest.revision: 40
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 1d5aabd4892011aa5c59abafc5d08840d1c8f5a8
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47570298"
---
# <a name="tableadapter-overview"></a>Общие сведения об адаптере таблиц
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Адаптеры таблиц — это автоматически созданный конструктором компонентов, соединиться с базой данных, выполнять запросы или хранимые процедуры и заполнить их DataTable с возвращенными данными. Адаптеры таблиц также используются для отправки обновленных данных из приложения в базе данных. Может иметь столько запросов, сколько требуется в TableAdapter, до тех пор, пока они возвращают данные, которые соответствуют схеме таблицы, с которой связан TableAdapter. На следующей схеме показано, как адаптеры таблиц взаимодействуют с базами данных и другими объектами в памяти:  
  
 ![Поток данных в клиентском приложении](../data-tools/media/clientdatadiagram.gif "ClientDataDiagram")  
  
 Если адаптеры таблиц создаются с помощью **конструктор наборов данных**, созданные классы адаптеров таблиц не создаются как вложенные классы <xref:System.Data.DataSet>. Они находятся в разных пространствах имен для каждого набора данных. Например, если у вас есть набор данных с именем `NorthwindDataSet`, адаптеры таблиц, связанные с <xref:System.Data.DataTable>s в `NorthwindDataSet` в `NorthwindDataSetTableAdapters` пространства имен. Для программного доступа к конкретному адаптеру таблиц, необходимо объявить новый экземпляр адаптера таблицы. Пример:  
  
 [!code-csharp[VbRaddataTableAdapters#7](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataTableAdapters/CS/Class1.cs#7)]
 [!code-vb[VbRaddataTableAdapters#7](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataTableAdapters/VB/Class1.vb#7)]  
  
## <a name="associated-datatable-schema"></a>Связанной схемы DataTable  
 При создании TableAdapter, начальный запрос или хранимая процедура используется для определения схемы TableAdapter, связанного с <xref:System.Data.DataTable>. Этот начальный запрос или хранимая процедура выполняются путем вызова метода `Fill` метода (который заполняет TableAdapter, связанного с <xref:System.Data.DataTable>). Любые изменения, внесенные в основном запросе TableAdapter, отражаются в схеме таблицы, связанные с ними данные. Например удаление столбца из основного запроса удаляет столбец из связанной таблицы данных. Если любых дополнительных запросов в адаптер таблицы использует инструкции SQL, возвращающие столбцы, которые не являются в основном запросе, конструктор попытается синхронизировать изменения столбцов между основным и любых дополнительных запросов. Дополнительные сведения см. в разделе [как: изменить адаптеры таблицы](http://msdn.microsoft.com/library/ca178745-e35a-45f1-a395-23cddfd8f855).  
  
## <a name="tableadapter-update-commands"></a>Команды обновления адаптера таблицы  
 Возможность обновления адаптера таблицы зависит от того, сколько информация доступна на основе основного запроса, указанный в мастере адаптера таблицы. Например адаптеры таблиц, настроенные для получения значения из нескольких таблиц (JOIN), скалярные значения, представления или результаты агрегатных функций изначально создаются с возможностью отправки обновлений в основную базу данных. Тем не менее, можно настроить вручную в команды INSERT, UPDATE и DELETE **свойства** окна.  
  
## <a name="tableadapter-queries"></a>Запросы адаптера таблиц  
 ![TableAdapter с несколькими запросами](../data-tools/media/tableadapter.gif "адаптера таблицы")  
  
 Адаптеры таблиц могут содержать несколько запросов для заполнения связанных таблиц. Можно определить столько запросов для TableAdapter вашему приложению до тех пор, пока каждый запрос возвращает данные, которые соответствуют той же схемы, как связанную таблицу данных. Это позволяет загружать данные, которые удовлетворяют различным критериям. Например если приложение содержит таблицу клиентов, можно создать запрос, который заполняет таблицу клиентов, чьи имена начинаются с определенной буквы и другой запрос, который заполняет таблицу со всех клиентов, находящихся в том же состоянии. Для заполнения `Customers` таблицы с клиентами в заданном состоянии, можно создать `FillByState` запрос, который принимает параметр для значения состояния: `SELECT * FROM Customers WHERE State = @State`. Запрос выполняется путем вызова `FillByState` и передав в значении параметра следующим образом: `CustomerTableAdapter.FillByState("WA")`. Дополнительные сведения см. в разделе [как: создание запросов TableAdapter](../data-tools/how-to-create-tableadapter-queries.md).  
  
 В дополнение к запросам, которые возвращают данные из той же схеме таблицы данных адаптера таблицы можно добавить запросы, возвращающие скалярные значения (одно). Например, создав запрос, который возвращает число клиентов (`SELECT Count(*) From Customers`) является допустимым для `CustomersTableAdapter` несмотря на то, что соответствует схеме таблицы возвращаются данные.  
  
## <a name="clearbeforefill-property"></a>Свойство ClearBeforeFill  
 По умолчанию каждый раз при выполнении запроса для заполнения таблицы данных адаптера данных очищается, и только результаты запроса будут загружены в таблице. Задайте `ClearBeforeFill` свойства `false` Если вы хотите добавить или объединять данные, возвращенные из запроса к существующим данным в таблице данных. Независимо от того, снят ли данные необходимо явно отправлять обновления в базе данных, при необходимости. Поэтому не забудьте сохранить любые изменения, вносимые в данные в таблице перед выполнением другой запрос, который заполняет таблицу. Дополнительные сведения см. в разделе [обновления данных с помощью адаптера таблицы](../data-tools/update-data-by-using-a-tableadapter.md).  
  
## <a name="tableadapter-inheritance"></a>Наследование адаптера таблицы  
 Адаптеры таблиц расширить функциональные возможности стандартных адаптеров данных за счет инкапсуляции настроенного <xref:System.Data.Common.DataAdapter>. По умолчанию TableAdapter наследует <xref:System.ComponentModel.Component> и не может быть приведен к <xref:System.Data.Common.DataAdapter> класса. Приведение TableAdapter для <xref:System.Data.Common.DataAdapter> приводит <xref:System.InvalidCastException>. Чтобы изменить базовый класс адаптера таблицы, можно ввести класс, производный от <xref:System.ComponentModel.Component> в **базового класса** свойство TableAdapter в **конструктор наборов данных**.  
  
## <a name="tableadapter-methods-and-properties"></a>Свойства и методы адаптера таблицы  
 Класс TableAdapter не является частью [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], и его не удается найти в документации или **обозреватель объектов**. Она создается во время разработки, при использовании одного из мастеров, упомянутых выше. Имя, присвоенное адаптера таблицы при ее создании основан на имени таблицы, в которой вы работаете. Например, если Создание адаптера таблицы на основе таблицы в базе данных с именем `Orders`, TableAdapter будет называться `OrdersTableAdapter`. Имя класса адаптера таблицы можно изменить с помощью **имя** свойство в **конструктор наборов данных**.  
  
 Ниже перечислены часто используемые методы и свойства TableAdapters.  
  
|Член|Описание|  
|------------|-----------------|  
|`TableAdapter.Fill`|Заполняет таблицу результатов команды SELECT адаптера таблицы TableAdapter связанные данные. Дополнительные сведения см. в разделе [как: заполнения набора данных с данными](../data-tools/how-to-fill-a-dataset-with-data.md).|  
|`TableAdapter.Update`|Отправляет изменения обратно в базу данных и возвращает целое число, представляющее число строк, затронутых обновлением. Дополнительные сведения см. в разделе [обновления данных с помощью адаптера таблицы](../data-tools/update-data-by-using-a-tableadapter.md).|  
|`TableAdapter.GetData`|Возвращает новый <xref:System.Data.DataTable> заполненный данными.|  
|`TableAdapter.Insert`|Создает новую строку в таблице данных. Дополнительные сведения см. в разделе [как: Добавление строк в таблицу данных](http://msdn.microsoft.com/library/78ebbb43-c402-49cf-81da-0715289487bf).|  
|`TableAdapter.ClearBeforeFill`|Определяет, очищается ли таблица данных перед вызовом одного из `Fill` методы.|  
  
## <a name="tableadapter-update-method"></a>Метод обновления адаптера таблицы  
 TableAdapters команды данных для чтения и записи из базы данных. TableAdapter начальной `Fill` (основной) запрос используется в качестве основы для создания схемы связанной таблицы данных, а также `InsertCommand`, `UpdateCommand`, и `DeleteCommand` команды, связанные с `TableAdapter.Update` метод. Это означает, что вызов адаптера `Update` метод выполняет инструкции, созданные при первоначальной настройке адаптера, и ни один из дополнительные запросы, которые добавлены с классом **мастер настройки запроса TableAdapter**.  
  
 При использовании адаптера таблицы, она фактически выполняет те же операции, с помощью команд, которые обычно выполняются. Например, при вызове адаптера `Fill` метод, адаптер выполняет команду в его `SelectCommand` свойство и использует модуль чтения данных (например, <xref:System.Data.SqlClient.SqlDataReader>) для загрузки результирующего набора в таблице данных. Аналогично, при вызове адаптера `Update` метод, он выполняет соответствующую команду (в `UpdateCommand`, `InsertCommand`, и `DeleteCommand` свойства) для каждой измененной записи в таблице данных.  
  
> [!NOTE]
>  Если имеется достаточно сведений в основном запросе `InsertCommand`, `UpdateCommand`, и `DeleteCommand` команды создаются по умолчанию при создании адаптера таблицы. Если основной TableAdapter запросов больше, чем инструкции SELECT для одной таблицы, возможно, конструктор не сможет создать `InsertCommand`, `UpdateCommand`, и `DeleteCommand`. Если эти команды не создаются, может появиться ошибка при выполнении `TableAdapter.Update` метод.  
  
## <a name="tableadapter-generatedbdirectmethods"></a>GenerateDbDirectMethods адаптера таблицы  
 В дополнение к `InsertCommand`, `UpdateCommand`, и `DeleteCommand`, адаптеры таблиц создаются с помощью методов, которые могут быть выполнены непосредственно в базе данных. Эти методы (`TableAdapter.Insert`, `TableAdapter.Update`, и `TableAdapter.Delete`) можно вызывать непосредственно для управления данными в базе данных. Это означает, что эти отдельные методы можно вызывать из кода вместо вызова TableAdapter.Update для обработки операций вставки, обновления и удаления, которые ожидают для связанной таблицы данных.  
  
 Если вы не хотите создавать эти прямые методы, задайте **GenerateDbDirectMethods** свойства `false` (в **свойства** окна). Дополнительные запросы, добавляемые к TableAdapter, являются автономными, они не создают эти методы.  
  
## <a name="tableadapter-support-for-nullable-types"></a>Поддержка TableAdapter обнуляемые типы  
 Адаптеры таблиц поддерживает типы nullable `Nullable(Of T)` и `T?`. Дополнительные сведения по обнуляемые типы в Visual Basic см. в разделе [значение](http://msdn.microsoft.com/library/9ac3b602-6f96-4e6d-96f7-cd4e81c468a6). Дополнительные сведения по обнуляемые типы в C# см. в разделе [обнуляемые типы, с помощью](http://msdn.microsoft.com/library/0bacbe72-ce15-4b14-83e1-9c14e6380c28).  
  
## <a name="see-also"></a>См. также  
 [Примеры работы с данными](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)   
 [Практическое руководство. Подключение к данным в базе данных](../data-tools/how-to-connect-to-data-in-a-database.md)   
 [Пошаговое руководство: Подключение к данным в базе данных (Windows Forms)](http://msdn.microsoft.com/library/02d39aa6-8993-4602-be13-a13536af3d1c)   
 [Подготовка приложения для получения данных](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Выборка данных в приложение](../data-tools/fetching-data-into-your-application.md)   
 [Привязка элементов управления к данным в Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Редактирование данных в приложении](../data-tools/editing-data-in-your-application.md)   
 [Проверка данных](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Сохранение данных](../data-tools/saving-data.md)