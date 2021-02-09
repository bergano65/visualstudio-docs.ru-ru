---
title: Невозможно изменить конструктор во время отладки
description: Конструктор не может быть изменен во время отладки. Просмотрите сведения об этом сообщении Visual Studio реляционный конструктор объектов (O/R Designer).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: 487dafe4-d57c-4be1-9e3a-bb0a8699b2fa
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 244fbcc21c062c50b2f61940a1b43cf17c22761f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99866441"
---
# <a name="the-designer-cannot-be-modified-while-debugging"></a>Невозможно изменить конструктор во время отладки

Это сообщение появляется, когда осуществляется попытка изменить элементы на **реляционном конструкторе объектов**, в то время как приложение выполняется в режиме отладки. Если приложение выполняется в режиме отладки, **конструктор O/R** доступен только для чтения.

Чтобы исправить эту ошибку, выберите пункт **прерывать отладку** в меню **Отладка** . Приложение останавливает отладку и может изменять элементы в **конструкторе O/R**.

## <a name="see-also"></a>См. также раздел

- [Инструменты LINQ to SQL в Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
