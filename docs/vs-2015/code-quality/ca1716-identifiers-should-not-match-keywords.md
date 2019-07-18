---
title: CA1716. Идентификаторы не должны совпадать с ключевыми словами | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- IdentifiersShouldNotMatchKeywords
- CA1716
helpviewer_keywords:
- IdentifiersShouldNotMatchKeywords
- CA1716
ms.assetid: 900cc8a1-1089-4069-a4ce-10b109ac4fab
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 35a97e62e17895cb700a1420c7851878f329112a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68189113"
---
# <a name="ca1716-identifiers-should-not-match-keywords"></a>CA1716. Идентификаторы не должны совпадать с ключевыми словами
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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

  Сравнение без учета регистра, используемый для [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ключевые слова и сравнение с учетом регистра используется для других языков.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Выберите имя, которое не отображается в списке ключевых слов.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Можно подавить предупреждение из этого правила, если вы уверены, что идентификатор не будет запутывания пользователей API-интерфейса, и что библиотеку можно использовать в некоторых языках [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].
