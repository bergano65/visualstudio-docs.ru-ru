---
title: Невозможно изменить конструктор во время отладки
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 487dafe4-d57c-4be1-9e3a-bb0a8699b2fa
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 77034b422f710bd6e7811679f35024b543a91558
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72648154"
---
# <a name="the-designer-cannot-be-modified-while-debugging"></a>Невозможно изменить конструктор во время отладки

Это сообщение появляется, когда осуществляется попытка изменить элементы на **реляционном конструкторе объектов**, в то время как приложение выполняется в режиме отладки. Когда приложение выполняется в режиме отладки, **реляционный конструктор объектов** доступен только для чтения.

Чтобы исправить эту ошибку, выберите пункт **прерывать отладку** в меню **Отладка** . Приложение останавливает отладку и может изменять элементы в **конструкторе O/R**.

## <a name="see-also"></a>См. также

- [Средства LINQ to SQL в Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)