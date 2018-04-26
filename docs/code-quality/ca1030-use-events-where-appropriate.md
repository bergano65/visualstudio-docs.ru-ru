---
title: 'CA1030: используйте события, если это уместно'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UseEventsWhereAppropriate
- CA1030
helpviewer_keywords:
- CA1030
- UseEventsWhereAppropriate
ms.assetid: ea051367-deeb-40f9-9b65-eb818f1e133a
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9349321319b8bab81a2d9e7b52e7f2d25e87f796
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
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