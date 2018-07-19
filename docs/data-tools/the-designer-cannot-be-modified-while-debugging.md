---
title: Невозможно изменить конструктор во время отладки
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 487dafe4-d57c-4be1-9e3a-bb0a8699b2fa
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 1bed9629c40d4d7b7e93ccd250474ea90b44ab7c
ms.sourcegitcommit: f37affbc1b885dfe246d4b2c295a6538b383a0ca
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37174105"
---
# <a name="the-designer-cannot-be-modified-while-debugging"></a>Невозможно изменить конструктор во время отладки

Это сообщение появляется, когда предпринята попытка изменить элементы на **реляционный конструктор объектов** когда приложение выполняется в режиме отладки. Когда приложение выполняется в режиме отладки, **реляционный конструктор объектов** доступен только для чтения.

Чтобы исправить эту ошибку, выберите **остановить отладку** на **Отладка** меню. Приложение выходит из режима отладки, а также изменять элементы в **реляционный конструктор объектов**.

## <a name="see-also"></a>См. также

- [Сообщения реляционного конструктора объектов](../data-tools/o-r-designer-messages.md)
- [Средства LINQ to SQL в Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)