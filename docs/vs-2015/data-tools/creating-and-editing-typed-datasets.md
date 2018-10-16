---
title: Создание и изменение типизированных наборов данных | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- Designer_Microsoft.VSDesigner.DataSource.Designer.DataSourceRootDesigner
- vs.data.adddataset
dev_langs:
- VB
- CSharp
- C++
- aspx
- aspx
helpviewer_keywords:
- datasets [Visual Basic], visual designer
- data [Visual Studio], Dataset Designer
- Dataset Designer
ms.assetid: cd0dbe93-be9b-41e4-bc39-e9300678c1f2
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 8c18717cd2a5c7e05b79dbe575d919ef0c8670dd
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49225847"
---
# <a name="creating-and-editing-typed-datasets"></a>Создание и изменение типизированных наборов данных
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Конструктор наборов данных** представляет собой набор визуальных инструментов, которые можно использовать для создания и редактирования типизированных наборов данных и отдельных элементов, которые они содержат.  
  
 **Конструктор наборов данных** обеспечивает визуальное представление объектов, содержащихся в типизированных наборах данных. Создание и изменение [TableAdapters](../data-tools/tableadapter-overview.md), [запросов TableAdapter](../data-tools/how-to-create-tableadapter-queries.md), <xref:System.Data.DataTable>s, <xref:System.Data.DataColumn>s, и <xref:System.Data.DataRelation>s с **конструктор наборов данных**.  
  
 Чтобы открыть **конструктор наборов данных**, дважды щелкните набор данных в **обозревателе решений**, или щелкните правой кнопкой мыши набор данных в **источников данных** и щелкните **изменение Набор данных в конструкторе**. Дополнительные сведения см. в разделе [как: Открытие набора данных в конструкторе наборов данных](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3). Добавить новую <xref:System.Data.DataSet> элемент с **Добавление нового элемента** появится диалоговое окно **конструктор наборов данных** с пустой набор данных готов для редактирования.  
  
> [!NOTE]
>  **Конструктор наборов данных** может использоваться для расширения функциональности набора данных. Дважды щелкните область конструктора или щелкните правой кнопкой мыши и выберите **Просмотр кода** создать файл разделяемого класса, где можно добавить код для набора данных, не будут изменены или удалены с помощью конструктора. Сведения о расширении функциональных возможностей адаптера таблицы, см. в разделе [расширения функциональных возможностей адаптера таблицы](../data-tools/extend-the-functionality-of-a-tableadapter.md).  
  
 В следующей таблице перечислены общие задачи, можно выполнить с **конструктор наборов данных**.  
  
