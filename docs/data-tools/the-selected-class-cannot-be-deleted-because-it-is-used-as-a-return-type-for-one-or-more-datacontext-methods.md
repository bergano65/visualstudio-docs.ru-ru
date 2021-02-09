---
title: Выбранный класс не может быть удален
description: Выбранный класс невозможно удалить, потому что он используется как возвращаемый тип одного или нескольких методов DataContext
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: d68254a0-f3a1-47e2-aed3-a83471e1d711
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: a9948df37df4faf7cc5349b2729ca4f648d973cb
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99866389"
---
# <a name="the-selected-class-cannot-be-deleted-because-it-is-used-as-a-return-type-for-one-or-more-datacontext-methods"></a>Выбранный класс невозможно удалить, потому что он используется как возвращаемый тип одного или нескольких методов DataContext

Тип возвращаемого значения одного или нескольких методов <xref:System.Data.Linq.DataContext> это выбранный класс сущностей. Удаление класса сущности, используемого в качестве типа возвращаемого значения для <xref:System.Data.Linq.DataContext> метода, приводит к сбою компиляции проекта. Чтобы удалить выбранный класс сущностей, Идентифицируйте методы <xref:System.Data.Linq.DataContext>, которые его используют, и задайте их типам возврата другой класс сущностей.

Для возврата типов возврата методов <xref:System.Data.Linq.DataContext> к их исходным автоматически сгенерированным типам сначала удалите метод <xref:System.Data.Linq.DataContext> из области **методов** и потом перетащите объект из **Обозревателя серверов**/**Обозревателя базы данных** снова в **реляционный конструктор объектов**.

## <a name="to-correct-this-error"></a>Исправление ошибки

1. Идентифицируйте методы <xref:System.Data.Linq.DataContext>, которые используют класс сущностей в качестве типа возврата, выбрав метод <xref:System.Data.Linq.DataContext> в области **методов** и проверив свойство **Тип возврата** в окне **Свойства**.

2. Установите **Тип возврата<xref:System.Data.Linq.DataContext> на другой класс сущностей или удалите метод** из области методов.

## <a name="see-also"></a>См. также раздел

- [Инструменты LINQ to SQL в Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
