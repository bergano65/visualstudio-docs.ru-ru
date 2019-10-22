---
title: Средства LINQ to SQL | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 45e477c0-5c6b-41f9-b2d0-2808fb4f6537
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 470cfabd54fa5f2b92001a635477c60d45fac538
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651514"
---
# <a name="linq-to-sql-tools-in-visual-studio"></a>Инструменты LINQ to SQL в Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

LINQ to SQL была первой технологией объектно-реляционного сопоставления, выпущенной корпорацией Майкрософт. Он хорошо работает в основных сценариях и по-своему поддерживается в Visual Studio, но больше не находится в режиме активной разработки. Используйте LINQ to SQL при обслуживании уже используемого ранее приложения или в простых приложениях, использующих SQL Server и не требующих многотабличного сопоставления. Как правило, новые приложения должны использовать Entity Framework, если требуется уровень объектно-реляционного сопоставления.

 В Visual Studio вы создаете LINQ to SQL классы, представляющие таблицы SQL, с помощью [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].

 В области конструктора [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] есть две различные области: область сущности слева и панель методы справа. Область сущностей является основной областью конструктора, отображающей классы сущностей, ассоциации и иерархии наследования. Область методов — это область конструктора, отображающая методы <xref:System.Data.Linq.DataContext>, которые сопоставлены хранимым процедурам и функциям.

 @No__t_0 ([!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]) предоставляет визуальную область конструктора для создания [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) классов сущностей и ассоциаций (связей), основанных на объектах в базе данных. Другими словами, [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] используется для создания модели объекта в приложении, которая сопоставляется с объектами в базе данных. Модель также генерирует <xref:System.Data.Linq.DataContext> со строгим контролем ввода, который используется для отправки и получения данных между классами сущностей и базой данных. Реляционный конструктор объектов [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] обеспечивает также функциональные возможности сопоставления сохраненных процедур и функций методам <xref:System.Data.Linq.DataContext> для возврата данных и заполнения классов сущностей. Наконец, [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] обеспечивает способность проектировать отношения наследования между классами сущностей.

## <a name="opening-the-or-designer"></a>Открытие реляционного конструктора объектов
 Чтобы добавить LINQ to SQL сущностную модель в проект, выберите  **&#124; проект добавить новый элемент** , а затем в списке элементов проекта выберите **LINQ to SQL классы** :

 ![Классы LINQ to SQL](../data-tools/media/raddata-linq-to-sql-classes.png "раддата LINQ to SQL классы")

 Visual Studio создает DBML-файл и добавляет его в решение. Это XML-файл сопоставления и связанные с ним файлы кода.

 ![LINQ to SQL классы в обозреватель решений](../data-tools/media/raddata-linq-to-sql-classes-in-solution-explorer.png "раддата LINQ to SQL классы в обозреватель решений")

 При выборе DBML-файла Visual Studio отображает область конструктора O/R, которая позволяет визуально создавать модель. На следующем рисунке показан конструктор после перетаскивания таблиц Customers и Orders базы данных Northwind из обозреватель сервера. Обратите внимание на связь между таблицами.

 ![Конструктор LINQ to SQL](../data-tools/media/raddata-linq-to-sql-designer.png "Конструктор LINQ to SQL раддата")

> [!IMPORTANT]
> @No__t_0 представляет собой простой объектно-реляционный сопоставитель, так как он поддерживает только 1:1 связей сопоставления. Другими словами, класс объекта может иметь сопоставляющее отношение только 1:1 с таблицей базы данных или представлением. Сложное сопоставление, например сопоставление класса сущности с соединяемой таблицей, не поддерживается; Используйте Entity Framework для сложного сопоставления. Кроме того, конструктор является односторонним генератором объектного кода. Это означает, что только изменения, которые вы осуществляете на области конструктора, отражаются в файле кода. Изменения, вносимые в файл кода вручную, не отражаются в [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. Любые изменения, которые вы вручную осуществляете в файле кода принимаются, когда конструктор сохраняется и генерируется код. Сведения о том, как добавить пользовательский код и расширить классы, создаваемые [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)], см. в разделе [как расширить код, формируемый конструктором O/R](../data-tools/how-to-extend-code-generated-by-the-o-r-designer.md).

