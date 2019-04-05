---
title: Практическое руководство. Создание LINQ to SQL classes, сопоставленных с таблицами и представлениями (реляционный конструктор объектов) | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 0fb78bbc-7a78-4ab4-b32f-85ece912e660
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: c2be46e61438c555fc7ee7d523b3ff9b758c0a15
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58991634"
---
# <a name="how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-or-designer"></a>Практическое руководство. создание классов LINQ to SQL, сопоставленных с таблицами и представлениями (реляционный конструктор объектов)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
Классы LINQ to SQL, которые сопоставляются таблицам БД или представлениям, называются *классы сущностей*. Класс сущностей сопоставляется с записью, тогда как отдельные свойства класса сущности сопоставляются с отдельными столбцами, образующими запись. Создайте классы сущностей, которые основаны на таблицами БД или представлениями, путем перетаскивания таблиц или представлений из **обозревателя серверов**/**обозреватель баз данных** на [средства LINQ to SQL в Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md). [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] Создает классы и применяет специфические [! LINQ к SQL атрибуты для включения [! Функции LINQ to SQL (при этом обмен данными и возможности редактирования <xref:System.Data.Linq.DataContext>). Подробные сведения о [! Классы LINQ to SQL, см. в разделе [LINQ to SQL объектной модели](http://msdn.microsoft.com/library/81dd0c37-e2a4-4694-83b0-f2e49e693810).

> [!NOTE]
> [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] Представляет собой простой объект реляционный модуль сопоставления в том случае, поскольку он поддерживает только отношения сопоставления 1:1. Другими словами, класс объекта может иметь сопоставляющее отношение только 1:1 с таблицей базы данных или представлением. Сложные сопоставления, например, сопоставление класса объекта с несколькими таблицам, не поддерживается. Однако, можно сопоставить класс объекта с представлением, которое объединяет несколько связанных таблиц.

## <a name="create-linq-to-sql-classes-that-are-mapped-to-database-tables-or-views"></a>Создание классов LINQ to SQL, которые сопоставляются с таблицами БД или представлениями
 Перетаскиванием таблиц или представлений из **обозревателя серверов**/**обозреватель баз данных** на [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] создает классы сущностей в дополнение к <xref:System.Data.Linq.DataContext> методы, которые используются для выполнение обновлений.

 По умолчанию [! Выполнения LINQ to SQL создает логику для сохранения изменений из класса обновляемых сущностей обратно к базе данных. Этот логический компонент основан таблицы (определения столбцов и информация о первичных ключах). Если такое поведение нежелательно, можно настроить класс сущностей использовать хранимые процедуры для выполнения операций вставки, обновления и Deletes вместо использования по умолчанию [! LINQ к поведению во время выполнения SQL. Дополнительные сведения см. в разделе [Как назначить хранимые процедуры для выполнения обновлений, вставок и удалений (реляционный конструктор объектов)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

#### <a name="to-create-linq-to-sql-classes-that-are-mapped-to-database-tables-or-views"></a>Для создания классов LINQ to SQL, которые сопоставляются с таблицами БД или представлениями

1.  В **Server**/**обозреватель баз данных**, разверните **таблиц** или **представления** и найдите таблицу базы данных, или просмотреть, что требуется для использования в приложении.

2.  Перетащите таблицу или представление на [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].

     Создается класс сущностей и появляется в области конструктора. Класс сущностей имеет свойства, которые сопоставляются столбцам в выбранной таблице или представлении.

## <a name="create-an-object-data-source-and-display-the-data-on-a-form"></a>Создание Object Data Source (Источника данных об объекте) и отображение данных на форме
 После создания классов сущностей с помощью [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)], можно создать источник данных объекта и заполнить [окна "Источники данных"](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992) с классами сущностей.

#### <a name="to-create-an-object-data-source-based-on-linq-to-sql-entity-classes"></a>Для создания источника данных об объекте на основе классов сущностей LINQ to SQL

1.  В меню **Сборка** щелкните пункт **Собрать решение** для создания своего проекта.

2.  В меню **Данные** выберите команду **Показать источники данных**.

3.  В окне **Источники данных** выберите **Добавить новый источник данных**.

4.  На странице **Выбор типа источника данных** выберите **Объект** и нажмите кнопку **Далее**.

5.  Разверните узлы, определите местонахождение, и выберите свой класс.

    > [!NOTE]
    > Если класс **Customer** недоступен, отмените работу мастера, выполните сборку проекта и снова запустите мастер.

6.  Нажмите кнопку **Готово** для создания источника данных и добавления класса сущности **Customer** в окно **Источники данных**.

7.  Перетащите элементы из окна **Источники данных** на форму.

## <a name="see-also"></a>См. также

- [Средства LINQ to SQL в Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Пошаговое руководство: Создание классов LINQ to SQL (реляционный конструктор объектов)](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)
- [Методы DataContext (реляционный конструктор объектов)](../data-tools/datacontext-methods-o-r-designer.md)
- [Практическое руководство. Создание методов DataContext, сопоставленных с хранимыми процедурами и функциями (реляционный конструктор объектов)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)
- [Модель объектов LINQ to SQL](http://msdn.microsoft.com/library/81dd0c37-e2a4-4694-83b0-f2e49e693810)
- [Пошаговое руководство: Настройка операций вставки, обновления и удаления в классах сущностей](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)
- [Пошаговое руководство: Добавление проверки в классы сущностей](http://msdn.microsoft.com/library/85b06a02-b2e3-4534-95b8-d077c8d4c1d7)
- [Практическое руководство. Создание связи между Классами LINQ to SQL (реляционный конструктор объектов)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)