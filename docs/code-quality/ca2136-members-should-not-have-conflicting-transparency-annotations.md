---
title: "CA2136: Элементы не должны иметь конфликтующие пометки прозрачности | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2127
- SecurityTransparentAssembliesShouldNotContainSecurityCriticalCode
- CA2136
helpviewer_keywords:
- SecurityTransparentAssembliesShouldNotContainSecurityCriticalCode
- CA2127
ms.assetid: ff5a1d18-7c52-4da5-8990-60be83a8ea81
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 350504d6e49351e96aa1c986ddf08893dc490d69
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="ca2136-members-should-not-have-conflicting-transparency-annotations"></a>CA2136: элементы не должны иметь конфликтующие пометки прозрачности
|||  
|-|-|  
|TypeName|TransparencyAnnotationsShouldNotConflict|  
|CheckId|CA2136|  
|Категория|Microsoft.Security|  
|Критическое изменение|Критическое|  
  
## <a name="cause"></a>Причина  
 Это правило срабатывает, когда член типа помечается <xref:System.Security> атрибута безопасности, отличной от прозрачности атрибута безопасности контейнера элемента.  
  
## <a name="rule-description"></a>Описание правила  
 Атрибуты прозрачности применяются из элементов кода большей области к элементам меньшей области. Атрибуты прозрачности элементов кода с большей областью имеют приоритет по сравнению с атрибутами прозрачности элементов кода, которые содержатся в первом элементе. Например, класс, отмеченный атрибутом <xref:System.Security.SecurityCriticalAttribute> атрибута не может содержать метод с атрибутом <xref:System.Security.SecuritySafeCriticalAttribute> атрибута.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Для устранения нарушения данного правила, удалите атрибут безопасности из элемента кода с меньшей областью или измените его атрибут должен совпадать с элемент кода.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Не следует отключать предупреждения из этого правила.  
  
## <a name="example"></a>Пример  
 В следующем примере метод помечен атрибутом <xref:System.Security.SecuritySafeCriticalAttribute> атрибута и является членом класса, помеченного с <xref:System.Security.SecurityCriticalAttribute> атрибута. Безопасный атрибут следует удалить.  
  
 [!code-csharp[FxCop.Security.CA2136.TransparencyAnnotationsShouldNotConflict#1](../code-quality/codesnippet/CSharp/ca2136-members-should-not-have-conflicting-transparency-annotations_1.cs)]