## <a name="creating-and-configuring-the-datacontext"></a>Создание и конфигурирование DataContext
 После добавления в проект элемента **LINQ to SQL Classes** и открытия [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] пустая область конструктора представляет собой пустую <xref:System.Data.Linq.DataContext>, готовую к настройке. в <xref:System.Data.Linq.DataContext> настроены сведения о соединении, предоставляемые первым элементом, который перетаскивается в область конструктора. Поэтому <xref:System.Data.Linq.DataContext> конфигурируется с использованием информации о подключении из первого сброшенного в область конструктора элемента. Дополнительные сведения о классе <xref:System.Data.Linq.DataContext> см. в разделе [методы DataContext (реляционный конструктор R)](../data-tools/datacontext-methods-o-r-designer.md).

## <a name="creating-entity-classes-that-map-to-database-tables-and-views"></a>Создание классов сущностей, которые сопоставляются таблицам БД или представлениям
 Классы сущностей, сопоставленные с таблицами и представлениями, можно создавать путем перетаскивания таблиц и представлений базы данных из **обозреватель сервера** /**Обозреватель базы данных** на [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. Как указывалось в предыдущем разделе, <xref:System.Data.Linq.DataContext> конфигурируется с информацией о подключении, предоставленной первым элементом, который перемещен в область конструктора. Если в [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] добавляется элемент, который использует другое подключение, то можно изменить подключение для <xref:System.Data.Linq.DataContext>. Дополнительные сведения см. [в разделе как создать LINQ to SQL классы, сопоставленные с таблицами и представлениями (реляционный конструктор R)](../data-tools/how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md).

## <a name="creating-datacontext-methods-that-call-stored-procedures-and-functions"></a>Создание методов DataContext, которые вызывают сохраненные процедуры и функции
 Можно создать <xref:System.Data.Linq.DataContext> методы, которые вызывают (сопоставлены с) хранимыми процедурами и функциями, перетащив их из **обозреватель сервера** /**Обозреватель базы данных** в [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. Сохраненные процедуры добавляются в [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] как методы <xref:System.Data.Linq.DataContext>.

> [!NOTE]
> При перетаскивании хранимых процедур и функций из **обозреватель сервера** /**Обозреватель базы данных** в [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] тип возвращаемого значения созданного метода <xref:System.Data.Linq.DataContext> различается в зависимости от места удаления элемента. Дополнительные сведения см. в разделе [методы DataContext (реляционный конструктор R)](../data-tools/datacontext-methods-o-r-designer.md).

## <a name="configuring-a-datacontext-to-use-stored-procedures-to-save-data-between-entity-classes-and-a-database"></a>Конфигурирование DataContext, чтобы использовать сохраненные процедуры для сохранения данных между классами сущностей и базой данных
 Как утверждалось ранее, можно создавать методы <xref:System.Data.Linq.DataContext>, которые вызывают сохраненные процедуры и функции. Кроме того, можно также назначать сохраненные процедуры, которые могут использоваться для поведения по умолчанию при [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] среды выполнения, которая выполняет Вставки, Обновления и удаления. Дополнительные сведения см. [в разделе инструкции. назначение хранимых процедур для выполнения операций обновления, вставки и удаления (реляционный конструктор R)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

## <a name="inheritance-and-the-or-designer"></a>Наследование и реляционный конструктор объектов
 Подобно другим объектам, [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] классы могут использовать наследование и выводиться из других классов. В базе данных, отношения наследования создаются несколькими способами. [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] поддерживает концепцию наследования одиночных таблиц, так как именно она обычно осуществляется в реляционных системах. Дополнительные сведения см. в разделе [инструкции. Настройка наследования с помощью реляционного конструктора O/R](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md).

## <a name="linq-to-sql-queries"></a>Запросы LINQ to SQL
 Классы сущностей, созданные [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)], предназначены для использования с [LINQ (интегрированный в язык запрос)](https://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d). Дополнительные сведения см. [в разделе инструкции. запрос сведений](https://msdn.microsoft.com/library/e538d288-2070-40ca-9da6-4fbc68cd6ad0).

## <a name="separating-the-generated-datacontext-and-entity-class-code-into-different-namespaces"></a>Отделение сгенерированного DataContext и кода класса сущностей в иные пространства имен Namespaces
 @No__t_0 предоставляет свойства **пространства имен контекста** и **пространства имен сущности** в <xref:System.Data.Linq.DataContext>. Эти свойства определяют, какое пространство имен <xref:System.Data.Linq.DataContext> и кода классов сущностей генерируется в нем. По умолчанию эти свойства пустые и <xref:System.Data.Linq.DataContext> классы сущностей генерируются в пространстве имен приложения. Чтобы сгенерировать код в пространство имен, отличное от пространства имен приложения, введите значение в свойства **Контекстное пространство имен** и (или) **Пространство имен сущностей**.

## <a name="in-this-section"></a>В данном разделе
 [Методы DataContext (реляционный конструктор R)](../data-tools/datacontext-methods-o-r-designer.md) Объясняет, что такое <xref:System.Data.Linq.DataContext> методы и как их создавать.

 [Наследование классов данных (реляционный конструктор R)](../data-tools/data-class-inheritance-o-r-designer.md) Описывает понятие наследования одной таблицы и его реализацию в [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].

 [Как создать LINQ to SQL классы, сопоставленные с таблицами и представлениями (реляционный конструктор R)](../data-tools/how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md) Описывает создание классов сущностей, сопоставленных с таблицами и представлениями в базе данных.

 [Как создать ассоциацию (связь) между LINQ to SQL классами (реляционный конструктор R)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md) Описывает, как создать связь между [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] классами сущностей.

 [Инструкции. Создание методов DataContext, сопоставленных с хранимыми процедурами и функциями (реляционный конструктор R)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md) Описывает создание <xref:System.Data.Linq.DataContext> методов, которые запускают хранимые процедуры или функции при их вызове.

 [Инструкции. назначение хранимых процедур для выполнения операций обновления, вставки и удаления (реляционный конструктор R)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md) Описывает, как настроить <xref:System.Data.Linq.DataContext> для использования хранимых процедур при сохранении данных из классов сущностей обратно в базу данных.

 [Как изменить тип возвращаемого значения метода DataContext (реляционный конструктор R)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md) Описывает, как задать тип возвращаемого значения метода <xref:System.Data.Linq.DataContext> в качестве типа класса сущности или автоматически созданного типа, созданного конструктором O/R.

 [Как добавить проверку в классы сущностей](../data-tools/how-to-add-validation-to-entity-classes.md) Описывает создание разделяемых методов, позволяющих добавлять код во время изменения свойств и обновления класса сущностей.

 [Включение и отключение во множественном числе (реляционный конструктор R)](../data-tools/how-to-turn-pluralization-on-and-off-o-r-designer.md) Описывает включение и отключение автоматического переименования классов, добавляемых в [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].

 [Как настроить наследование с помощью реляционного конструктора O/R](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md) Описывает настройку классов сущностей с помощью наследования одной таблицы с [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].

 [Пошаговое руководство. расширение кода, созданного с помощью конструктора O/R](../data-tools/how-to-extend-code-generated-by-the-o-r-designer.md) Описывает, как и где следует добавлять код, который не будет перезаписываться при изменении объектов в конструкторе O/R.

 [Пошаговое руководство. создание LINQ to SQL классов с помощью наследования одной таблицы (реляционный конструктор R)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md) Содержит пошаговые инструкции по настройке классов сущностей с помощью наследования одной таблицы с [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].

 [Пошаговое руководство. Настройка поведения вставки, обновления и удаления классов сущностей](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md) Содержит пошаговые инструкции по настройке <xref:System.Data.Linq.DataContext> для использования хранимых процедур при сохранении данных из классов сущностей обратно в базу данных.

## <a name="reference-content"></a>Справочные материалы
 <xref:System.Linq>

 <xref:System.Data.Linq>

## <a name="see-also"></a>См. также раздел
 [Часто задаваемые вопросы](https://msdn.microsoft.com/library/252ed666-0679-4eea-b71b-2f14117ef443) [о средствах Visual Studio Data Tools для .NET](../data-tools/visual-studio-data-tools-for-dotnet.md) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) [доступе к данным в Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
