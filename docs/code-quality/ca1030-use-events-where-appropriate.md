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
ms.openlocfilehash: 6d1b0bac434ad7a182dc56ac08173646068623bd
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/13/2018
ms.locfileid: "45547555"
---
# <a name="ca1030-use-events-where-appropriate"></a>CA1030: используйте события, если это уместно
|||
|-|-|
|TypeName|UseEventsWhereAppropriate|
|CheckId|CA1030|
|Категория|Microsoft.Design|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Открытый, защищенный или закрытый метод имя начинается с одним из следующих:

- Дополнительный компонент

- RemoveOn

- Fire

- Raise

## <a name="rule-description"></a>Описание правила
 Данное правило отслеживает методы с именами, которые, как правило, используются для событий. События следуют шаблоне разработки наблюдателя или публикации-подписки; они используются при изменении состояния в один объект необходимо передать другим объектам. Если метод вызывается в ответ на четко определенное изменение состояния, метод должен вызываться с помощью обработчика событий. Объекты, вызывающие методы, должны создавать события, а не вызывать методы напрямую.

 Некоторые распространенные события находятся в приложениях пользовательского интерфейса, когда действия пользователя, например на нажатие кнопки приводит к сегмент кода для выполнения. [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] Модель событий не ограничивается пользовательские интерфейсы; он должен применяться везде, где необходимо сообщить состояние изменяется на один или несколько объектов.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Если метод вызывается при изменении состояния объекта, рекомендуется изменить способы использования [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] модель событий.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Отключайте предупреждение из этого правила, если метод не работает с [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] модель событий.