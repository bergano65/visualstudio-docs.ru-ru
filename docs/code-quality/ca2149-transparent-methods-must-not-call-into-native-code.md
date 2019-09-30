---
title: CA2149. Прозрачные методы не должны вызывать машинный код
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2149
ms.assetid: 28951bd7-f3db-4871-99aa-bad68d1ead80
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 8e75b12b820b3ff3ac5a26f83148a49ca87c12ad
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2019
ms.locfileid: "71231956"
---
# <a name="ca2149-transparent-methods-must-not-call-into-native-code"></a>CA2149. Прозрачные методы не должны вызывать машинный код

|||
|-|-|
|TypeName|транспарентмесодсмустноткаллнативекоде|
|CheckId|CA2149|
|Категория|Microsoft.Security|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина:
Метод вызывает собственную функцию через заглушку метода, например P/Invoke.

## <a name="rule-description"></a>Описание правила
Это правило срабатывает для любого прозрачного метода, который вызывает непосредственно в машинный код, например с помощью P/Invoke. Нарушение этого правила приводит к <xref:System.MethodAccessException> тому, что в модели прозрачности уровня 2 и полное требование для <xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A> модели прозрачности уровня 1.

## <a name="how-to-fix-violations"></a>Устранение нарушений
Чтобы устранить нарушение этого правила, пометьте метод, который вызывает машинный код с <xref:System.Security.SecurityCriticalAttribute> помощью атрибута или. <xref:System.Security.SecuritySafeCriticalAttribute>

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения
Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
[!code-csharp[FxCop.Security.CA2149.TransparentMethodsMustNotCallNativeCode#1](../code-quality/codesnippet/CSharp/ca2149-transparent-methods-must-not-call-into-native-code_1.cs)]