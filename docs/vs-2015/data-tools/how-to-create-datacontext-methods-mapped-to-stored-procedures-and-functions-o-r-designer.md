---
title: Пошаговое руководство. Создание методов DataContext, сопоставленных с хранимыми процедурами и функциями (реляционный конструктор R) | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: e7ca32f1-50b3-48af-ad92-ceafd749296a
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 70053b74a4dd2ad569e1e8195f4c9b2e7b214440
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72665980"
---
# <a name="how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-or-designer"></a>Практическое руководство. Создание методов DataContext, сопоставленных с хранимыми процедурами и функциями (реляционный конструктор объектов)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Хранимые процедуры и функции можно добавлять в [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] методы AS <xref:System.Data.Linq.DataContext> . Вызов метода и передача в обязательные параметры запускает сохраненную процедуру или функцию на базе данных и возвращает данные в тип возвращаемого значения метода <xref:System.Data.Linq.DataContext>. Подробные сведения о <xref:System.Data.Linq.DataContext> методах см. в разделе [методы DataContext (реляционный конструктор R)](../data-tools/datacontext-methods-o-r-designer.md).

> [!NOTE]
> Хранимые процедуры также используются для переопределения действий, которые [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] выполняет для операций вставки, обновления и удаления при сохранении изменений из классов сущностей в базе данных. Дополнительные сведения см. [в разделе инструкции. назначение хранимых процедур для выполнения операций обновления, вставки и удаления (реляционный конструктор R)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

## <a name="creating-datacontext-methods"></a>Создание методов DataContext
 Методы можно создавать <xref:System.Data.Linq.DataContext> путем перетаскивания хранимых процедур или функций из **обозреватель сервера или Обозреватель базы данных** в [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] .

> [!NOTE]
> Тип возвращаемого значения сформированного метода <xref:System.Data.Linq.DataContext> будет зависеть от места, в котором завершается перетаскивание хранимой процедуры или функции в [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. Если сбрасываете элемент прямо на существующий класс сущностей, то создается метод <xref:System.Data.Linq.DataContext>, который имеет тип возвращаемого значения класса сущностей. Если вы сбрасываете элементы в пустой области конструктора [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)], то создается метод <xref:System.Data.Linq.DataContext>, который возвращает автоматически сгенерированный тип. Тип возвращаемого значения метода можно изменить <xref:System.Data.Linq.DataContext> после его добавления на панель методы. Чтобы просмотреть или изменить тип возвращаемого значения метода <xref:System.Data.Linq.DataContext>, выберите его и проверьте свойство **тип возвращаемого значения** в окне **Свойства**. Дополнительные сведения см. в разделе [инструкции. изменение типа возвращаемого значения метода DataContext (реляционный конструктор данных)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

#### <a name="to-create-datacontext-methods-that-return-automatically-generated-types"></a>Для создания методов DataContext, которые возвращают автоматически сгенерированные типы

1. В **Обозреватель сервера** / **Обозреватель базы данных**разверните узел **хранимые процедуры** базы данных, с которой вы работаете.

2. Найдите нужную сохраненную процедуру и перетащите ее на пустую область конструктора [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].

     Метод <xref:System.Data.Linq.DataContext> создается с автоматически сгенерированным типом возвращаемого значения и появляется в области **Методы**.

#### <a name="to-create-datacontext-methods-that-have-the-return-type-of-an-entity-class"></a>Чтобы создать методы DataContext, которые имеют тип возврата класса сущностей

1. В **Обозреватель сервера** / **Обозреватель базы данных**разверните узел **хранимые процедуры** базы данных, с которой вы работаете.

2. Найдите нужную сохраненную процедуру и перетащите ее на существующий класс сущностей в конструкторе [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].

     Метод <xref:System.Data.Linq.DataContext> создается с типом возвращаемого значения выбранного класса сущностей и появляется в области **Методы**.

> [!NOTE]
> Дополнительные сведения об изменении типа возвращаемого значения существующих <xref:System.Data.Linq.DataContext> методы, см. в разделе [как: Изменение типа возвращаемого значения метода DataContext (реляционный конструктор объектов)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).

## <a name="see-also"></a>См. также:
 [LINQ to SQL средства в](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [методах DataContext](../data-tools/datacontext-methods-o-r-designer.md) Visual Studio [. Пошаговое руководство. Создание классов LINQ to SQL (реляционный конструктор r)](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) [Знакомство с LINQ в Visual Basic](https://msdn.microsoft.com/library/3047d86e-0d49-40e2-928b-dc02e46c7984) [Практическое руководство. Написание запросов LINQ на C#](https://msdn.microsoft.com/library/45e47fcc-cfa1-4b72-b161-d038ae87bd23)
