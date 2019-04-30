---
title: Средства LINQ to SQL | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 45e477c0-5c6b-41f9-b2d0-2808fb4f6537
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 31bbc54b08fc053d10bd79d6a6b24e7605bc0351
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63384046"
---
# <a name="linq-to-sql-tools-in-visual-studio"></a>Средства LINQ to SQL в Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

LINQ to SQL была первой технологии объектно реляционного сопоставления, выпускаемых корпорацией Майкрософт. Он хорошо работает в основных сценариях и по-прежнему будет поддерживаться в Visual Studio, но больше не находится в активной разработке. Используйте LINQ to SQL, при обслуживании с устаревшим приложением, оно уже используется, или в простых приложений, использующих SQL Server и не требуют сопоставление нескольких таблиц. Как правило новые приложения должны использовать Entity Framework, когда требуется уровень объектно реляционным модулем сопоставления.

 В Visual Studio вы создание классов LINQ to SQL, которые представляют таблицы SQL с помощью [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].

 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] Имеется две области в области конструктора: область сущностей слева и область методов справа. Область сущностей является основной областью конструктора, отображающей классы сущностей, ассоциации и иерархии наследования. Область методов — это область конструктора, отображающая методы <xref:System.Data.Linq.DataContext>, которые сопоставлены хранимым процедурам и функциям.

 [!INCLUDE[vs_ordesigner_long](../includes/vs-ordesigner-long-md.md)] ([!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]) Предоставляет визуальную область конструктора для создания [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) классов сущностей и ассоциаций (связей), которые базируются на объектах в базе данных. Другими словами, [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] используется для создания модели объекта в приложении, которая сопоставляется с объектами в базе данных. Модель также генерирует <xref:System.Data.Linq.DataContext> со строгим контролем ввода, который используется для отправки и получения данных между классами сущностей и базой данных. Реляционный конструктор объектов [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] обеспечивает также функциональные возможности сопоставления сохраненных процедур и функций методам <xref:System.Data.Linq.DataContext> для возврата данных и заполнения классов сущностей. Наконец, [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] обеспечивает способность проектировать отношения наследования между классами сущностей.

## <a name="opening-the-or-designer"></a>Открытие реляционного конструктора объектов
 Чтобы добавить LINQ модель entity SQL в проект, выберите **проекта &#124; Добавление нового элемента** и нажмите кнопку **LINQ to SQL Classes** из списка элементов проекта:

 ![LINQ to SQL Classes](../data-tools/media/raddata-linq-to-sql-classes.png "raddata классы LINQ to SQL")

 Visual Studio создает DBML-файла и добавляет его в решение. Это XML-файл сопоставления и его файлы связанный код.

 ![Классы LINQ to SQL в обозревателе решений](../data-tools/media/raddata-linq-to-sql-classes-in-solution-explorer.png "классы raddata LINQ to SQL в обозревателе решений")

 При выборе DBML-файла, Visual Studio отображает область конструктора O/R, который позволяет визуально создавать модели. Ниже показан конструктор после перетащили таблицы Northwind Customers и Orders из обозревателя серверов. Обратите внимание на связь между таблицами.

 ![Конструктор LINQ to SQL](../data-tools/media/raddata-linq-to-sql-designer.png "raddata конструктор LINQ to SQL")

> [!IMPORTANT]
> [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] Представляет собой простой объект реляционный модуль сопоставления в том случае, поскольку он поддерживает только отношения сопоставления 1:1. Другими словами, класс объекта может иметь сопоставляющее отношение только 1:1 с таблицей базы данных или представлением. Сложные сопоставления, например сопоставление класса сущностей с соединяемой таблицей, не поддерживается; Используйте Entity Framework для сложные сопоставления. Кроме того, конструктор является односторонним генератором объектного кода. Это означает, что только изменения, которые вы осуществляете на области конструктора, отражаются в файле кода. Изменения, вносимые в файл кода вручную, не отражаются в [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. Любые изменения, которые вы вручную осуществляете в файле кода принимаются, когда конструктор сохраняется и генерируется код. Сведения о том, как добавить пользовательский код и распространить классы, создаваемые [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)], см. в разделе [как: Расширение кода, созданного конструктором O/R](../data-tools/how-to-extend-code-generated-by-the-o-r-designer.md).

