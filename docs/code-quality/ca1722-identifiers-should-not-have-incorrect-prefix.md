---
title: CA1722. Идентификаторы не должны иметь неправильные префиксы
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- IdentifiersShouldNotHaveIncorrectPrefix
- CA1722
helpviewer_keywords:
- CA1722
- IdentifiersShouldNotHaveIncorrectPrefix
ms.assetid: c3313c51-d004-4f9a-a0d1-6c4c4a1fb1e6
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bea94b555be5079deae5a021cb5ecbd2ccd07adb
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53904751"
---
# <a name="ca1722-identifiers-should-not-have-incorrect-prefix"></a>CA1722. Идентификаторы не должны иметь неправильные префиксы

|||
|-|-|
|TypeName|IdentifiersShouldNotHaveIncorrectPrefix|
|CheckId|CA1722|
|Категория|Microsoft.Naming|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Идентификатор имеет неверный префикс.

## <a name="rule-description"></a>Описание правила
 В соответствии с соглашением об именовании, только некоторые элементы программирования могут иметь имена, которые начинаются с особого префикса.

 Имена типов не имеют особого префикса и не должны иметь префикс «C». Это правило сообщает о нарушениях для имен типов, таких как «CMyClass» и не сообщает о нарушениях для имен типов, например «Кэш».

 Соглашения об именовании обеспечивают единообразие библиотек, предназначенных среда CLR. Эта согласованность уменьшает обучения, требуемом для новых библиотек программного обеспечения и повышает уверенность клиента в том, что библиотека была разработана тому, кто имеет опыт в разработке управляемого кода.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Удалите префикс из идентификатора.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="related-rules"></a>Связанные правила
 [CA1715: Идентификаторы должны иметь правильные префиксы](../code-quality/ca1715-identifiers-should-have-correct-prefix.md)