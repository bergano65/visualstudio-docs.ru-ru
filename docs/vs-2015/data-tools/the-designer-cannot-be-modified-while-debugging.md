---
title: Невозможно изменить конструктор во время отладки | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 487dafe4-d57c-4be1-9e3a-bb0a8699b2fa
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9efa18c7b27f744b56aa3c3c192903690b79e47b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47572566"
---
# <a name="the-designer-cannot-be-modified-while-debugging"></a>Невозможно изменить конструктор во время отладки
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [невозможно изменить конструктор во время отладки](https://docs.microsoft.com/visualstudio/data-tools/the-designer-cannot-be-modified-while-debugging).  
  
  
Это сообщение появляется, когда осуществляется попытка изменить элементы на реляционном конструкторе объектов, когда приложение выполняется в режиме отладки. Когда приложение выполняется в режиме отладки, реляционный конструктор объектов доступен только для чтения.  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
-   Нажмите кнопку **остановить отладку** на **Отладка** меню.  
  
     Приложение выходит из режима отладки, и элементы в реляционном конструкторе объектов можно изменять.  
  
## <a name="see-also"></a>См. также  
 [Средства LINQ to SQL в Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [Пошаговое руководство: Создание классов LINQ to SQL (реляционный конструктор объектов)](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)   
 [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)