## <a name="creating-and-configuring-the-datacontext"></a>Создание и конфигурирование DataContext
 После добавления **LINQ to SQL Classes** проект и открытия [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)], пустая область конструктора представляет пустой <xref:System.Data.Linq.DataContext> готовую к конфигурированию. <xref:System.Data.Linq.DataContext> настраивается с помощью сведений о соединении из первого объекта, который был перетащен в область конструктора... Поэтому <xref:System.Data.Linq.DataContext> конфигурируется с использованием информации о подключении из первого сброшенного в область конструктора элемента. Дополнительные сведения о <xref:System.Data.Linq.DataContext> см. класс, [методы DataContext (реляционный конструктор объектов)](../data-tools/datacontext-methods-o-r-designer.md).

## <a name="creating-entity-classes-that-map-to-database-tables-and-views"></a>Создание классов сущностей, которые сопоставляются таблицам БД или представлениям
 Можно создать классы сущностей, сопоставляемые с таблицами и представлениями, путем перетаскивания таблиц базы данных и представления из **обозревателя серверов**/**обозреватель баз данных** на [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. Как указывалось в предыдущем разделе, <xref:System.Data.Linq.DataContext> конфигурируется с информацией о подключении, предоставленной первым элементом, который перемещен в область конструктора. Если в [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] добавляется элемент, который использует другое подключение, то можно изменить подключение для <xref:System.Data.Linq.DataContext>. Дополнительные сведения см. в разделе [Как создать классы LINQ to SQL, сопоставленные с таблицами и представлениями (реляционный конструктор объектов)](../data-tools/how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md).

## <a name="creating-datacontext-methods-that-call-stored-procedures-and-functions"></a>Создание методов DataContext, которые вызывают сохраненные процедуры и функции
 Можно создать <xref:System.Data.Linq.DataContext> методы, которые вызывают (сопоставляются) сохраненные процедуры и функции путем перетаскивания их из **обозревателя серверов**/**обозреватель баз данных** на [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. Сохраненные процедуры добавляются в [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] как методы <xref:System.Data.Linq.DataContext>.

> [!NOTE]
> При перетаскивании хранимые процедуры и функции из **обозревателя серверов**/**обозреватель баз данных** на [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)], тип возвращаемого значения создаваемого <xref:System.Data.Linq.DataContext> метод отличается в зависимости от того, где вы сбросили элемент. Дополнительные сведения см. в разделе [методы DataContext (реляционный конструктор объектов)](../data-tools/datacontext-methods-o-r-designer.md).

## <a name="configuring-a-datacontext-to-use-stored-procedures-to-save-data-between-entity-classes-and-a-database"></a>Конфигурирование DataContext, чтобы использовать сохраненные процедуры для сохранения данных между классами сущностей и базой данных
 Как утверждалось ранее, можно создавать методы <xref:System.Data.Linq.DataContext>, которые вызывают сохраненные процедуры и функции. Кроме того, можно также назначать сохраненные процедуры, которые могут использоваться для поведения по умолчанию при [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] среды выполнения, которая выполняет Вставки, Обновления и удаления. Дополнительные сведения см. в разделе [Как назначить хранимые процедуры для выполнения обновлений, вставок и удалений (реляционный конструктор объектов)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

## <a name="inheritance-and-the-or-designer"></a>Наследование и реляционный конструктор объектов
 Подобно другим объектам, [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] классы могут использовать наследование и выводиться из других классов. В базе данных, отношения наследования создаются несколькими способами. [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] поддерживает концепцию наследования одиночных таблиц, так как именно она обычно осуществляется в реляционных системах. Дополнительные сведения см. в разделе [Как настроить наследование с использованием реляционного конструктора объектов](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md).

## <a name="linq-to-sql-queries"></a>Запросы LINQ to SQL
 Классы сущностей, созданных [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] предназначены для использования с [LINQ (Language-Integrated Query)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d). Дополнительные сведения см. в разделе [Как Запрос информации](http://msdn.microsoft.com/library/e538d288-2070-40ca-9da6-4fbc68cd6ad0).

## <a name="separating-the-generated-datacontext-and-entity-class-code-into-different-namespaces"></a>Отделение сгенерированного DataContext и кода класса сущностей в иные пространства имен Namespaces
 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] Предоставляет **пространство имен контекста** и **пространство имен сущностей** свойства <xref:System.Data.Linq.DataContext>. Эти свойства определяют, какое пространство имен <xref:System.Data.Linq.DataContext> и кода классов сущностей генерируется в нем. По умолчанию эти свойства пустые и <xref:System.Data.Linq.DataContext> классы сущностей генерируются в пространстве имен приложения. Чтобы сгенерировать код в пространство имен, отличное от пространства имен приложения, введите значение в свойства **Контекстное пространство имен** и (или) **Пространство имен сущностей**.

## <a name="in-this-section"></a>Содержание раздела
 [Методы DataContext (реляционный конструктор объектов)](../data-tools/datacontext-methods-o-r-designer.md) объясняет, что <xref:System.Data.Linq.DataContext> методы и как их создания.

 [Данные класса наследования (реляционный конструктор объектов)](../data-tools/data-class-inheritance-o-r-designer.md) описывает концепцию наследования одиночных таблиц и как это реализуется в [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].

 [Практическое руководство. Создание LINQ to SQL classes, сопоставленных с таблицами и представлениями (реляционный конструктор объектов)](../data-tools/how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md) описывает способы создания классов сущностей, которые сопоставляются с таблицами и представлениями в базе данных.

 [Практическое руководство. Создать ассоциацию (связь) между классами LINQ to SQL (реляционный конструктор объектов)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md) описывается, как создать связь между [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] классов сущностей.

 [Практическое руководство. Создание методов DataContext, сопоставленных с хранимыми процедурами и функциями (реляционный конструктор объектов)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md) описывается создание <xref:System.Data.Linq.DataContext> методов, выполняющих хранимые процедуры или функции, когда они вызываются.

 [Практическое руководство. Назначение хранимых процедур для выполнения обновлений, вставок и удалений (реляционный конструктор объектов)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md) описываются способы настройки <xref:System.Data.Linq.DataContext> использование хранимых процедур при сохранении данных из сущности классов обратно в базу данных.

 [Практическое руководство. Изменить тип возвращаемого значения метода DataContext (реляционный конструктор объектов)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md) описывается, как задать тип возвращаемого значения <xref:System.Data.Linq.DataContext> метод типа класса сущностей или автоматически генерируемым типом, созданные конструктором O/R.

 [Практическое руководство. Добавление проверки в классы сущностей](../data-tools/how-to-add-validation-to-entity-classes.md) описываются способы генерации частичных методов, которые позволяют добавлять код в процессе изменений свойств и обновлений классов сущностей.

 [Практическое руководство. Включение и отключение (реляционный конструктор объектов) плюрализации](../data-tools/how-to-turn-pluralization-on-and-off-o-r-designer.md) описывается включение и отключение автоматического переименования классов, которые добавляются к [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].

 [Практическое руководство. Настройка наследования с помощью реляционного конструктора](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md) описывается настройка классов сущностей, используя наследование одной таблицы с [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].

 [Практическое руководство. Расширить код, созданный конструктором O/R](../data-tools/how-to-extend-code-generated-by-the-o-r-designer.md) описывает способы и места для добавления кода, который не перезаписывается, когда изменения в объектах на реляционном конструкторе объектов регенерируют код.

 [Пошаговое руководство: Создание классов LINQ to SQL с помощью однотабличного наследования (реляционный конструктор объектов)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md) пошаговые инструкции по конфигурированию классов сущностей, используя наследование одной таблицы [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].

 [Пошаговое руководство: Настройка вставки, обновления и удаления в классах сущностей](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md) содержит пошаговые инструкции по настройке <xref:System.Data.Linq.DataContext> использование хранимых процедур при сохранении данных из сущности классов обратно в базу данных.

## <a name="reference-content"></a>Справочные материалы
 <xref:System.Linq>

 <xref:System.Data.Linq>

## <a name="see-also"></a>См. также
 [Visual Studio data tools для .NET](../data-tools/visual-studio-data-tools-for-dotnet.md) [вопросы и ответы](http://msdn.microsoft.com/library/252ed666-0679-4eea-b71b-2f14117ef443) [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) [доступ к данным в Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
