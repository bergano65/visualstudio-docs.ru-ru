---
title: Невозможно изменить конструктор во время отладки
description: Конструктор не может быть изменен во время отладки. Просмотрите сведения об этом сообщении Visual Studio реляционный конструктор объектов (O/R Designer).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: 487dafe4-d57c-4be1-9e3a-bb0a8699b2fa
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: f83462328897a8a02b068507d0fa6903bad49367
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/10/2020
ms.locfileid: "94434835"
---
# <a name="the-designer-cannot-be-modified-while-debugging"></a>Невозможно изменить конструктор во время отладки

Это сообщение появляется, когда осуществляется попытка изменить элементы на **реляционном конструкторе объектов** , в то время как приложение выполняется в режиме отладки. Если приложение выполняется в режиме отладки, **конструктор O/R** доступен только для чтения.

Чтобы исправить эту ошибку, выберите пункт **прерывать отладку** в меню **Отладка** . Приложение останавливает отладку и может изменять элементы в **конструкторе O/R**.

## <a name="see-also"></a>См. также раздел

- [Инструменты LINQ to SQL в Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
