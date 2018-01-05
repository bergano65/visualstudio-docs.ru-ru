---
title: "CA1030: Используйте события, если это уместно | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- UseEventsWhereAppropriate
- CA1030
helpviewer_keywords:
- CA1030
- UseEventsWhereAppropriate
ms.assetid: ea051367-deeb-40f9-9b65-eb818f1e133a
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 616c79e67662407562f735f5cddd2c0bf2796797
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="ca1030-use-events-where-appropriate"></a>CA1030: используйте события, если это уместно
|||  
|-|-|  
|TypeName|UseEventsWhereAppropriate|  
|CheckId|CA1030|  
|Категория|Microsoft.Design|  
|Критическое изменение|Не критическое|  
  
## <a name="cause"></a>Причина  
 Имя метода на открытый, защищенный или закрытый начинается с одного из следующих:  
  
-   Дополнительный компонент  
  
-   RemoveOn  
  
-   Пожара  
  
-   Raise  
  
## <a name="rule-description"></a>Описание правила  
 Данное правило отслеживает методы с именами, которые, как правило, используются для событий. События следуют шаблон разработки наблюдателя или публикации-подписки; они используются, когда изменения состояния в одном объекте должен иметь возможность взаимодействия с другими объектами. Если метод вызывается в ответ на четко определенное изменение состояния, метод должен быть вызван обработчик событий. Объекты, вызывающие методы, должны создавать события, а не вызывать методы напрямую.  
  
 Типичными примерами событий находятся в приложениях пользовательского интерфейса, когда действие пользователя, например на нажатие кнопки приводит к сегмент кода для выполнения. [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] Модель событий не ограничивается пользовательскими интерфейсами; он должен использоваться в любом месте, необходимо сообщить состояние изменяется на один или несколько объектов.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Если метод вызывается при изменении состояния объекта, рассмотрите возможность изменения схемы для использования [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] модель событий.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Отключайте предупреждение из этого правила, если метод не работает с [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] модель событий.