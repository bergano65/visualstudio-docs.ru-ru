---
title: Невозможно изменить конструктор во время отладки
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 487dafe4-d57c-4be1-9e3a-bb0a8699b2fa
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 1667277e4f833ddcd6c2b2e077898ae5c76aada4
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/16/2020
ms.locfileid: "76113567"
---
# <a name="the-designer-cannot-be-modified-while-debugging"></a>Невозможно изменить конструктор во время отладки

Это сообщение появляется, когда осуществляется попытка изменить элементы на **реляционном конструкторе объектов**, в то время как приложение выполняется в режиме отладки. Когда приложение выполняется в режиме отладки, **реляционный конструктор объектов** доступен только для чтения.

Чтобы исправить эту ошибку, выберите пункт **прерывать отладку** в меню **Отладка** . Приложение останавливает отладку и может изменять элементы в **конструкторе O/R**.

## <a name="see-also"></a>См. также:

- [Средства LINQ to SQL в Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
