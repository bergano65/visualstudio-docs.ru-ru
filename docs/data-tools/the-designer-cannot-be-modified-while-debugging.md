---
title: Невозможно изменить конструктор во время отладки
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: 487dafe4-d57c-4be1-9e3a-bb0a8699b2fa
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 483267e2e570efbcc3cc1842560014ee9ba73d11
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/23/2020
ms.locfileid: "85281452"
---
# <a name="the-designer-cannot-be-modified-while-debugging"></a>Невозможно изменить конструктор во время отладки

Это сообщение появляется, когда осуществляется попытка изменить элементы на **реляционном конструкторе объектов**, в то время как приложение выполняется в режиме отладки. Если приложение выполняется в режиме отладки, **конструктор O/R** доступен только для чтения.

Чтобы исправить эту ошибку, выберите пункт **прерывать отладку** в меню **Отладка** . Приложение останавливает отладку и может изменять элементы в **конструкторе O/R**.

## <a name="see-also"></a>См. также

- [Средства LINQ to SQL в Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
