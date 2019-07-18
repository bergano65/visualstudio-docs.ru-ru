---
title: CA2130. Константы критической безопасности должны быть прозрачными | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2130
ms.assetid: 344c7f7b-9130-4675-ae7f-9fa260cc9789
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 26d3b5389bb080dee6e550c4bc0e6c035fd15db2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68154329"
---
# <a name="ca2130-security-critical-constants-should-be-transparent"></a>CA2130. Важные константы безопасности должны быть прозрачными
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ConstantsShouldBeTransparent|
|CheckId|CA2130|
|Категория|Microsoft.Security|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Константного поля или член перечисления помечается <xref:System.Security.SecurityCriticalAttribute>.

## <a name="rule-description"></a>Описание правила
 Принудительная прозрачность не применяется для постоянных значений, чтобы во время выполнения не требовалась подстановка значений. Константные поля должны быть прозрачными для системы безопасности, чтобы анализаторы кода не предполагали, что прозрачный для системы безопасности код не может получить доступ к константе.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, удалите атрибут SecurityCritical из поля или значения.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
 В следующих примерах значение перечисления `EnumWithCriticalValues.CriticalEnumValue` и константы `CriticalConstant` выдавал подобное предупреждение. Чтобы устранить проблемы, удалите [`SecurityCritical`] атрибут, чтобы сделать их безопасности прозрачным.

 [!code-csharp[FxCop.Security.CA2130.ConstantsShouldBeTransparent#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2130.constantsshouldbetransparent/cs/ca2130 - constantsshouldbetransparent.cs#1)]
