---
title: 'CA1716: идентификаторы не должны совпадать с ключевыми словами'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- IdentifiersShouldNotMatchKeywords
- CA1716
helpviewer_keywords:
- IdentifiersShouldNotMatchKeywords
- CA1716
ms.assetid: 900cc8a1-1089-4069-a4ce-10b109ac4fab
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2b5ee844da2c04a1dd6eac6a7ca458957dd22a71
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/13/2018
ms.locfileid: "45550613"
---
# <a name="ca1716-identifiers-should-not-match-keywords"></a>CA1716: идентификаторы не должны совпадать с ключевыми словами
|||
|-|-|
|TypeName|IdentifiersShouldNotMatchKeywords|
|CheckId|CA1716|
|Категория|Microsoft.Naming|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Имя пространства имен, тип или член виртуального члена или интерфейс совпадает с зарезервированным ключевым словом в языке программирования.

## <a name="rule-description"></a>Описание правила
 Идентификаторы пространств имен, типов и виртуальные и члены интерфейса не должны совпадать с ключевыми словами, которые определены в языках, поддерживаемых среда CLR. В зависимости от используемого языка и ключевого слова ошибки компилятора и неоднозначностей могут затруднять библиотеку для использования.

 Это правило проверяет ключевые слова на следующих языках:

- Visual Basic

- C#

- C++/CLI

 Сравнение без учета регистра, используемый для [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] ключевые слова и сравнение с учетом регистра используется для других языков.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Выберите имя, которое не отображается в списке ключевых слов.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Можно подавить предупреждение из этого правила, если вы уверены, что идентификатор не будет запутывания пользователей API-интерфейса, и что библиотеку можно использовать в некоторых языках [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].