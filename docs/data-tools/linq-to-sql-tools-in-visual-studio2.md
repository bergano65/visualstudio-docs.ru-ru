---
title: "Средства LINQ to SQL в Visual Studio2 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 45e477c0-5c6b-41f9-b2d0-2808fb4f6537
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Средства LINQ to SQL в Visual Studio
LINQ to SQL была первой технологии объектно реляционного сопоставления, выпускаемых корпорацией Майкрософт. Он хорошо работает в основных сценариях и продолжает поддерживаться в Visual Studio, но он больше не является активной разработке. Использование LINQ to SQL, при обслуживании с устаревшим приложением, оно уже используется, или в простых приложений, использующих SQL Server и не требуют сопоставления нескольких таблиц. В общем случае новые приложения должны использовать Entity Framework, когда необходим уровень объектно реляционного сопоставления.  
  
 В Visual Studio вы создания классов LINQ to SQL, представляющих таблицы SQL с помощью [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
  [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] Имеет две различные области конструктора: область сущностей слева и область методов справа. Область сущностей является основной областью конструктора, отображающей классы сущностей, ассоциации и иерархии наследования. Область методов это область конструктора, отображающая <xref:System.Data.Linq.DataContext> методов, сопоставленных с хранимыми процедурами и функциями.  
  
  [!INCLUDE[vs_ordesigner_long](../data-tools/includes/vs_ordesigner_long_md.md)] ([!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]) Предоставляет визуальную область конструктора для создания [LINQ to SQL](../Topic/LINQ%20to%20SQL.md) классов сущностей и ассоциаций (связей), основанных на объектах в базе данных. Другими словами, [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] используется для создания модели объекта в приложении, которая сопоставляется с объектами в базе данных. Он также создает строго типизированный объект <xref:System.Data.Linq.DataContext> используемый для отправки и получения данных между классами сущностей и базой данных.  [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] Также предоставляет функциональные возможности для сопоставления хранимых процедур и функций <xref:System.Data.Linq.DataContext> методов для возврата данных и заполнения классов сущностей. Наконец, [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] обеспечивает способность проектировать отношения наследования между классами сущностей.  
  
## <a name="opening-the-or-designer"></a>Открытие реляционного конструктора объектов  
 Чтобы добавить LINQ модель entity SQL в проект, выберите **& проекта #124; Добавление нового элемента** и выберите  **LINQ to SQL Classes** в списке элементов проекта:  
  
 ![Классы LINQ-SQL](../data-tools/media/raddata-linq-to-sql-classes.png "raddata LINQ to SQL Classes")  
  
 Visual Studio создает DBML-файла и добавляет его в решение. Это файл сопоставления XML и файлы связанного кода.  
  
 ![Классы LINQ to SQL в обозревателе решений](../data-tools/media/raddata-linq-to-sql-classes-in-solution-explorer.png "raddata LINQ to SQL classes in Solution Explorer")  
  
 При выборе DBML-файла, Visual Studio отображает область конструктора O/R, который позволяет визуально создавать модели. Ниже показан конструктор после перетащили таблицам Northwind Customers и Orders из обозревателя серверов. Обратите внимание, связи между таблицами.  
  
 ![Конструктор LINQ to SQL](../data-tools/media/raddata-linq-to-sql-designer.png "raddata LINQ to SQL Designer")  
  
> [!IMPORTANT]
>   [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] Представляет простой реляционный модуль сопоставления, поскольку он поддерживает только сопоставляющие отношения 1:1. Другими словами, класс объекта может иметь сопоставляющее отношение только 1:1 с таблицей базы данных или представлением. Сложные сопоставления, например, сопоставление класса сущностей нескольким таблицам, не поддерживается; Сложные сопоставления, использующих платформу Entity Framework. Кроме того, конструктор является односторонним генератором объектного кода. Это означает, что только изменения, которые вы осуществляете на области конструктора, отражаются в файле кода. Изменения, вносимые в файл кода вручную, не отражаются в [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]. Любые изменения, которые вы вручную осуществляете в файле кода принимаются, когда конструктор сохраняется и генерируется код. Сведения о том, как добавить пользовательский код и распространить классы, сгенерированные [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], в разделе [как: расширить код, созданный с помощью реляционного конструктора](../Topic/How%20to:%20Extend%20Code%20Generated%20by%20the%20O-R%20Designer.md).  
  
## <a name="creating-and-configuring-the-datacontext"></a>Создание и конфигурирование DataContext  
 После добавления **LINQ to SQL Classes** элемент в проект и откройте [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], пустая область конструктора представляет пустой <xref:System.Data.Linq.DataContext> готовая к настройке.  <xref:System.Data.Linq.DataContext> настраивается с помощью сведений о соединении из первого элемента, который был перетащен в область конструктора... Таким образом <xref:System.Data.Linq.DataContext> настраивается с помощью сведения о подключении из первого перемещенного в область конструктора элемента. Дополнительные сведения о <xref:System.Data.Linq.DataContext> см. класс, [методы DataContext (реляционный конструктор)](../data-tools/datacontext-methods-o-r-designer.md).  
  
## <a name="creating-entity-classes-that-map-to-database-tables-and-views"></a>Создание классов сущностей, которые сопоставляются таблицам БД или представлениям  
 Можно создать классы сущностей, сопоставляемые с таблицами и представлениями, путем перетаскивания таблиц и представлений из **обозревателя**/**обозревателя базы данных** на [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]. Как показано в предыдущем разделе <xref:System.Data.Linq.DataContext> настраивается с помощью сведений о соединении из первого элемента, который был перетащен в область конструктора. Если добавляется элемент, который использует другое подключение [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], можно изменить подключение для <xref:System.Data.Linq.DataContext>. Дополнительные сведения см. в разделе [Практическое руководство: создание классов LINQ to SQL сопоставляется с таблицами и представлениями (реляционный конструктор)](../Topic/How%20to:%20Create%20LINQ%20to%20SQL%20classes%20mapped%20to%20tables%20and%20views%20\(O-R%20Designer\).md).  
  
## <a name="creating-datacontext-methods-that-call-stored-procedures-and-functions"></a>Создание методов DataContext, которые вызывают сохраненные процедуры и функции  
 Можно создать <xref:System.Data.Linq.DataContext> методы, которые вызывают (сопоставляются) хранимые процедуры и функции путем перетаскивания их из **обозревателя**/**обозревателя базы данных** на [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]. Хранимые процедуры и функции добавляются [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] как методы <xref:System.Data.Linq.DataContext>.  
  
> [!NOTE]
>  При перетаскивании хранимых процедур и функций из **обозревателя серверов**/**обозревателя базы данных** на [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], тип возвращаемого значения создаваемого <xref:System.Data.Linq.DataContext> метод отличается в зависимости от того, где завершилось перетаскивание элемента. Дополнительные сведения см. в разделе [методы DataContext (реляционный конструктор)](../data-tools/datacontext-methods-o-r-designer.md).  
  
## <a name="configuring-a-datacontext-to-use-stored-procedures-to-save-data-between-entity-classes-and-a-database"></a>Конфигурирование DataContext, чтобы использовать сохраненные процедуры для сохранения данных между классами сущностей и базой данных  
 Как упоминалось ранее, можно создать <xref:System.Data.Linq.DataContext> методы, которые вызывают сохраненные процедуры и функции. Кроме того, можно также назначать сохраненные процедуры, которые могут использоваться для поведения по умолчанию при [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] среды выполнения, которая выполняет Вставки, Обновления и удаления. Дополнительные сведения см. в разделе [Практическое руководство: назначение хранимых процедур для выполнения обновлений, вставок и удалений (реляционный конструктор)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).  
  
## <a name="inheritance-and-the-or-designer"></a>Наследование и реляционный конструктор объектов  
 Подобно другим объектам, [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] классы могут использовать наследование и выводиться из других классов. В базе данных, отношения наследования создаются несколькими способами. [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] поддерживает концепцию наследования одиночных таблиц, так как именно она обычно осуществляется в реляционных системах. Дополнительные сведения см. в разделе [Практическое руководство: Настройка наследования с использованием реляционного конструктора объектов](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md).  
  
## <a name="linq-to-sql-queries"></a>Запросы LINQ to SQL  
 Классы сущностей, созданные [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] предназначены для использования с [LINQ (Language-Integrated Query)](../Topic/LINQ%20\(Language-Integrated%20Query\).md). Дополнительные сведения см. в разделе [как: запрос информации](../Topic/How%20to:%20Query%20for%20Information.md).  
  
## <a name="separating-the-generated-datacontext-and-entity-class-code-into-different-namespaces"></a>Отделение сгенерированного DataContext и кода класса сущностей в иные пространства имен Namespaces  
  [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] Предоставляет **пространство имен контекста** и **пространство имен сущности** Свойства <xref:System.Data.Linq.DataContext>. Эти свойства определяют, какое пространство имен <xref:System.Data.Linq.DataContext> и кода классов сущностей генерируется в. По умолчанию эти свойства являются пустыми и <xref:System.Data.Linq.DataContext> классы сущностей генерируются в пространстве имен приложения. Чтобы сгенерировать код в пространство имен, отличное от пространства имен приложения, введите значение в **пространство имен контекста** или **пространство имен сущности** Свойства.  
  
## <a name="in-this-section"></a>Содержание раздела  
 [Методы DataContext (реляционный конструктор)](../data-tools/datacontext-methods-o-r-designer.md)  
 Объясняет, что <xref:System.Data.Linq.DataContext> методы являются и как их создавать.  
  
 [Наследование классов данных (конструктор O/R)](../data-tools/data-class-inheritance-o-r-designer.md)  
 Описывает концепцию наследования одиночных таблиц и способы ее реализации в [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
 [Практическое руководство: Создание LINQ для классов SQL, сопоставленных с таблицами и представлениями (реляционный конструктор)](../Topic/How%20to:%20Create%20LINQ%20to%20SQL%20classes%20mapped%20to%20tables%20and%20views%20\(O-R%20Designer\).md)  
 Описывает способы создания классов сущностей, которые сопоставляются с таблицами и представлениями в базе данных.  
  
 [Практическое руководство: создание ассоциацию (связь) между классами LINQ to SQL (реляционный конструктор)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)  
 Описывает создание отношений между классами сущностей [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)].  
  
 [Практическое руководство: создание методов DataContext, сопоставленных с хранимыми процедурами и функциями (реляционный конструктор)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)  
 Описывает создание <xref:System.Data.Linq.DataContext> методов, выполняющих хранимые процедуры или функции при их вызове.  
  
 [Практическое руководство: назначение хранимых процедур для выполнения обновлений, вставок и удалений (реляционный конструктор)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)  
 Описывает, как настроить <xref:System.Data.Linq.DataContext> Использование хранимых процедур при сохранении данных из сущности классы обратно в базу данных.  
  
 [Практическое руководство: изменить тип возврата метода DataContext (реляционный конструктор)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md)  
 Описывает, как задать тип возвращаемого значения <xref:System.Data.Linq.DataContext> метод был типом класса сущностей или автоматически генерируемым типом, созданные в реляционный конструктор объектов.  
  
 [Практическое руководство: Добавление проверки к классам сущностей](../data-tools/how-to-add-validation-to-entity-classes.md)  
 Описывает способы генерации частичных методов, которые способны добавлять код в процессе изменений свойств и обновлений классов сущностей.  
  
 [Практическое руководство: Включение и выключение (конструктор O/R) плюрализации](../data-tools/how-to-turn-pluralization-on-and-off-o-r-designer.md)  
 Описывает включение и отключение автоматического переименования классов, которые добавляются в [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
 [Практическое руководство: Настройка наследования с использованием реляционного конструктора объектов](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md)  
 Описывает способы конфигурирования классов сущностей, используя наследование одиночной таблицы [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
 [Практическое руководство: расширить код, созданный с помощью конструктора O/R](../Topic/How%20to:%20Extend%20Code%20Generated%20by%20the%20O-R%20Designer.md)  
 Описывает способы и места добавления кода, который не будет переписан, когда изменения в объектах на реляционном конструкторе объектов регенерируют код.  
  
 [Пошаговое руководство: Создание классов LINQ to SQL с помощью наследование одной таблицы (конструктор O/R)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)  
 Предоставляет пошаговые инструкции по конфигурированию классов сущностей, используя наследование одиночной таблицы [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
 [Пошаговое руководство: Настройка вставки, обновления и удаления в классах сущностей](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)  
 Пошаговые инструкции по настройке <xref:System.Data.Linq.DataContext> Использование хранимых процедур при сохранении данных из сущности классы обратно в базу данных.  
  
## <a name="reference-content"></a>Справочные материалы  
 <xref:System.Linq>  
  
 <xref:System.Data.Linq>  
  
## <a name="see-also"></a>См. также раздел  
 [Данные средства Visual Studio для .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)   
 [Часто задаваемые вопросы](../Topic/Frequently%20Asked%20Questions.md)   
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)   
 [Доступ к данным в Visual Studio](../data-tools/accessing-data-in-visual-studio.md)