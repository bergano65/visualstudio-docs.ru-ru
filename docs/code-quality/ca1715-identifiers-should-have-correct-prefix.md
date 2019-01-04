---
title: CA1715. Идентификаторы должны иметь правильные префиксы
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA1715
- IdentifiersShouldHaveCorrectPrefix
helpviewer_keywords:
- IdentifiersShouldHaveCorrectPrefix
- CA1715
ms.assetid: cf45f8df-6855-4cb6-a4e2-7cfed714cf2f
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 7c7abdaa2356bdf622f0892e9b027047fc021096
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53912929"
---
# <a name="ca1715-identifiers-should-have-correct-prefix"></a>CA1715. Идентификаторы должны иметь правильные префиксы

|||
|-|-|
|TypeName|IdentifiersShouldHaveCorrectPrefix|
|CheckId|CA1715|
|Категория|Microsoft.Naming|
|Критическое изменение|Критическое, если возникает в интерфейсах.<br /><br /> Не критическое — при возникновении на параметры универсального типа.|

## <a name="cause"></a>Причина
 Имя видимого интерфейса не начинается с прописные «I».

 - или -

 Имя параметра универсального типа в видимый извне тип или методе не начинается с заглавной 'T'.

## <a name="rule-description"></a>Описание правила
 По соглашению имена некоторых элементов программирования начинаются с особого префикса.

 Интерфейс имена должны начинаться с заглавной, «I» следуют другая прописная буква. Это правило выдает сообщение нарушения для имени интерфейса, такие как «MyInterface» и «IsolatedInterface».

 Имена параметров универсального типа должны начинаться с заглавной 'T' и при необходимости может следовать другая прописная буква. Это правило выдает сообщение нарушения для определения имен параметров универсального типа, таких как «V» и «Тип».

 Соглашения об именовании обеспечивают единообразие библиотек, предназначенных среда CLR. Это уменьшает обучения, необходимый для новых библиотек программного обеспечения и повышает уверенность клиента в том, что библиотека была разработана тому, кто имеет опыт в разработке управляемого кода.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Переименуйте идентификатор, чтобы он правильно добавлен префикс.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
 **В следующем примере интерфейс с неправильным именем.**

 [!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix#1](../code-quality/codesnippet/CPP/ca1715-identifiers-should-have-correct-prefix_1.cpp)]
 [!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix#1](../code-quality/codesnippet/VisualBasic/ca1715-identifiers-should-have-correct-prefix_1.vb)]
 [!code-csharp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix#1](../code-quality/codesnippet/CSharp/ca1715-identifiers-should-have-correct-prefix_1.cs)]

## <a name="example"></a>Пример
 **В следующем примере устраняется нарушение устраняется с помощью префикса интерфейса с помощью «I».**

 [!code-csharp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2#1](../code-quality/codesnippet/CSharp/ca1715-identifiers-should-have-correct-prefix_2.cs)]
 [!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2#1](../code-quality/codesnippet/CPP/ca1715-identifiers-should-have-correct-prefix_2.cpp)]
 [!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2#1](../code-quality/codesnippet/VisualBasic/ca1715-identifiers-should-have-correct-prefix_2.vb)]

## <a name="example"></a>Пример
 **В следующем примере является параметром универсального типа с неправильным именем.**

 [!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3#1](../code-quality/codesnippet/CPP/ca1715-identifiers-should-have-correct-prefix_3.cpp)]
 [!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3#1](../code-quality/codesnippet/VisualBasic/ca1715-identifiers-should-have-correct-prefix_3.vb)]
 [!code-csharp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3#1](../code-quality/codesnippet/CSharp/ca1715-identifiers-should-have-correct-prefix_3.cs)]

## <a name="example"></a>Пример
 **В следующем примере устраняется нарушение устраняется с помощью префикса параметра универсального типа т ".**

 [!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4#1](../code-quality/codesnippet/CPP/ca1715-identifiers-should-have-correct-prefix_4.cpp)]
 [!code-csharp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4#1](../code-quality/codesnippet/CSharp/ca1715-identifiers-should-have-correct-prefix_4.cs)]
 [!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4#1](../code-quality/codesnippet/VisualBasic/ca1715-identifiers-should-have-correct-prefix_4.vb)]

## <a name="related-rules"></a>Связанные правила
 [CA1722: Идентификаторы не должны иметь неверные префиксы](../code-quality/ca1722-identifiers-should-not-have-incorrect-prefix.md)