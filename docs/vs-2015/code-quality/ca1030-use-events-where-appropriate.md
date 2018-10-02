---
title: 'CA1030: Используйте события, если это уместно | Документация Майкрософт'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- UseEventsWhereAppropriate
- CA1030
helpviewer_keywords:
- CA1030
- UseEventsWhereAppropriate
ms.assetid: ea051367-deeb-40f9-9b65-eb818f1e133a
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 8100aff6c2215d9a5fa031d69fc0ee105e440e3a
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2018
ms.locfileid: "47592236"
---
# <a name="ca1030-use-events-where-appropriate"></a>CA1030: используйте события, если это уместно
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [CA1030: используйте события, если это уместно](https://docs.microsoft.com/visualstudio/code-quality/ca1030-use-events-where-appropriate).

|||
|-|-|
|TypeName|UseEventsWhereAppropriate|
|CheckId|CA1030|
|Категория|Microsoft.Design|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Открытый, защищенный или закрытый метод имя начинается с одним из следующих:

-   Дополнительный компонент

-   RemoveOn

-   Fire

-   Raise

## <a name="rule-description"></a>Описание правила
 Данное правило отслеживает методы с именами, которые, как правило, используются для событий. События следуют шаблоне разработки наблюдателя или публикации-подписки; они используются при изменении состояния в один объект необходимо передать другим объектам. Если метод вызывается в ответ на четко определенное изменение состояния, метод должен вызываться с помощью обработчика событий. Объекты, вызывающие методы, должны создавать события, а не вызывать методы напрямую.

 Некоторые распространенные события находятся в приложениях пользовательского интерфейса, когда действия пользователя, например на нажатие кнопки приводит к сегмент кода для выполнения. [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] Модель событий не ограничивается пользовательские интерфейсы; он должен применяться везде, где необходимо сообщить состояние изменяется на один или несколько объектов.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Если метод вызывается при изменении состояния объекта, рекомендуется изменить способы использования [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] модель событий.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Отключайте предупреждение из этого правила, если метод не работает с [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] модель событий.



