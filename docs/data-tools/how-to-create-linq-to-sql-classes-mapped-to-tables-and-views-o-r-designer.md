---
title: 'Как: создать LINQ to SQL classes, сопоставленных с таблицами и представлениями (конструктор O-R) | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0fb78bbc-7a78-4ab4-b32f-85ece912e660
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: cc3c70ca70170de630dc28a10ff5d1352a610bfb
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-or-designer"></a>Как: создать LINQ to SQL classes сопоставлены с таблицами и представлениями (O/R-конструктор)
[!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] классы, которые сопоставляются таблицам БД или представлениям, называются *классы сущностей*. Класс сущностей сопоставляется с записью, тогда как отдельные свойства класса сущности сопоставляются отдельные столбцы, составляющие запись. Создание классов сущностей, основанных на таблицах базы данных или представления путем перетаскивания таблиц или представлений из **обозревателя серверов**/**обозреватель баз данных** на [средства LINQ to SQL в Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md). [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] Создает классы и применяет специфические [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] атрибуты для их [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] функциональные возможности (передачи данных и редактирования возможности <xref:System.Data.Linq.DataContext>). Дополнительные сведения о [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] классы, в разделе [LINQ to SQL модель объектов](/dotnet/framework/data/adonet/sql/linq/the-linq-to-sql-object-model).  
  
> [!NOTE]
>  [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] Представляет простой объект реляционный модуль сопоставления, поскольку он поддерживает только сопоставляющие отношения 1:1. Другими словами, класс объекта может иметь сопоставляющее отношение только 1:1 с таблицей базы данных или представлением. Сложные сопоставления, например, сопоставление класса объекта с несколькими таблицам, не поддерживается. Однако, можно сопоставить класс объекта с представлением, которое объединяет несколько связанных таблиц.  
  
## <a name="create-linq-to-sql-classes-that-are-mapped-to-database-tables-or-views"></a>Создание классов LINQ to SQL, которые сопоставляются с таблицами БД или представлениями  
 Перетаскиванием таблиц или представлений из **обозревателя серверов**/**обозреватель баз данных** на [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] будут созданы классы сущностей в дополнение к <xref:System.Data.Linq.DataContext> методы, используемые для выполнение обновлений.  
  
 По умолчанию среда выполнения [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] создает логический компонент для сохранения изменений из класса обновляемых сущностей обратно в базу данных. Этот логический компонент основан таблицы (определения столбцов и информация о первичных ключах). Если вы не хотите такого поведения, то можно конфигурировать класс сущностей, чтобы использовать сохраненные процедуры для выполнения Inserts, Updates и Deletes вместо использования поведения по умолчанию [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)]. Дополнительные сведения см. в разделе [как: назначение хранимых процедур для выполнения обновления, вставки и удаления (конструктор O/R)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).  
  
[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### <a name="to-create-linq-to-sql-classes-that-are-mapped-to-database-tables-or-views"></a>Для создания классов LINQ to SQL, которые сопоставляются с таблицами БД или представлениями  
  
1.  В **сервера**/**обозреватель баз данных**, разверните **таблиц** или **представления** и найдите таблицу базы данных или представление, должны для использования в приложении.  
  
2.  Перетащите таблицу или представление на [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
     Создается класс сущностей и появляется в области конструктора. Класс сущностей имеет свойства, которые сопоставляются столбцам в выбранной таблице или представлении.  
  
## <a name="create-an-object-data-source-and-display-the-data-on-a-form"></a>Создание Object Data Source (Источника данных об объекте) и отображение данных на форме  
 После создания классов сущностей с помощью [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], можно создать источник данных и заполнения [окно "Источники данных"](add-new-data-sources.md) с классами сущностей.  
  
#### <a name="to-create-an-object-data-source-based-on-linq-to-sql-entity-classes"></a>Для создания источника данных об объекте на основе классов сущностей LINQ to SQL  
  
1.  На **построения** меню, нажмите кнопку **построить решение** для построения проекта.  
  
2.  В меню **Данные** выберите команду **Показать источники данных**.  
  
3.  В окне **Источники данных** выберите **Добавить новый источник данных**.  
  
4.  Нажмите кнопку **объекта** на **Выбор типа источника данных** и нажмите кнопку **Далее**.  
  
5.  Разверните узлы, определите местонахождение, и выберите свой класс.  
  
    > [!NOTE]
    >  Если **клиента** класс недоступен, отмените работу мастера, постройте проект и снова запустите мастер.  
  
6.  Нажмите кнопку **Готово** для создания источника данных и добавления **клиента** класса сущности, который **источники данных** окна.  
  
7.  Перетащите элементы из **источники данных** окна в форму.  
  
## <a name="see-also"></a>См. также  
 [Средства LINQ to SQL в Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [Пошаговое руководство: Создание классов LINQ to SQL (конструктор O-R)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)   
 [Методы DataContext (O/R-конструктор)](../data-tools/datacontext-methods-o-r-designer.md)   
 [Как: создание методов DataContext, сопоставленных с хранимыми процедурами и функциями (O/R-конструктор)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)   
 [LINQ to SQL модель объектов](/dotnet/framework/data/adonet/sql/linq/the-linq-to-sql-object-model)   
 [Пошаговое руководство: Настройка инструкции insert, update и delete поведение классов сущностей](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)   
  [Как: создать ассоциацию (связь) между LINQ to SQL classes (O/R-конструктор)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)