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
ms.openlocfilehash: e4055c4096895645edf8dfdab8318622a100e6e3
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2019
ms.locfileid: "55955587"
---
# <a name="the-designer-cannot-be-modified-while-debugging"></a>Невозможно изменить конструктор во время отладки

Это сообщение появляется, когда осуществляется попытка изменить элементы на **реляционном конструкторе объектов**, в то время как приложение выполняется в режиме отладки. Когда приложение выполняется в режиме отладки, **реляционный конструктор объектов** доступен только для чтения.

Чтобы исправить эту ошибку, выберите **остановить отладку** на **Отладка** меню. Приложение выходит из режима отладки, а также изменять элементы в **реляционный конструктор объектов**.

## <a name="see-also"></a>См. также

- [Сообщения реляционного конструктора объектов](../data-tools/o-r-designer-messages.md)
- [Средства LINQ to SQL в Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)