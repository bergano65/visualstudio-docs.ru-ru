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
ms.openlocfilehash: 1313c5ee79a7a13d3eb937a3431b13ea393857d1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "85544525"
---
# <a name="ca1030-use-events-where-appropriate"></a>CA1030. По возможности используйте события
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Элемент|Значение|
|-|-|
|TypeName|UseEventsWhereAppropriate|
|CheckId|CA1030|
|Категория|Microsoft. Design|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Имя открытого, защищенного или закрытого метода начинается с одного из следующих:

- AddOn

- RemoveOn

- Fire

- Вести

## <a name="rule-description"></a>Описание правила
 Данное правило отслеживает методы с именами, которые, как правило, используются для событий. События следуют шаблону разработки "наблюдатель" или "публикация-подписка"; они используются, когда изменение состояния одного объекта должно обмениваться данными с другими объектами. Если метод вызывается в ответ на четко определенное изменение состояния, метод должен вызываться обработчиком событий. Объекты, вызывающие методы, должны создавать события, а не вызывать методы напрямую.

 Некоторые распространенные примеры событий находятся в приложениях пользовательского интерфейса, в которых пользовательское действие, например нажатие кнопки, приводит к выполнению сегмента кода. [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]Модель событий не ограничивается пользовательскими интерфейсами. ее следует использовать в любом месте, когда необходимо передать изменения состояния в один или несколько объектов.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Если метод вызывается при изменении состояния объекта, следует рассмотреть возможность изменения структуры для использования [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] модели событий.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Подавлять предупреждение из этого правила, если метод не работает с [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] моделью событий.
