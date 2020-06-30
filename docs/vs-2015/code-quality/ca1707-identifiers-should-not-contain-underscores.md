---
title: 'CA1707: идентификаторы не должны содержать знаки подчеркивания | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- IdentifiersShouldNotContainUnderscores
- CA1707
helpviewer_keywords:
- CA1707
- IdentifiersShouldNotContainUnderscores
ms.assetid: 5fb539ef-c304-4323-90c0-b14386da9774
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: fe6b90ef971bd00392381f47860d85f34e10dc26
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/30/2020
ms.locfileid: "85544031"
---
# <a name="ca1707-identifiers-should-not-contain-underscores"></a>CA1707. Идентификаторы не должны содержать символы подчеркивания
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю документацию по Visual Studio см. в разделе [CA1707: идентификаторы не должны содержать символы подчеркивания](/visualstudio/code-quality/ca1707-identifiers-should-not-contain-underscores).

|Item|Значение|
|-|-|
|TypeName|IdentifiersShouldNotContainUnderscores|
|CheckId|CA1707|
|Категория|Microsoft. Naming|
|Критическое изменение|Критическое — при возникновении сборок<br /><br /> Не критическое — при возникновении параметров типа|

## <a name="cause"></a>Причина
 Имя идентификатора содержит символ подчеркивания (_).

## <a name="rule-description"></a>Описание правила
 В соответствии с соглашением имена идентификаторов не могут содержать знак подчеркивания (_). Правило проверяет пространства имен, типы, члены и параметры.

 Соглашения об именовании обеспечивают общий вид библиотек, предназначенных для среды CLR. Это сокращает кривую обучения, необходимую для новых библиотек программного обеспечения, и повышает уверенность пользователей в том, что библиотека была разработана кем-то, кто имеет опыт разработки управляемого кода.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Удалите все символы подчеркивания из имени.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="related-rules"></a>Связанные правила
 [CA1709. Идентификаторы должны иметь правильное сочетание прописных и строчных букв](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

 [CA1708. Идентификаторы должны отличаться не только прописными и строчными буквами](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)
