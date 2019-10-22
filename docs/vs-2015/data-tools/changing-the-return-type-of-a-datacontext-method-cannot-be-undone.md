---
title: Изменение типа возвращаемого значения метода DataContext не может быть отменено | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 76b161fc-5075-4192-8d94-f15b02e199e9
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f020aed4c1213d3db008862386704c0f63b86bde
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662472"
---
# <a name="changing-the-return-type-of-a-datacontext-method-cannot-be-undone"></a>Невозможно отменить замену типа данных, возвращаемых методом DataContext
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Операция изменения возвращаемого типа метода DataContext не может быть отменена. Чтобы возвратиться назад к автоматически сгенерированному типу, необходимо снова перетащить элемент из Обозревателя серверов/обозревателя базы данных на область реляционного конструктора объектов. Вы уверены, что хотите изменить тип возвращения?

 Тип возвращаемого значения метода <xref:System.Data.Linq.DataContext> различен в зависимости от того, куда вы сбросили элемент в [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. Если вы сбрасываете элемент прямо в существующий класс сущностей, то создается метод <xref:System.Data.Linq.DataContext>, который имеет тип возврата класса сущностей. Если вы сбрасываете элемент на пустую область конструктора [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)], то создается метод <xref:System.Data.Linq.DataContext>, который возвращает автоматически сгенерированный тип. Можно изменить тип возвращаемого значения метода <xref:System.Data.Linq.DataContext> после его добавления в область методов. Чтобы проверить или изменить тип возврата метода <xref:System.Data.Linq.DataContext>, выберите его и щелкните по свойству **Тип возврата** в окне **Свойства**.

### <a name="to-change-the-return-type-of-a-datacontext"></a>Для изменения типа возврата метода DataContext

- Щелкните **Да**.

### <a name="to-exit-the-message-box-and-leave-the-return-type-unchanged"></a>Для закрытия окна сообщения, оставляя тип возвращаемого значения неизмененным

- Нажмите кнопку **Нет**.

### <a name="to-revert-to-the-original-return-type-after-changing-the-return-type"></a>Чтобы возвратиться к первоначальному типу возврата после изменения типа возврата

1. Выберите метод <xref:System.Data.Linq.DataContext> на [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] и удалите его.

2. Найдите элемент в **обозревателе серверов/обозревателе базы данных** и перетащите его на [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].

     Метод <xref:System.Data.Linq.DataContext> создается с первоначальным типом возвращаемого значения по умолчанию.

## <a name="see-also"></a>См. также раздел
 [LINQ to SQL средства в](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [методах DataContext Visual Studio (реляционный конструктор)](../data-tools/datacontext-methods-o-r-designer.md) [как создать методы DataContext, сопоставленные с хранимыми процедурами и функциями (реляционный конструктор r)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)
