---
title: "Свойство &lt;имя свойства&gt; невозможно удалить, так как оно участвует в ассоциации &lt;имя ассоциации&gt; | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 389873cc-92dd-48da-bfca-0f6c8e0ae3c2
caps.latest.revision: "3"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.workload: data-storage
ms.openlocfilehash: 44a83e15cd712fb98c697b68b1dccaea5d0caf99
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="the-property-ltproperty-namegt-cannot-be-deleted-because-it-is-participating-in-the-association-ltassociation-namegt"></a>Свойство &lt;имя свойства&gt; невозможно удалить, так как оно участвует в ассоциации &lt;имя связи&gt;
Выбранное свойство имеет значение **свойство ассоциации** для ассоциации между классами, указанными в сообщении об ошибке. Свойства не могут быть удалены, если они участвуют в ассоциации между классами данных.  
  
 Задать **свойство ассоциации** другое свойство класса данных, чтобы дать возможность успешного удаления нужного свойства.  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
1.  В реляционном конструкторе объектов выберите линию ассоциацию, которая соединяет классы данных, указанные в сообщении об ошибке.  
  
2.  Дважды щелкните строку, чтобы открыть **Редактор ассоциаций** диалоговое окно.  
  
3.  Удалите свойство из **свойства ассоциации**.  
  
4.  Попытайтесь снова удалить свойство.  
  
## <a name="see-also"></a>См. также
[Сообщения реляционного конструктора объектов](../data-tools/o-r-designer-messages.md)  
[Средства LINQ to SQL в Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)