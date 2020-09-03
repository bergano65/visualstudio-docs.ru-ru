---
title: 'CA2136: элементы не должны иметь конфликтующие аннотации прозрачности | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2127
- SecurityTransparentAssembliesShouldNotContainSecurityCriticalCode
- CA2136
helpviewer_keywords:
- SecurityTransparentAssembliesShouldNotContainSecurityCriticalCode
- CA2127
ms.assetid: ff5a1d18-7c52-4da5-8990-60be83a8ea81
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: a3a17a0db7dd4ad1c57d23104a313a78cd1289ed
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547697"
---
# <a name="ca2136-members-should-not-have-conflicting-transparency-annotations"></a>CA2136. Члены не должны иметь противоречащие заметки прозрачности
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Элемент|Значение|
|-|-|
|TypeName|транспаренцианнотатионсшаулднотконфликт|
|CheckId|CA2136|
|Категория|Microsoft.Security|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Это правило срабатывает, если член типа помечен <xref:System.Security> атрибутом безопасности с разной прозрачностью, чем атрибут безопасности контейнера элемента.

## <a name="rule-description"></a>Описание правила
 Атрибуты прозрачности применяются из элементов кода большей области к элементам меньшей области. Атрибуты прозрачности элементов кода с большей областью имеют приоритет по сравнению с атрибутами прозрачности элементов кода, которые содержатся в первом элементе. Например, класс, помеченный <xref:System.Security.SecurityCriticalAttribute> атрибутом, не может содержать метод, помеченный <xref:System.Security.SecuritySafeCriticalAttribute> атрибутом.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить это нарушение, удалите атрибут безопасности из элемента Code с более ранней областью или измените его атрибут так, чтобы он совпадал с содержащим элементом кода.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Не отключайте вывод предупреждений из этого правила.

## <a name="example"></a>Пример
 В следующем примере метод помечен <xref:System.Security.SecuritySafeCriticalAttribute> атрибутом и является членом класса, помеченного <xref:System.Security.SecurityCriticalAttribute> атрибутом. Безопасный атрибут безопасности следует удалить.

 [!code-csharp[FxCop.Security.CA2136.TransparencyAnnotationsShouldNotConflict#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2136.transparencyannotationsshouldnotconflict/cs/ca2136 - transparencyannotationsshouldnotconflict.cs#1)]
