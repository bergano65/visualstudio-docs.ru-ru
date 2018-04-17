---
title: Конструктор не может быть изменен при отладке | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 487dafe4-d57c-4be1-9e3a-bb0a8699b2fa
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: faa5fd73bdfdcb130c86a21c7554b3af4d48b716
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="the-designer-cannot-be-modified-while-debugging"></a>Невозможно изменить конструктор во время отладки
Это сообщение появляется, когда осуществляется попытка изменить элементы на реляционном конструкторе объектов, когда приложение выполняется в режиме отладки. Когда приложение выполняется в режиме отладки, реляционный конструктор объектов доступен только для чтения.  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
-   Нажмите кнопку **остановить отладку** на **отладки** меню.  
  
     Приложение выходит из режима отладки, и элементы в реляционном конструкторе объектов можно изменять.  
  
## <a name="see-also"></a>См. также
[Сообщения реляционного конструктора объектов](../data-tools/o-r-designer-messages.md)  
[Средства LINQ to SQL в Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)