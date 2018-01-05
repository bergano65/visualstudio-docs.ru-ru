---
title: "Этот связанный метод является базовым методом для следующая операция вставки по умолчанию, update или delete методы | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 62afa6da-97cf-48b9-8de3-33e4d72a0377
caps.latest.revision: "3"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: cb3f6c23d4994346dab26e800c116ad0c7301f4a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
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