---
title: "Выбранный класс невозможно удалить, поскольку он используется как тип возвращаемого значения для одного или нескольких методов DataContext | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d68254a0-f3a1-47e2-aed3-a83471e1d711
caps.latest.revision: "3"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 865c8f9fa91c24eed1e10bde68b239932237a62b
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="the-selected-class-cannot-be-deleted-because-it-is-used-as-a-return-type-for-one-or-more-datacontext-methods"></a>Выбранный класс невозможно удалить, потому что он используется как тип возвращаемого значения одного или нескольких методов DataContext
Тип возврата одного или нескольких методов <xref:System.Data.Linq.DataContext> это выбранный класс сущностей. Удаление класса сущностей, который используется в качестве типа возврата для метода <xref:System.Data.Linq.DataContext>, вызовет ошибку компиляции проекта. Чтобы удалить выбранный класс сущностей, Идентифицируйте методы <xref:System.Data.Linq.DataContext>, которые его используют, и задайте их типам возврата другой класс сущностей.  
  
 Для возврата типов возврата <xref:System.Data.Linq.DataContext> методов к их исходным автоматически сгенерированным типам, сначала удалите <xref:System.Data.Linq.DataContext> метод из области методов и потом перетащите объект из **обозревателя серверов** / **Обозреватель баз данных** снова в реляционный конструктор.  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
1.  Определить <xref:System.Data.Linq.DataContext> методы, которые используются класс сущностей в качестве типа возврата, выбрав <xref:System.Data.Linq.DataContext> метод в методах области и проверив **тип возвращаемого значения** свойство в **свойства** окна .  
  
2.  Задать **тип возвращаемого значения** на другой класс сущностей или удалите <xref:System.Data.Linq.DataContext> метод из области методов.  
  
## <a name="see-also"></a>См. также
[Сообщения реляционного конструктора объектов](../data-tools/o-r-designer-messages.md)  
[Средства LINQ to SQL в Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)