---
title: 'Практическое: создание методов DataContext, сопоставленных с хранимыми процедурами и функциями (реляционный конструктор объектов) | Документация Майкрософт'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e7ca32f1-50b3-48af-ad92-ceafd749296a
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 8b1864fa87867d2f48179c5215a18f2897d9883c
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49196200"
---
# <a name="how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-or-designer"></a>Практическое: создание методов DataContext, сопоставленных с хранимыми процедурами и функциями (реляционный конструктор объектов)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Хранимые процедуры и функции могут добавляться к [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] как <xref:System.Data.Linq.DataContext> методы. Вызов метода и передача в обязательные параметры запускает хранимую процедуру или функцию в базе данных и возвращает данные в тип возвращаемого значения <xref:System.Data.Linq.DataContext> метод. Подробные сведения о <xref:System.Data.Linq.DataContext> методы, см. в разделе [методы DataContext (реляционный конструктор объектов)](../data-tools/datacontext-methods-o-r-designer.md).  
  
> [!NOTE]
>  Хранимые процедуры также используются для переопределения действий, которые [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] выполняет для операций вставки, обновления и удаления при сохранении изменений из классов сущностей в базе данных. Дополнительные сведения см. в разделе [как: назначение хранимых процедур для выполнения обновлений, вставок и удалений (реляционный конструктор объектов)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).  
  
## <a name="creating-datacontext-methods"></a>Создание методов DataContext  
 Можно создать <xref:System.Data.Linq.DataContext> методов путем перетаскивания сохраненных процедур или функций из **Server Explorer/Database Explorer** на [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].  
  
> [!NOTE]
>  Тип возвращаемого значения сформированного метода <xref:System.Data.Linq.DataContext> будет зависеть от места, в котором завершается перетаскивание хранимой процедуры или функции в [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. Если сбрасываете элемент прямо на существующий класс сущностей, то создается метод <xref:System.Data.Linq.DataContext>, который имеет тип возврата класса сущностей. Если вы сбрасываете элементы в пустой области конструктора [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)], то создается метод <xref:System.Data.Linq.DataContext>, который возвращает автоматически сгенерированный тип. Можно изменить тип возвращаемого значения <xref:System.Data.Linq.DataContext> метод после его добавления в область методов. Чтобы проверить или изменить тип возвращаемого значения <xref:System.Data.Linq.DataContext> метод, выберите его и проверьте **тип возвращаемого значения** свойство в **свойства** окна. Дополнительные сведения см. в разделе [способы: измените тип возвращаемого значения метода DataContext (реляционный конструктор объектов)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
#### <a name="to-create-datacontext-methods-that-return-automatically-generated-types"></a>Для создания методов DataContext, которые возвращают автоматически сгенерированные типы  
  
1.  В **обозревателя серверов**/**обозреватель баз данных**, разверните **хранимые процедуры** узел базы данных, вы работаете.  
  
2.  Найдите нужную сохраненную процедуру и перетащите ее на пустую область конструктора [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].  
  
     <xref:System.Data.Linq.DataContext> Метод создается с автоматически сгенерированным типом возвращаемого значения и появляется в **методы** области.  
  
#### <a name="to-create-datacontext-methods-that-have-the-return-type-of-an-entity-class"></a>Чтобы создать методы DataContext, которые имеют тип возвращаемого значения класса сущностей  
  
1.  В **обозревателя серверов**/**обозреватель баз данных**, разверните **хранимые процедуры** узел базы данных, вы работаете.  
  
2.  Найдите нужную сохраненную процедуру и перетащите ее на существующий класс сущностей в конструкторе [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].  
  
     <xref:System.Data.Linq.DataContext> Метод создается с типом возвращаемого значения выбранного класса сущностей и появляется в **методы** области.  
  
> [!NOTE]
>  Сведения об изменении типа возвращаемого значения существующих <xref:System.Data.Linq.DataContext> методы, см. в разделе [способы: измените тип возвращаемого значения метода DataContext (реляционный конструктор объектов)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).  
  
## <a name="see-also"></a>См. также  
 [Средства LINQ to SQL в Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [Методы DataContext (реляционный конструктор объектов)](../data-tools/datacontext-methods-o-r-designer.md)   
 [Пошаговое руководство: Создание классов LINQ to SQL (реляционный конструктор объектов)](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)   
 [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)   
 [Знакомство с LINQ в Visual Basic](http://msdn.microsoft.com/library/3047d86e-0d49-40e2-928b-dc02e46c7984)   
 [Практическое руководство. Создание запросов LINQ на языке C#](http://msdn.microsoft.com/library/45e47fcc-cfa1-4b72-b161-d038ae87bd23)

