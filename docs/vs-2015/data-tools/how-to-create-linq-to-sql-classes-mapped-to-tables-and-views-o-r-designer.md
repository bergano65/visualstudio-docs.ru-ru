---
title: Пошаговое руководство. Создание LINQ to SQL классов, сопоставленных с таблицами и представлениями (реляционный конструктор R) | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 0fb78bbc-7a78-4ab4-b32f-85ece912e660
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7a63e81abcae508487afa40d0778c0f9e9b9caf4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72665924"
---
# <a name="how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-or-designer"></a>Практическое руководство. Создание классов LINQ to SQL, сопоставленных с таблицами и представлениями (реляционный конструктор объектов)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
LINQ to SQL классы, сопоставленные с таблицами и представлениями базы данных, называются *классами сущностей*. Класс сущностей сопоставляется с записью, а отдельные свойства класса сущностей сопоставляются с отдельными столбцами, которые составляют запись. Создание классов сущностей, основанных на таблицах или представлениях базы данных, путем перетаскивания таблиц или представлений из **Обозреватель сервера** / **Обозреватель базы данных** на [средства LINQ to SQL в Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md). [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]Создает классы и применяет определенные [! Атрибуты LINQ to SQL для включения [! Функциональные возможности LINQ to SQL (возможности обмена данными и редактирования <xref:System.Data.Linq.DataContext> ). Подробные сведения о [! LINQ to SQL классах см. [в LINQ to SQL объектной модели](https://msdn.microsoft.com/library/81dd0c37-e2a4-4694-83b0-f2e49e693810).

> [!NOTE]
> [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]— Это простой объектно-реляционный сопоставитель, так как он поддерживает только 1:1 связей сопоставления. Другими словами, класс объекта может иметь сопоставляющее отношение только 1:1 с таблицей базы данных или представлением. Сложные сопоставления, например, сопоставление класса объекта с несколькими таблицам, не поддерживается. Однако, можно сопоставить класс объекта с представлением, которое объединяет несколько связанных таблиц.

## <a name="create-linq-to-sql-classes-that-are-mapped-to-database-tables-or-views"></a>Создание классов LINQ to SQL, которые сопоставляются с таблицами БД или представлениями
 При перетаскивании таблиц или представлений из **Обозреватель сервера** / **Обозреватель базы данных** в [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] создаются классы сущностей, а также <xref:System.Data.Linq.DataContext> методы, используемые для выполнения обновлений.

 По умолчанию [! LINQ to SQL среда выполнения создает логику для сохранения изменений из обновляемого класса сущностей обратно в базу данных. Этот логический компонент основан таблицы (определения столбцов и информация о первичных ключах). Если это поведение нежелательно, можно настроить класс сущности для использования хранимых процедур для выполнения операций вставки, обновления и удаления вместо использования по умолчанию [! LINQ to SQL поведение среды выполнения. Дополнительные сведения см. [в разделе инструкции. назначение хранимых процедур для выполнения операций обновления, вставки и удаления (реляционный конструктор R)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

#### <a name="to-create-linq-to-sql-classes-that-are-mapped-to-database-tables-or-views"></a>Для создания классов LINQ to SQL, которые сопоставляются с таблицами БД или представлениями

1. В **Server** / **Обозреватель базы данных**сервера разверните узел **таблицы** или **представления** и выберите таблицу или представление базы данных, которые нужно использовать в приложении.

2. Перетащите таблицу или представление на [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].

     Создается класс сущностей и появляется в области конструктора. Класс сущностей имеет свойства, которые сопоставляются столбцам в выбранной таблице или представлении.

## <a name="create-an-object-data-source-and-display-the-data-on-a-form"></a>Создание Object Data Source (Источника данных об объекте) и отображение данных на форме
 После создания классов сущностей с помощью [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] можно создать источник данных объекта и заполнить [окно Источники данных](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992) классами сущностей.

#### <a name="to-create-an-object-data-source-based-on-linq-to-sql-entity-classes"></a>Для создания источника данных об объекте на основе классов сущностей LINQ to SQL

1. В меню **Сборка** щелкните пункт **Собрать решение** для создания своего проекта.

2. В меню **Данные** выберите команду **Показать источники данных**.

3. В окне **Источники данных** выберите **Добавить новый источник данных**.

4. На странице **Выбор типа источника данных** выберите **Объект** и нажмите кнопку **Далее**.

5. Разверните узлы, определите местонахождение, и выберите свой класс.

    > [!NOTE]
    > Если класс **Customer** недоступен, отмените работу мастера, выполните сборку проекта и снова запустите мастер.

6. Нажмите кнопку **Готово** для создания источника данных и добавления класса сущности **Customer** в окно **Источники данных**.

7. Перетащите элементы из окна **Источники данных** на форму.

## <a name="see-also"></a>См. также раздел

- [Средства LINQ to SQL в Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Пошаговое руководство. Создание классов LINQ to SQL (реляционный конструктор R)](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)
- [Методы DataContext (реляционный конструктор R)](../data-tools/datacontext-methods-o-r-designer.md)
- [Практическое руководство. Создание методов DataContext, сопоставленных с хранимыми процедурами и функциями (реляционный конструктор объектов)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)
- [Модель объектов LINQ to SQL](https://msdn.microsoft.com/library/81dd0c37-e2a4-4694-83b0-f2e49e693810)
- [Пошаговое руководство. Настройка поведения вставки, обновления и удаления классов сущностей](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)
- [Пошаговое руководство. Добавление проверки к классам сущностей](https://msdn.microsoft.com/library/85b06a02-b2e3-4534-95b8-d077c8d4c1d7)
- [Практическое руководство. Создание связи (отношения) между классами LINQ to SQL (реляционный конструктор объектов)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)