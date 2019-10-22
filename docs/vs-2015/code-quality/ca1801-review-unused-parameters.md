---
title: 'CA1801: Проверьте неиспользуемые параметры | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AvoidUnusedParameters
- CA1801
- ReviewUnusedParameters
helpviewer_keywords:
- CA1801
- ReviewUnusedParameters
ms.assetid: 5d73545c-e153-4b7c-a7b2-be6bf5aca5be
caps.latest.revision: 31
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: caf1ec865d604545940b0a5442947ef61bd60f9a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671529"
---
# <a name="ca1801-review-unused-parameters"></a>CA1801: проверьте неиспользуемые параметры
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю документацию по Visual Studio см. в разделе [CA1801: Проверка неиспользуемых параметров](https://docs.microsoft.com/visualstudio/code-quality/ca1801-review-unused-parameters).

|||
|-|-|
|TypeName|ReviewUnusedParameters|
|CheckId|CA1801|
|Категория|Microsoft. Usage|
|Критическое изменение|Не критическое — если элемент не виден за пределами сборки, независимо от внесенных изменений.<br /><br /> Не критическое — при изменении элемента на использование параметра в его теле.<br /><br /> Критическое — при удалении параметра он становится видимым за пределами сборки.|

## <a name="cause"></a>Причина
 Сигнатура метода включает параметр, не использующийся в основной части метода. Это правило не проверяет следующие методы:

- Методы, на которые ссылается делегат.

- Методы, используемые в качестве обработчиков событий.

- Методы, объявляемые с модификатором `abstract` (`MustOverride` в Visual Basic).

- Методы, объявляемые с модификатором `virtual` (`Overridable` в Visual Basic).

- Методы, объявляемые с модификатором `override` (`Overrides` в Visual Basic).

- Методы, объявленные с модификатором `extern` (оператор `Declare` в Visual Basic).

## <a name="rule-description"></a>Описание правила
 Проверьте параметры в невиртуальных методах, которые не используются в теле метода, чтобы убедиться, что не существует ошибок, связанных с доступом к ним. Неиспользуемые параметры приводят к затратам на обслуживание и производительность.

 Иногда нарушение этого правила может указывать на ошибку реализации в методе. Например, параметр должен использоваться в теле метода. Отключить предупреждения этого правила, если параметр должен существовать из-за обратной совместимости.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, удалите неиспользуемый параметр (критическое изменение) или используйте параметр в теле метода (некритическое изменение).

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Можно отключить вывод предупреждения из этого правила для ранее отгруженного кода, для которого исправление будет критическим изменением.

## <a name="example"></a>Пример
 В следующем примере показаны два метода. Один метод нарушает правило, а другой метод удовлетворяет этому правилу.

 [!code-csharp[FxCop.Usage.ReviewUnusedParameters#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.ReviewUnusedParameters/cs/FxCop.Usage.ReviewUnusedPerameters.cs#1)]

## <a name="related-rules"></a>Связанные правила
 [CA1811: не используйте невызываемый закрытый код](../code-quality/ca1811-avoid-uncalled-private-code.md)

 [CA1812: не создавайте внутренние классы без экземпляров](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

 [CA1804: удалите неиспользуемые локальные переменные](../code-quality/ca1804-remove-unused-locals.md)
