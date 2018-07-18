---
title: 'CA1026: не следует использовать параметры по умолчанию'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7bf28c16bc5457309c2de42d79574dbb64739d9e
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
ms.locfileid: "31901651"
---
# <a name="ca1026-default-parameters-should-not-be-used"></a>CA1026: не следует использовать параметры по умолчанию
|||
|-|-|
|TypeName|DefaultParametersShouldNotBeUsed|
|CheckId|CA1026|
|Категория|Microsoft.Design|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Видимый извне тип содержит видимое извне метод, использующий параметр по умолчанию.

## <a name="rule-description"></a>Описание правила
 Методы, использующие параметры по умолчанию разрешены в общеязыковой спецификацией (CLS); Однако CLS разрешает компиляторам не учитывать значения, назначенные для этих параметров. Код, написанный для компиляторов, которые не учитывают значения параметров по умолчанию необходимо явно предоставить аргументы для каждого параметра по умолчанию. Для однородной работы с различными языками программирования, перегрузки методов, предоставляющие параметры по умолчанию следует заменять методы, использующие параметры по умолчанию.

 Компилятор игнорирует значения параметров по умолчанию для управляемых расширений для C++ при доступе к управляемому коду. Компилятор Visual Basic поддерживает методы с параметрами по умолчанию, использующих [необязательно](/dotnet/visual-basic/language-reference/modifiers/optional) ключевое слово.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение данного правила, замените метод, который использует параметры по умолчанию с помощью перегрузки методов, предоставляющие параметры по умолчанию.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
 В следующем примере показано метод, который использует параметры по умолчанию и перегруженные методы, обеспечивающие аналогичную функциональность.

 [!code-vb[FxCop.Design.DefaultParameters#1](../code-quality/codesnippet/VisualBasic/ca1026-default-parameters-should-not-be-used_1.vb)]

## <a name="related-rules"></a>Связанные правила
 [CA1025: замените повторяющиеся аргументы массивом параметров](../code-quality/ca1025-replace-repetitive-arguments-with-params-array.md)

## <a name="see-also"></a>См. также
 [Независимость от языка и независимые от языка компоненты](/dotnet/standard/language-independence-and-language-independent-components)