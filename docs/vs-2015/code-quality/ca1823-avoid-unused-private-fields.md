---
title: 'CA1823: Избегайте неиспользуемых закрытых полей | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AvoidUnusedPrivateFields
- CA1823
helpviewer_keywords:
- AvoidUnusedPrivateFields
- CA1823
ms.assetid: 614f94f6-0dc7-430f-8124-cb889a4a720f
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: d7ccfbe863e010b4dcf8a9d1b442c9bcdba6822e
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661127"
---
# <a name="ca1823-avoid-unused-private-fields"></a>CA1823: избегайте наличия неиспользованных закрытых полей
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AvoidUnusedPrivateFields|
|CheckId|CA1823|
|Категория|Microsoft. Performance|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Это правило сообщается, когда закрытое поле в коде существует, но не используется ни одним из путей кода.

## <a name="rule-description"></a>Описание правила
 Обнаружены закрытые поля, доступ к которым, судя по всему, не предоставляется в сборке.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, удалите поле или добавьте код, который его использует.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 В этом правиле можно отключить вывод предупреждений.

## <a name="related-rules"></a>Связанные правила
 [CA1812: не создавайте внутренние классы без экземпляров](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

 [CA1801: проверьте неиспользуемые параметры](../code-quality/ca1801-review-unused-parameters.md)

 [CA1804: удалите неиспользуемые локальные переменные](../code-quality/ca1804-remove-unused-locals.md)

 [CA1811: не используйте невызываемый закрытый код](../code-quality/ca1811-avoid-uncalled-private-code.md)
