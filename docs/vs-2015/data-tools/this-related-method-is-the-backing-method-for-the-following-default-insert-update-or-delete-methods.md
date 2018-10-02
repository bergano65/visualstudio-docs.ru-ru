---
title: Этот связанный метод является базовым методом для следующих по умолчанию insert, update или методов delete | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 62afa6da-97cf-48b9-8de3-33e4d72a0377
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9f487bab485d11446d8e3f920d04c35a64591771
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47561661"
---
# <a name="this-related-method-is-the-backing-method-for-the-following-default-insert-update-or-delete-methods"></a>Этот связанный метод является основным для следующих методов вставки, обновления и удаления по умолчанию
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [этот связанный метод является базовым методом для следующих по умолчанию insert, update или методов delete](https://docs.microsoft.com/visualstudio/data-tools/this-related-method-is-the-backing-method-for-the-following-default-insert-update-or-delete-methods).  
  
  
Этот связанный метод является базовым методом для следующих методов вставки, обновления или удаления по умолчанию. Если он удаляется, то эти методы также удаляются. Продолжить?  
  
 Выбранный метод `DataContext` сейчас используется как один из методов удаления, обновления или удаления для одного из классов сущностей на реляционном конструкторе объектов. Удаление выбранного метода вызовет класс объекта, который использовал этот метод для возврата к заданному по умолчанию поведению во время выполнения для выполнения Вставки, обновления или Удаления во время обновления.  
  
### <a name="to-delete-the-selected-method-causing-the-entity-class-to-use-runtime-updates"></a>Для удаления выбранного метода, вынуждая класс сущностей использовать обновления среды выполнения  
  
-   Нажмите кнопку **Да**.  
  
     Выбранный метод удаляется, и любые классы, которые использовали этот метод для переопределения поведения обновления, возвращаются к использованию поведения LINQ to SQL по умолчанию во время выполнения.  
  
### <a name="to-close-the-message-box-leaving-the-selected-method-unchanged"></a>Для закрытия окна сообщения, оставляя выбранный метод неизмененным  
  
-   Нажмите кнопку **Нет**.  
  
     Окно сообщения закрывается без сохранения изменений.  
  
## <a name="see-also"></a>См. также  
 [Методы DataContext (реляционный конструктор объектов)](../data-tools/datacontext-methods-o-r-designer.md)   
 [Практическое: назначение хранимых процедур для выполнения обновлений, вставок и удалений (реляционный конструктор объектов)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)   
 [Средства LINQ to SQL в Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)

