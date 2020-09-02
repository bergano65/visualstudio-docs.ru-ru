---
title: Методы DataContext (реляционный конструктор R) | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: c149f4e5-3b61-4c33-892e-3e26d47f3eeb
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e9d7e0eee35e0f1e62247865bd539aab8d21349d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657395"
---
# <a name="datacontext-methods-or-designer"></a>Методы DataContext (реляционный конструктор объектов)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

DataContext] (assetId:///Т: System. Data. LINQ. DataContext? qualifyHint = false&автообновление = true) [LINQ to SQL](../data-tools/linq-to-sql-tools-in-visual-studio2.md)методы <xref:System.Data.Linq.DataContext> класса, которые выполняют хранимые процедуры и функции в базе данных.

 Класс <xref:System.Data.Linq.DataContext> представляет собой класс [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)], который действует как канал между базой данных SQL Server и классами сущностей [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)], сопоставленных этой базе данных. <xref:System.Data.Linq.DataContext>Класс содержит сведения строки подключения и методы для подключения к базе данных и управления данными в базе данных. По умолчанию <xref:System.Data.Linq.DataContext> класс содержит несколько методов, которые можно вызывать, например <xref:System.Data.Linq.DataContext.SubmitChanges%2A> метод, отправляющий обновленные данные из [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] классов в базу данных. Можно также создать дополнительные методы <xref:System.Data.Linq.DataContext>, которые сопоставляются сохраненным процедурам и функциям. Другими словами, вызов этих пользовательских методов запустит сохраненную процедуру или функцию в базе данных, которой метод <xref:System.Data.Linq.DataContext> сопоставлен. Можно добавить новые методы в класс <xref:System.Data.Linq.DataContext> точно так, как добавлялись бы методы, чтобы расширить любой класс. Однако, в обсуждении <xref:System.Data.Linq.DataContext> методов в контексте [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] , это <xref:System.Data.Linq.DataContext> методы, которые сопоставляются с хранимыми процедурами и функциями, которые обсуждаются.

## <a name="methods-pane"></a>Область методов
 <xref:System.Data.Linq.DataContext> методы, которые сопоставляются с хранимыми процедурами и функциями, отображаются на панели методы [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] . Панель методы — это панель, расположенная вдоль стороны области **сущности** (Главная область конструктора). На панели методы перечислены все <xref:System.Data.Linq.DataContext> методы, которые были созданы с помощью [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] . По умолчанию панель методы пуста; Перетащите хранимые процедуры или функции из **Обозреватель сервера** / **Обозреватель базы данных** на [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] методы для создания <xref:System.Data.Linq.DataContext> и заполнения области методов. Дополнительные сведения см. [в разделе инструкции. Создание методов DataContext, сопоставленных с хранимыми процедурами и функциями (реляционный конструктор операций и т. д.)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md).

> [!NOTE]
> Откройте и закройте панель методы, щелкнув правой кнопкой мыши, [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] а затем выбрав **Скрыть панель методов** или **Показать панель методов**, или воспользоваться сочетанием клавиш CTRL + 1.

## <a name="two-types-of-datacontext-methods"></a>Два типа возврата методов DataContext
 Методы DataContext сопоставляются хранимым процедурам и функциям в базе данных. Методы DataContext создаются и добавляются в области методов в [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. Существует два различных типа методов <xref:System.Data.Linq.DataContext> — возвращающие один или несколько результирующих наборов и не возвращающие результирующие наборы:

- Методы <xref:System.Data.Linq.DataContext>, которые возвращают один или несколько результирующих наборов.

     Этот вид метода <xref:System.Data.Linq.DataContext> создается, если приложение должно только запускать хранимые процедуры и функции в базе данных и возвращать результаты. Дополнительные сведения см. [в разделе инструкции. Создание методов DataContext, сопоставленных с хранимыми процедурами и функциями (реляционный конструктор O/R)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md), System. Data. LINQ. исинглересулт \<T> и <xref:System.Data.Linq.IMultipleResults> .

- Методы <xref:System.Data.Linq.DataContext>, которые не возвращают результирующих наборов, например операции вставки, обновления и удаления для некоторого класса сущности.

     Этот вид метода <xref:System.Data.Linq.DataContext> создается, если приложение должно запускать хранимые процедуры вместо выполнения определенных по умолчанию действий [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] для сохранения измененных данных между классом сущности и базой данных. Дополнительные сведения см. [в разделе инструкции. назначение хранимых процедур для выполнения операций обновления, вставки и удаления (реляционный конструктор R)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

## <a name="return-types-of-datacontext-methods"></a>Типы возвращаемого значения методов DataContext
 При перетаскивании хранимых процедур и функций из **Обозреватель сервера** / **Обозреватель базы данных** в [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] , тип возвращаемого значения созданного <xref:System.Data.Linq.DataContext> метода отличается в зависимости от места удаления элемента. При перетаскивании элементов непосредственно в существующий класс сущностей создается <xref:System.Data.Linq.DataContext> метод с типом возвращаемого значения класса сущностей; удаление элементов в пустую область [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] (на любой панели) создает <xref:System.Data.Linq.DataContext> метод, возвращающий автоматически созданный тип. Автоматически сгенерированный тип, который создается, имеет имя, которое соответствует имени сохраненной процедуры или имени функции и свойствам, которые сопоставляют полям, возвращенным сохраненной процедурой или функцией.

> [!NOTE]
> Можно изменить тип возвращаемого значения метода <xref:System.Data.Linq.DataContext> после его добавления в область методов. Чтобы просмотреть или изменить тип возвращаемого значения метода <xref:System.Data.Linq.DataContext>, выберите его и проверьте свойство **тип возвращаемого значения** в окне **Свойства**. Дополнительные сведения см. в разделе [инструкции. изменение типа возвращаемого значения метода DataContext (реляционный конструктор данных)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).

 Объекты, перетаскиваемые из базы данных в область реляционного конструктора объектов, автоматически получают имена, основанные на имени объектов в базе данных. Если несколько раз перетащить один объект, к концу имени будет добавлен номер, чтобы различить имена экземпляров. Если имена объектов базы данных содержат пробелы или символы, которые не поддерживаются в Visual Basic или в C#, то пробел или недопустимый символ будет заменен символом подчеркивания.

## <a name="see-also"></a>См. также:
 [Средства LINQ to SQL в Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) [хранимые процедуры](https://msdn.microsoft.com/library/4d23dd7a-a85f-44ff-a717-af7d0950c0fc) [Практическое руководство. Создание методов DataContext, сопоставленных с хранимыми процедурами и функциями (реляционный конструктор объектов)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md) [Практическое руководство. назначение хранимых процедур для выполнения операций обновления, вставки и удаления (o/r Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md) [Пошаговое руководство. Настройка классов сущностей в](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md) [пошаговом руководстве по созданию класса LINQ to SQL (o-R Designer)](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)
