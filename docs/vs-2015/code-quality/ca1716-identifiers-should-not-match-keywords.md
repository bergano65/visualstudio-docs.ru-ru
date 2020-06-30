---
title: 'CA1716: идентификаторы не должны совпадать с ключевыми словами | Документация Майкрософт'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 67a3588a857a0eea7d338217f975ed593dfdad52
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/30/2020
ms.locfileid: "85543706"
---
# <a name="ca1716-identifiers-should-not-match-keywords"></a>CA1716. Идентификаторы не должны совпадать с ключевыми словами
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|Значение|
|-|-|
|TypeName|IdentifiersShouldNotMatchKeywords|
|CheckId|CA1716|
|Категория|Microsoft. Naming|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Имя пространства имен, типа или члена виритуал или интерфейса соответствует зарезервированному ключевому слову в языке программирования.

## <a name="rule-description"></a>Описание правила
 Идентификаторы пространств имен, типов и виртуальных элементов и членов интерфейса не должны совпадать с ключевыми словами, которые определены в языках, предназначенных для среды CLR. В зависимости от используемого языка и ключевого слова ошибки и неоднозначности компилятора могут усложнить использование библиотеки.

 Это правило проверяет ключевые слова на следующих языках:

- Visual Basic

- C#

- C++/CLI

  Сравнение без учета регистра используется для [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ключевых слов, а для других языков используется сравнение с учетом регистра.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Выберите имя, которое не отображается в списке ключевых слов.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Предупреждение из этого правила можно отключить, если вы убедились, что идентификатор не будет путать пользователей API и что библиотека может использоваться на всех доступных языках в [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] .
