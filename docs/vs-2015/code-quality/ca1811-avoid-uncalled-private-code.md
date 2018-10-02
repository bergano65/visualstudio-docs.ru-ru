---
title: 'CA1811: Не используйте Невызываемый закрытый код | Документация Майкрософт'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- AvoidUncalledPrivateCode
- CA1811
helpviewer_keywords:
- CA1811
- AvoidUncalledPrivateCode
ms.assetid: aadbba74-7821-475f-8980-34d17c0a0a8b
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 2f08d3fe31d6a314de9bc64441add64246f8e256
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2018
ms.locfileid: "47591993"
---
# <a name="ca1811-avoid-uncalled-private-code"></a>CA1811: не используйте невызываемый закрытый код
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [CA1811: не используйте Невызываемый закрытый код](https://docs.microsoft.com/visualstudio/code-quality/ca1811-avoid-uncalled-private-code).

|||
|-|-|
|TypeName|AvoidUncalledPrivateCode|
|CheckId|CA1811|
|Категория|Microsoft.Performance|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Член закрытым или внутренним (на уровне сборки) не поддерживает вызывающих объектов в сборке, не вызывается средой CLR и не вызывается делегат. Это правило не проверяются следующие члены:

-   Явные члены интерфейса.

-   Статические конструкторы.

-   Конструкторы сериализации.

-   Методы, помеченные как <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> или <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName>.

-   Члены, которые являются переопределениями.

## <a name="rule-description"></a>Описание правила
 Это правило можно отчетов ложных положительных результатов, в случае точки входа, не распознаются в настоящее время логике правила. Кроме того компилятор может выдать noncallable кода в сборку.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, удалите noncallable код или добавьте код, который ее вызывает.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Его можно безопасно подавить предупреждение из этого правила.

## <a name="related-rules"></a>Связанные правила
 [CA1812: не создавайте внутренние классы без экземпляров](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

 [CA1801: проверьте неиспользуемые параметры](../code-quality/ca1801-review-unused-parameters.md)

 [CA1804: удалите неиспользуемые локальные переменные](../code-quality/ca1804-remove-unused-locals.md)



