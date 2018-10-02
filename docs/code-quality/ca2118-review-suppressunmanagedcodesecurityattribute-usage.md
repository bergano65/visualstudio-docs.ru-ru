---
title: 'CA2118: обзор использования SuppressUnmanagedCodeSecurityAttribute'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2118
- ReviewSuppressUnmanagedCodeSecurityUsage
helpviewer_keywords:
- ReviewSuppressUnmanagedCodeSecurityUsage
- CA2118
ms.assetid: 4cb8d2fc-4e44-4dc3-9b74-7f5838827d41
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 900abe516ebd07cf5a8849f269f915623500731e
ms.sourcegitcommit: ad5fb20f18b23eb8bd2568717f61edc6b7eee5e7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47859709"
---
# <a name="ca2118-review-suppressunmanagedcodesecurityattribute-usage"></a>CA2118: обзор использования SuppressUnmanagedCodeSecurityAttribute

|||
|-|-|
|TypeName|ReviewSuppressUnmanagedCodeSecurityUsage|
|CheckId|CA2118|
|Категория|Microsoft.Security|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Открытый или защищенный тип или член <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> атрибута.

## <a name="rule-description"></a>Описание правила
 <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> изменяет поведение системы безопасности по умолчанию для элементов, выполняющих неуправляемый код с помощью COM-взаимодействия или платформы вызова. Как правило, система открывает [данные и моделирование](/dotnet/framework/data/index) на разрешение неуправляемого кода. Это требование происходит во время выполнения для каждого вызова члена, а также проверяет каждый источник вызова в стеке вызовов для разрешения. Когда атрибут присутствует, система создает [требования связывания](/dotnet/framework/misc/link-demands) для разрешения: разрешения непосредственно вызывающего метода проверяются в том случае, если вызывающий является JIT-компиляции.

 Этот атрибут служит в основном для повышения производительности; однако, прирост производительности сопряжен со значительными рисками безопасности. Если атрибут помещается на открытые члены, которые вызова собственных методов, вызывающих в стеке вызовов (кроме непосредственного вызывающего объекта) не требуется разрешение неуправляемого кода на исполнение неуправляемого кода. В зависимости от действий открытого члена и обрабатывать входные данные он может разрешить ненадежных вызывающих объектов для доступа к функциям, как правило, недоступны надежному коду.

 .NET Framework зависит от проверки безопасности, чтобы предотвратить вызывающим объектам прямой доступ к диапазону адресов текущего процесса. Так как этот атрибут обходит обычную безопасность, код может представлять серьезную угрозу, если он может использоваться для чтения или записи памяти процесса. Обратите внимание на то, что риск не ограничивается методы, которые намеренно предоставляют доступ к памяти процесса; также присутствует в любом сценарии, где вредоносный код может получить доступ любыми средствами, например, предоставляя неожиданные, имеет неправильный формат или недопустимые входные данные.

 Политики безопасности по умолчанию не предоставляет разрешение неуправляемого кода к сборке, если он выполняется с локального компьютера, либо членом одной из следующих групп:

- Моя группа кода зоны компьютера

- Группа кода Microsoft строгого имени

- Группа кода ECMA строгого имени

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Внимательно просмотрите код и убедиться, что этот атрибут является абсолютно необходимым. Если вы не знакомы с безопасности управляемого кода, или не понимаете последствия для системы безопасности с помощью этого атрибута, удалите его из кода. Если атрибут является обязательным, необходимо убедиться, что вызывающие объекты не может использовать код намеренно. Если код не имеет разрешения на выполнение неуправляемого кода, этот атрибут не влияет и должны быть удалены.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Чтобы безопасно подавить предупреждение из этого правила, необходимо убедиться, что ваш код не предоставляет вызывающему объекту доступ к встроенным операциям или ресурсам, которые могут использоваться в злонамеренных целях.

## <a name="example-1"></a>Пример 1
 Следующий пример приводит к нарушению правила.

 [!code-csharp[FxCop.Security.TypesDoNotSuppress#1](../code-quality/codesnippet/CSharp/ca2118-review-suppressunmanagedcodesecurityattribute-usage_1.cs)]

## <a name="example-2"></a>Пример 2
 В следующем примере `DoWork` метод предоставляет доступ к общедоступным к методу вызова платформы `FormatHardDisk`.

 [!code-csharp[FxCop.Security.PInvokeAndSuppress#1](../code-quality/codesnippet/CSharp/ca2118-review-suppressunmanagedcodesecurityattribute-usage_2.cs)]

## <a name="example-3"></a>Пример 3
 В следующем примере, открытый метод `DoDangerousThing` вызывает нарушение. Чтобы устранить это нарушение `DoDangerousThing` следует делать закрытым, и к нему доступ должен предоставляться через открытый метод, защищенный требованием безопасности, как показано в `DoWork` метод.

 [!code-csharp[FxCop.Security.TypeInvokeAndSuppress#1](../code-quality/codesnippet/CSharp/ca2118-review-suppressunmanagedcodesecurityattribute-usage_3.cs)]

## <a name="see-also"></a>См. также

- <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName>
- [Правила написания безопасного кода](/dotnet/standard/security/secure-coding-guidelines)
- [Данные и моделирование](/dotnet/framework/data/index)
- [Требования связывания](/dotnet/framework/misc/link-demands)