|Кому|См.|  
|--------|---------|  
|Создание адаптера таблицы|[Создание и настройка адаптеров таблиц](../data-tools/create-and-configure-tableadapters.md)|  
|Изменить адаптера таблицы|[Практическое: изменение объектов TableAdapter](http://msdn.microsoft.com/library/ca178745-e35a-45f1-a395-23cddfd8f855)|  
|Создание запроса адаптера таблицы|[Практическое руководство. Создание запросов TableAdapter](../data-tools/how-to-create-tableadapter-queries.md)|  
|Изменение запроса адаптера таблицы|[Практическое руководство. Изменение запросов TableAdapter](../data-tools/how-to-edit-tableadapter-queries.md)|  
|Создание <xref:System.Data.DataTable>|[Практическое руководство. Создание таблиц данных](../data-tools/how-to-create-data-tables.md)|  
|Изменить <xref:System.Data.DataTable>|[Разработка объектов DataTable](../data-tools/designing-datatables.md)|  
|Создание <xref:System.Data.DataColumn>|[Практическое: Добавление столбцов в объект DataTable](http://msdn.microsoft.com/library/8ca21f77-b99a-47a7-a656-7cfd7a1bd9df)|  
|Создание связи между двумя <xref:System.Data.DataTable>s|[Практическое: создание объектов DataRelation с помощью конструктора наборов данных](http://msdn.microsoft.com/library/a3ab4803-0b50-4b74-9920-ab20bfbf1aa2)|  
|Расширения функциональности набора данных|[Практическое: расширения функциональности набора данных](http://msdn.microsoft.com/library/dfbc21eb-7ea2-4942-addd-49677f5493be)|  
|Добавление проверки в таблицу данных <xref:System.Data.DataTable.ColumnChanging> событий|[Практическое: проверка данных в ходе изменения столбцов](http://msdn.microsoft.com/library/a2680600-67b6-4a40-a77e-b5bc638281c5)|  
|Добавление проверки в таблицу данных <xref:System.Data.DataTable.RowChanging> событий|[Практическое: проверка данных в ходе изменения строк](http://msdn.microsoft.com/library/afc03c77-dfed-4302-9376-929400468ecc)|  
  
## <a name="creating-objects-on-the-design-surface"></a>Создание объектов в области конструктора  
 Можно создать наборы данных путем добавления и редактирования отдельных объектов, составляющих набор данных. В следующей таблице приведены объяснения различных объектов в **набора данных** вкладке **элементов** , можно перетащить в область конструктора:  
  
|Object|Описание|  
|------------|-----------------|  
|адаптер таблиц|Содержит коллекцию команд данных и подключение к данным, которые используются для связи с основной базы данных и заполнить таблицу данных. Дополнительные сведения см. в разделе [TableAdapter Overview](../data-tools/tableadapter-overview.md) и [Создание и настройка адаптеров таблиц](../data-tools/create-and-configure-tableadapters.md).|  
|Запрос|Запросы TableAdapter являются строго типизированных методов, выполнение инструкций SQL и хранимых процедур. Выполнение запроса адаптера таблицы заполняет таблицу данных или выполняет другие задачи базы данных. Дополнительные сведения см. в разделе [как: создание запросов TableAdapter](../data-tools/how-to-create-tableadapter-queries.md). Перетаскивание запроса в таблицу добавляет запрос к этой таблице, тогда как перетаскивание запроса в пустую область **конструктор наборов данных** создает глобальный запрос. Дополнительные сведения см. в разделе [как: Добавление глобальных запросов в адаптер таблицы](../data-tools/how-to-add-global-queries-to-a-tableadapter.md).|  
|<xref:System.Data.DataTable>|Представляет коллекцию строк, возвращаемых из базы данных в памяти.|  
|Связи (<xref:System.Data.DataRelation>)|Представляет связь «родители потомки» между двумя <xref:System.Data.DataTable>s. Дополнительные сведения см. в разделе [Знакомство с объектами DataRelation](http://msdn.microsoft.com/library/89d8a881-8265-41f2-a88b-61311ab06192) и [Пошаговое руководство: Создание связи между таблицами данных](http://msdn.microsoft.com/library/9b3f1c87-7098-4ed4-a710-cde8f8059f82).|  
  
> [!NOTE]
>  **Конструктор наборов данных** подключается к основной базе данных создается только в том случае, если набор данных; в конструкторе не автоматически обнаруживает последующие изменения в базе данных. Чтобы обновить существующий XSD-файл, повторно запустите **мастер настройки**. Если были изменены связи таблиц, удалите и снова добавить соответствующие таблицы в XSD-файл.  
  
## <a name="linq-to-dataset"></a>LINQ to Dataset  
 [!INCLUDE[linq_dataset](../includes/linq-dataset-md.md)] позволяет [LINQ (Language-Integrated Query)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d) над данными в <xref:System.Data.DataSet> объекта. Дополнительные сведения см. в разделе [LINQ to DataSet](http://msdn.microsoft.com/library/743e3755-3ecb-45a2-8d9b-9ed41f0dcf17).  
  
## <a name="see-also"></a>См. также  
 [Пошаговое руководство: Создание набора данных с помощью конструктора наборов данных](../data-tools/walkthrough-creating-a-dataset-with-the-dataset-designer.md)   
 [Пошаговое руководство: Создание адаптера таблицы с несколькими запросами](../data-tools/walkthrough-creating-a-tableadapter-with-multiple-queries.md)   
 [Пошаговое руководство: Создание таблицы данных в конструкторе наборов данных](../data-tools/walkthrough-creating-a-datatable-in-the-dataset-designer.md)   
 [Пошаговое руководство: Создание связи между таблицами данных](http://msdn.microsoft.com/library/9b3f1c87-7098-4ed4-a710-cde8f8059f82)   
 [Пошаговое руководство: Отображение данных в форме Windows](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)   
 [Окно источников данных](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992)   
 [Инструменты для работы с наборами данных в Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)   
 [Подготовка приложения для получения данных](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Выборка данных в приложение](../data-tools/fetching-data-into-your-application.md)   
 [Редактирование данных в приложении](../data-tools/editing-data-in-your-application.md)   
 [Проверка данных](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Сохранение данных](../data-tools/saving-data.md)