---
title: Выбранный класс невозможно удалить, потому что он используется как возвращаемый тип одного или нескольких методов DataContext
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: d68254a0-f3a1-47e2-aed3-a83471e1d711
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 3b577dc32a233d1f18518aa27001f340c634314c
ms.sourcegitcommit: 50f0c3f2763a05de8482b3579026d9c76c0e226c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/09/2019
ms.locfileid: "65458172"
---
# <a name="the-selected-class-cannot-be-deleted-because-it-is-used-as-a-return-type-for-one-or-more-datacontext-methods"></a>Выбранный класс невозможно удалить, потому что он используется как возвращаемый тип одного или нескольких методов DataContext

Тип возвращаемого значения одного или нескольких методов <xref:System.Data.Linq.DataContext> это выбранный класс сущностей. Удаление класса сущностей, который используется как тип возвращаемого значения для <xref:System.Data.Linq.DataContext> метод приводит к компиляции проекта переход на другой. Чтобы удалить выбранный класс сущностей, Идентифицируйте методы <xref:System.Data.Linq.DataContext>, которые его используют, и задайте их типам возврата другой класс сущностей.

Для возврата типов возврата методов <xref:System.Data.Linq.DataContext> к их исходным автоматически сгенерированным типам сначала удалите метод <xref:System.Data.Linq.DataContext> из области **методов** и потом перетащите объект из **Обозревателя серверов**/**Обозревателя базы данных** снова в **реляционный конструктор объектов**.

## <a name="to-correct-this-error"></a>Исправление ошибки

1. Идентифицируйте методы <xref:System.Data.Linq.DataContext>, которые используют класс сущностей в качестве типа возврата, выбрав метод <xref:System.Data.Linq.DataContext> в области **методов** и проверив свойство **Тип возврата** в окне **Свойства**.

2. Установите **Тип возврата<xref:System.Data.Linq.DataContext> на другой класс сущностей или удалите метод**  из области методов.

## <a name="see-also"></a>См. также

- [Средства LINQ to SQL в Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)