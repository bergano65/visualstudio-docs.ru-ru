---
title: Невозможно изменить конструктор во время отладки | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 487dafe4-d57c-4be1-9e3a-bb0a8699b2fa
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: eb021b5222c0c89d15ca9be9c9c155152118df5f
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59658777"
---
# <a name="the-designer-cannot-be-modified-while-debugging"></a>Невозможно изменить конструктор во время отладки
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Это сообщение появляется, когда осуществляется попытка изменить элементы на реляционном конструкторе объектов, когда приложение выполняется в режиме отладки. Когда приложение выполняется в режиме отладки, реляционный конструктор объектов доступен только для чтения.  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
-   Нажмите кнопку **остановить отладку** на **Отладка** меню.  
  
     Приложение выходит из режима отладки, и элементы в реляционном конструкторе объектов можно изменять.  
  
## <a name="see-also"></a>См. также  
 [Средства LINQ to SQL в Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [Пошаговое руководство: Создание классов LINQ to SQL (реляционный конструктор объектов)](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)   
 [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)
