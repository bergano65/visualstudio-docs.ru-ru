---
title: CA2114. Безопасность метода должна быть надмножеством типа
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- MethodSecurityShouldBeASupersetOfType
- CA2114
helpviewer_keywords:
- CA2114
- MethodSecurityShouldBeASupersetOfType
ms.assetid: 663f7aa4-8be5-4bd5-be92-4e9444f07077
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ec58e8060447a02309a0a902bcf63eea8805ca8c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53881796"
---
# <a name="ca2114-method-security-should-be-a-superset-of-type"></a>CA2114. Безопасность метода должна быть надмножеством типа

|||
|-|-|
|TypeName|MethodSecurityShouldBeASupersetOfType|
|CheckId|CA2114|
|Категория|Microsoft.Security|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Тип имеет декларативную безопасность и один из его методов имеет декларативную безопасность для одного действия безопасности и действие по обеспечению безопасности не [требования связывания](/dotnet/framework/misc/link-demands), и разрешения, проверяемые типа не являются подмножеством разрешения Проверка с помощью метода.

## <a name="rule-description"></a>Описание правила
 Метод не должен иметь тип уровня и метод декларативной безопасности для одного действия. Эти две проверки не объединяются; применяется только по требованию уровне метода. Например, если тип запрашивает разрешение `X`, и один из его методов разрешение `Y`, код не имеет разрешения `X` для выполнения метода.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Просмотрите код, чтобы убедиться в том, что оба действия являются обязательными. Если оба действия необходимы, убедитесь, что действие уровне метода включает безопасность, определенную на уровне типа. Например, если тип запрашивает разрешение `X`, и его метод также должен запросить разрешение `Y`, метод должен явным образом запрашивать `X` и `Y`.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Его можно безопасно подавить предупреждение из этого правила, если метод не требует безопасности, заданную типом. Тем не менее это не обычный сценарий и может указывать на необходимость проверки тщательного планирования.

## <a name="example-1"></a>Пример 1

В следующем примере разрешения среды для демонстрации опасности нарушения этого правила. В этом примере код приложения создает экземпляр безопасного типа перед запрет разрешений на тип. В обычном случае приложению потребуется еще один способ получения экземпляра объекта.

В следующем примере библиотека запрашивает разрешение для типа записи и разрешения на чтение для метода.

[!code-csharp[FxCop.Security.MethodLevelSecurity#1](../code-quality/codesnippet/CSharp/ca2114-method-security-should-be-a-superset-of-type_1.cs)]

## <a name="example-2"></a>Пример 2

Следующий код приложения демонстрируется уязвимость библиотеки путем вызова метода, несмотря на то, что он не соответствует требованиям безопасности на уровне типа.

[!code-csharp[FxCop.Security.TestMethodLevelSecurity#1](../code-quality/codesnippet/CSharp/ca2114-method-security-should-be-a-superset-of-type_2.cs)]

В этом примере выводятся следующие данные:

```txt
[All permissions] Personal information: 6/16/1964 12:00:00 AM
[No write permission (demanded by type)] Personal information: 6/16/1964 12:00:00 AM
[No read permission (demanded by method)] Could not access personal information: Request failed.
```

## <a name="see-also"></a>См. также

- [Правила написания безопасного кода](/dotnet/standard/security/secure-coding-guidelines)
- [Требования связывания](/dotnet/framework/misc/link-demands)
- [Данные и моделирование](/dotnet/framework/data/index)