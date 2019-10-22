---
title: 'CA1030: используйте события, если это уместно | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UseEventsWhereAppropriate
- CA1030
helpviewer_keywords:
- CA1030
- UseEventsWhereAppropriate
ms.assetid: ea051367-deeb-40f9-9b65-eb818f1e133a
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 7ab3a576b5014799e470260567a4942b5c3ef9de
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661924"
---
# <a name="ca1030-use-events-where-appropriate"></a>CA1030: используйте события, если это уместно
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|UseEventsWhereAppropriate|
|CheckId|CA1030|
|Категория|Microsoft. Design|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Имя открытого, защищенного или закрытого метода начинается с одного из следующих:

- AddOn

- RemoveOn

- Срабатывание

- Вести

## <a name="rule-description"></a>Описание правила
 Данное правило отслеживает методы с именами, которые, как правило, используются для событий. События следуют шаблону разработки "наблюдатель" или "публикация-подписка"; они используются, когда изменение состояния одного объекта должно обмениваться данными с другими объектами. Если метод вызывается в ответ на четко определенное изменение состояния, метод должен вызываться обработчиком событий. Объекты, вызывающие методы, должны создавать события, а не вызывать методы напрямую.

 Некоторые распространенные примеры событий находятся в приложениях пользовательского интерфейса, в которых пользовательское действие, например нажатие кнопки, приводит к выполнению сегмента кода. Модель событий [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] не ограничивается пользовательскими интерфейсами; его следует использовать в любом месте, где необходимо передать изменения состояния одному или нескольким объектам.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Если метод вызывается при изменении состояния объекта, следует рассмотреть возможность изменения макета для использования модели событий [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Подавлять предупреждение из этого правила, если метод не работает с моделью событий [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].
