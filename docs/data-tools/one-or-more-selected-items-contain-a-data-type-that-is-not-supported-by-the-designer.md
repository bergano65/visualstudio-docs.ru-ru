---
title: Один или несколько выбранных элементов содержат тип данных, не поддерживаемый конструктором
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 71dcd4f9-2946-42c5-9ce4-99c819ea2785
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: e27cf5c7cd6c6cb16de317e014083af405236019
ms.sourcegitcommit: 50f0c3f2763a05de8482b3579026d9c76c0e226c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/09/2019
ms.locfileid: "65460593"
---
# <a name="one-or-more-selected-items-contain-a-data-type-that-is-not-supported-by-the-designer"></a>Один или несколько выбранных элементов содержат тип данных, не поддерживаемый конструктором

Один или несколько элементов, перетащить из **обозревателя серверов** или **обозреватель баз данных** на **реляционный конструктор объектов** содержит тип данных, который не поддерживается **O /R конструктор**, например [определяемых пользователем типов CLR](/dotnet/framework/data/adonet/sql/clr-user-defined-types).

## <a name="to-correct-this-error"></a>Исправление ошибки

1. Создайте представление, которое основано на нужной таблице и которое не включает неподдерживаемый тип данных.

2. Перетащите представление из **обозревателя серверов** или **обозреватель баз данных** в конструктор.

## <a name="see-also"></a>См. также

- [Средства LINQ to SQL в Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)