---
title: Выбранный класс невозможно удалить, потому что он используется как возвращаемый тип одного или нескольких методов DataContext
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: d68254a0-f3a1-47e2-aed3-a83471e1d711
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 249a5338985983509f04e0ff268b2f30e2773f71
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/16/2020
ms.locfileid: "76113557"
---
# <a name="the-selected-class-cannot-be-deleted-because-it-is-used-as-a-return-type-for-one-or-more-datacontext-methods"></a>Выбранный класс невозможно удалить, потому что он используется как возвращаемый тип одного или нескольких методов DataContext

Тип возвращаемого значения одного или нескольких методов <xref:System.Data.Linq.DataContext> это выбранный класс сущностей. Удаление класса сущности, используемого в качестве типа возвращаемого значения для <xref:System.Data.Linq.DataContext> метода, приводит к сбою компиляции проекта. Чтобы удалить выбранный класс сущностей, Идентифицируйте методы <xref:System.Data.Linq.DataContext>, которые его используют, и задайте их типам возврата другой класс сущностей.

Для возврата типов возврата методов <xref:System.Data.Linq.DataContext> к их исходным автоматически сгенерированным типам сначала удалите метод <xref:System.Data.Linq.DataContext> из области **методов** и потом перетащите объект из **Обозревателя серверов**/**Обозревателя базы данных** снова в **реляционный конструктор объектов**.

## <a name="to-correct-this-error"></a>Исправление ошибки

1. Идентифицируйте методы <xref:System.Data.Linq.DataContext>, которые используют класс сущностей в качестве типа возврата, выбрав метод <xref:System.Data.Linq.DataContext> в области **методов** и проверив свойство **Тип возврата** в окне **Свойства**.

2. Установите **Тип возврата<xref:System.Data.Linq.DataContext> на другой класс сущностей или удалите метод**  из области методов.

## <a name="see-also"></a>См. также:

- [Средства LINQ to SQL в Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
