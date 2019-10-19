---
title: Конструктор не может быть изменен во время отладки | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 487dafe4-d57c-4be1-9e3a-bb0a8699b2fa
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a8e393ad46b6d37bd74806a0a4b84825bd059457
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672271"
---
# <a name="the-designer-cannot-be-modified-while-debugging"></a>Невозможно изменить конструктор во время отладки
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Это сообщение появляется, когда осуществляется попытка изменить элементы на реляционном конструкторе объектов, когда приложение выполняется в режиме отладки. Когда приложение выполняется в режиме отладки, реляционный конструктор объектов доступен только для чтения.

### <a name="to-correct-this-error"></a>Исправление ошибки

- В меню **Отладка** выберите команду **прерывать отладку** .

     Приложение выходит из режима отладки, и элементы в реляционном конструкторе объектов можно изменять.

## <a name="see-also"></a>См. также раздел
 [LINQ to SQL средства в Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [Пошаговое руководство. Создание классов LINQ to SQL (реляционный конструктор R)](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)
