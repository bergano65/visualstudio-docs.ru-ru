---
title: Этот связанный метод является базовым методом для следующая операция вставки по умолчанию, update или delete методы | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 62afa6da-97cf-48b9-8de3-33e4d72a0377
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 89421c61e34bf4ed98bcb8c2c8bd6ef93e1dae0b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="this-related-method-is-the-backing-method-for-the-following-default-insert-update-or-delete-methods"></a>Этот связанный метод является основным для следующих методов вставки, обновления и удаления по умолчанию
Этот связанный метод является базовым методом для следующих методов вставки, обновления или удаления по умолчанию. Если он удаляется, то эти методы также удаляются. Продолжить?  
  
 Выбранный метод `DataContext` сейчас используется как один из методов удаления, обновления или удаления для одного из классов сущностей на реляционном конструкторе объектов. Удаление выбранного метода вызовет класс объекта, который использовал этот метод для возврата к заданному по умолчанию поведению во время выполнения для выполнения Вставки, обновления или Удаления во время обновления.  
  
### <a name="to-delete-the-selected-method-causing-the-entity-class-to-use-runtime-updates"></a>Для удаления выбранного метода, вынуждая класс сущностей использовать обновления среды выполнения  
  
-   Нажмите кнопку **Да**.  
  
     Выбранный метод удаляется, и любые классы, которые использовали этот метод для переопределения поведения обновления, возвращаются к использованию поведения LINQ to SQL по умолчанию во время выполнения.  
  
### <a name="to-close-the-message-box-leaving-the-selected-method-unchanged"></a>Для закрытия окна сообщения, оставляя выбранный метод неизмененным  
  
-   Нажмите кнопку **Нет**.  
  
     Окно сообщения закрывается без сохранения изменений.  
  
## <a name="see-also"></a>См. также
[Сообщения реляционного конструктора объектов](../data-tools/o-r-designer-messages.md)  
[Средства LINQ to SQL в Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)