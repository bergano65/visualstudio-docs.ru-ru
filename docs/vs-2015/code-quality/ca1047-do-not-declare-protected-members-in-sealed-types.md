---
title: CA1047. Не объявляйте защищенные члены в запечатанных типах | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotDeclareProtectedMembersInSealedTypes
- CA1047
helpviewer_keywords:
- CA1047
- DoNotDeclareProtectedMembersInSealedTypes
ms.assetid: 829033b5-a9d8-4f26-a719-45494c9dd035
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 6d949a756dfe3ff22ba43d172078d35bfe706e14
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62536108"
---
# <a name="ca1047-do-not-declare-protected-members-in-sealed-types"></a>CA1047. Не объявляйте защищенные члены в запечатанных типах
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotDeclareProtectedMembersInSealedTypes|
|CheckId|CA1047|
|Категория|Microsoft.Design|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Открытый тип является `sealed` (`NotInheritable` в Visual basic) и объявляют защищенный член или защищенные вложенного типа. Это правило не касается нарушений <xref:System.Object.Finalize%2A> методы, которые необходимо следовать этому шаблону.

## <a name="rule-description"></a>Описание правила
 Типы объявляют защищенный члены таким образом, чтобы наследующие типы могли получить доступ к члену или переопределить его. По определению не может наследовать от запечатанного типа, что означает, что вызов защищенных методов для запечатанных типов невозможен.

 Компилятор C# выдает предупреждение для этой ошибки.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, изменить уровень доступа члена на закрытый или сделайте тип наследуемым.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует. Тип в ее текущем состоянии может привести к проблемам обслуживания и не предоставляет никаких преимуществ.

## <a name="example"></a>Пример
 В следующем примере тип, который нарушает это правило.

 [!code-csharp[FxCop.Design.SealedNoProtected#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.SealedNoProtected/cs/FxCop.Design.SealedNoProtected.cs#1)]
 [!code-vb[FxCop.Design.SealedNoProtected#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.SealedNoProtected/vb/FxCop.Design.SealedNoProtected.vb#1)]
