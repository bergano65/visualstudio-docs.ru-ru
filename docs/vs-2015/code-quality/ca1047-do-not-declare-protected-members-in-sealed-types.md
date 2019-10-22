---
title: 'CA1047: не объявляйте защищенные члены в запечатанных типах | Документация Майкрософт'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: ebc6732e559b70e753a44b14cf45b7de9fc150d4
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668180"
---
# <a name="ca1047-do-not-declare-protected-members-in-sealed-types"></a>CA1047: не объявляйте защищенные элементы в запечатанных типах
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotDeclareProtectedMembersInSealedTypes|
|CheckId|CA1047|
|Категория|Microsoft. Design|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Открытый тип — `sealed` (`NotInheritable` в Visual Basic) и объявляет защищенный член или защищенный вложенный тип. Это правило не сообщает о нарушениях для методов <xref:System.Object.Finalize%2A>, которые должны следовать этому шаблону.

## <a name="rule-description"></a>Описание правила
 Типы объявляют защищенный члены таким образом, чтобы наследующие типы могли получить доступ к члену или переопределить его. По определению нельзя наследовать от запечатанного типа. Это означает, что нельзя вызывать защищенные методы в запечатанных типах.

 C# Компилятор выдает предупреждение для этой ошибки.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, измените уровень доступа элемента на частный или сделайте тип наследуемым.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует. Если оставить тип в его текущем состоянии, это может вызвать проблемы с обслуживанием и не дает никаких преимуществ.

## <a name="example"></a>Пример
 В следующем примере показан тип, нарушающий это правило.

 [!code-csharp[FxCop.Design.SealedNoProtected#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.SealedNoProtected/cs/FxCop.Design.SealedNoProtected.cs#1)]
 [!code-vb[FxCop.Design.SealedNoProtected#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.SealedNoProtected/vb/FxCop.Design.SealedNoProtected.vb#1)]
