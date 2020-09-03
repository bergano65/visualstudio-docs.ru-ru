---
title: 'CA1715: идентификаторы должны иметь правильный префикс | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1715
- IdentifiersShouldHaveCorrectPrefix
helpviewer_keywords:
- IdentifiersShouldHaveCorrectPrefix
- CA1715
ms.assetid: cf45f8df-6855-4cb6-a4e2-7cfed714cf2f
caps.latest.revision: 31
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: fe362a58a047c8594d09bc6985c48d16f21d3b76
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545604"
---
# <a name="ca1715-identifiers-should-have-correct-prefix"></a>CA1715. Идентификаторы должны иметь правильные префиксы
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю документацию по Visual Studio см. в разделе [CA1715: идентификаторы должны иметь правильный префикс](/visualstudio/code-quality/ca1715-identifiers-should-have-correct-prefix).

|Элемент|Значение|
|-|-|
|TypeName|IdentifiersShouldHaveCorrectPrefix|
|CheckId|CA1715|
|Категория|Microsoft. Naming|
|Критическое изменение|Критическое — при срабатывании интерфейсов.<br /><br /> Не критическое — при возникновении параметров универсального типа.|

## <a name="cause"></a>Причина
 Имя интерфейса, видимого извне, не начинается с прописной буквы I.

 -или-

 Имя параметра универсального типа для видимого извне типа или метода не начинается с прописной буквы 'T '.

## <a name="rule-description"></a>Описание правила
 По соглашению имена некоторых программных элементов начинаются с определенного префикса.

 Имена интерфейсов должны начинаться с прописной буквы "I", за которой следует другая прописная буква. Это правило сообщает о нарушениях имен интерфейсов, таких как "Минтерфаце" и "Исолатединтерфаце".

 Имена параметров универсального типа должны начинаться с прописной буквы «'T», а при необходимости может следовать еще одна прописная буква. Это правило сообщает о нарушениях имен параметров универсального типа, таких как "V" и "Type".

 Соглашения об именовании обеспечивают общий вид библиотек, предназначенных для среды CLR. Это сокращает кривую обучения, необходимую для новых библиотек программного обеспечения, и повышает уверенность пользователей в том, что библиотека была разработана кем-то, кто имеет опыт разработки управляемого кода.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Переименуйте идентификатор таким образом, чтобы он был правильно исправлен.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
 **В следующем примере показан неверно именованный интерфейс.**

 [!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix/cpp/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix.cpp#1)]
 [!code-csharp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix/cs/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix.cs#1)]
 [!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix/vb/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix.vb#1)]

## <a name="example"></a>Пример
 **Следующий пример устраняет предыдущее нарушение, добавляя к интерфейсу префикс "I".**

 [!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2/cpp/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2.cpp#1)]
 [!code-csharp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2/cs/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2.cs#1)]
 [!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2/vb/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2.vb#1)]

## <a name="example"></a>Пример
 **В следующем примере показан неправильно именованный параметр универсального типа.**

 [!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3/cpp/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3.cpp#1)]
 [!code-csharp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3/cs/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3.cs#1)]
 [!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3/vb/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3.vb#1)]

## <a name="example"></a>Пример
 **Следующий пример устраняет предыдущее нарушение путем префикса параметра универсального типа с помощью 'T '.**

 [!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4/cpp/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4.cpp#1)]
 [!code-csharp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4/cs/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4.cs#1)]
 [!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4/vb/FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4.vb#1)]

## <a name="related-rules"></a>Связанные правила
 [CA1722. Идентификаторы не должны иметь неправильные префиксы](../code-quality/ca1722-identifiers-should-not-have-incorrect-prefix.md)
