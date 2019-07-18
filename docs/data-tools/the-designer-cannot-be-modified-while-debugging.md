---
title: Невозможно изменить конструктор во время отладки
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 487dafe4-d57c-4be1-9e3a-bb0a8699b2fa
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 2e18a95aa2e4eb8a9238a046e3a77f3d618cdd2b
ms.sourcegitcommit: 50f0c3f2763a05de8482b3579026d9c76c0e226c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/09/2019
ms.locfileid: "65458365"
---
# <a name="the-designer-cannot-be-modified-while-debugging"></a>Невозможно изменить конструктор во время отладки

Это сообщение появляется, когда осуществляется попытка изменить элементы на **реляционном конструкторе объектов**, в то время как приложение выполняется в режиме отладки. Когда приложение выполняется в режиме отладки, **реляционный конструктор объектов** доступен только для чтения.

Чтобы исправить эту ошибку, выберите **остановить отладку** на **Отладка** меню. Приложение выходит из режима отладки, а также изменять элементы в **реляционный конструктор объектов**.

## <a name="see-also"></a>См. также

- [Средства LINQ to SQL в Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)