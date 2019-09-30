---
title: CA1026. Не следует использовать параметры по умолчанию
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1026
- DefaultParametersShouldNotBeUsed
helpviewer_keywords:
- CA1026
- DefaultParametersShouldNotBeUsed
ms.assetid: 09643415-36ef-4d0f-9411-5721e14e2512
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 62de7654083f3fd64f95401f95e5ee593effb27d
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236133"
---
# <a name="ca1026-default-parameters-should-not-be-used"></a>CA1026. Не следует использовать параметры по умолчанию

|||
|-|-|
|TypeName|DefaultParametersShouldNotBeUsed|
|CheckId|CA1026|
|Категория|Microsoft. Design|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина:
Тип, видимый извне, содержит метод, видимый извне, который использует параметр по умолчанию.

## <a name="rule-description"></a>Описание правила
Методы, использующие параметры по умолчанию, разрешены в спецификации CLS; Однако CLS позволяет компиляторам игнорировать значения, назначенные этим параметрам. Код, написанный для компиляторов, игнорирующих значения параметров по умолчанию, должен явно предоставлять аргументы для каждого параметра по умолчанию. Для поддержания поведения в разных языках программирования методы, использующие параметры по умолчанию, должны заменяться перегрузками методов, предоставляющими параметры по умолчанию.

Компилятор игнорирует значения параметров по умолчанию для управляемого расширения, C++ когда оно обращается к управляемому коду. Компилятор Visual Basic поддерживает методы, имеющие параметры по умолчанию, которые используют ключевое слово [Optional](/dotnet/visual-basic/language-reference/modifiers/optional) .

## <a name="how-to-fix-violations"></a>Устранение нарушений
Чтобы устранить нарушение этого правила, замените метод, использующий параметры по умолчанию, на перегрузки методов, которые предоставляют параметры по умолчанию.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения
Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
В следующем примере показан метод, использующий параметры по умолчанию, и перегруженные методы, которые предоставляют эквивалентную функциональность.

[!code-vb[FxCop.Design.DefaultParameters#1](../code-quality/codesnippet/VisualBasic/ca1026-default-parameters-should-not-be-used_1.vb)]

## <a name="related-rules"></a>Связанные правила
[CA1025 Замена повторяющихся аргументов массивом params](../code-quality/ca1025-replace-repetitive-arguments-with-params-array.md)

## <a name="see-also"></a>См. также
[Независимость от языка и независимые от языка компоненты](/dotnet/standard/language-independence-and-language-independent-components)