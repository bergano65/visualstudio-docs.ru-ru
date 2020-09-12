---
title: Неподдерживаемые типы данных
description: Один или несколько выбранных элементов содержат тип данных, не поддерживаемый конструктором
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: 71dcd4f9-2946-42c5-9ce4-99c819ea2785
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 167146b9a7938e5498e8db023602b2e13f74379c
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/11/2020
ms.locfileid: "90034082"
---
# <a name="one-or-more-selected-items-contain-a-data-type-that-is-not-supported-by-the-designer"></a>Один или несколько выбранных элементов содержат тип данных, не поддерживаемый конструктором

Один или несколько элементов, которые были перемещены из **Обозреватель сервера** или **Обозреватель базы данных** в **Реляционный конструктор** объектов, содержат тип данных, который не поддерживается **реляционным конструктором**объектов, например [определяемыми пользователем типами CLR](/dotnet/framework/data/adonet/sql/clr-user-defined-types).

## <a name="to-correct-this-error"></a>Исправление ошибки

1. Создайте представление, которое основано на нужной таблице и которое не включает неподдерживаемый тип данных.

2. Перетащите представление из **Обозреватель сервера** или **Обозреватель базы данных** в конструктор.

## <a name="see-also"></a>См. также раздел

- [Инструменты LINQ to SQL в Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
