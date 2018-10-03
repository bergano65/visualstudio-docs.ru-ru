---
title: 'CA2118: Обзор использования SuppressUnmanagedCodeSecurityAttribute | Документация Майкрософт'
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
- CA2118
- ReviewSuppressUnmanagedCodeSecurityUsage
helpviewer_keywords:
- ReviewSuppressUnmanagedCodeSecurityUsage
- CA2118
ms.assetid: 4cb8d2fc-4e44-4dc3-9b74-7f5838827d41
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: eb88a188c24e65bef6686b4a157c92fa63c5875f
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2018
ms.locfileid: "47591738"
---
# <a name="ca2118-review-suppressunmanagedcodesecurityattribute-usage"></a>CA2118: обзор использования SuppressUnmanagedCodeSecurityAttribute
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [CA2118: обзор использования SuppressUnmanagedCodeSecurityAttribute](https://docs.microsoft.com/visualstudio/code-quality/ca2118-review-suppressunmanagedcodesecurityattribute-usage).

|||
|-|-|
|TypeName|ReviewSuppressUnmanagedCodeSecurityUsage|
|CheckId|CA2118|
|Категория|Microsoft.Security|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Открытый или защищенный тип или член <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> атрибута.

## <a name="rule-description"></a>Описание правила
 <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> изменяет поведение системы безопасности по умолчанию для элементов, выполняющих неуправляемый код с помощью COM-взаимодействия или платформы вызова. Как правило, система открывает [данные и моделирование](http://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6) на разрешение неуправляемого кода. Это требование происходит во время выполнения для каждого вызова члена, а также проверяет каждый источник вызова в стеке вызовов для разрешения. Когда атрибут присутствует, система создает [требования связывания](http://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) для разрешения: разрешения непосредственно вызывающего метода проверяются в том случае, если вызывающий является JIT-компиляции.

 Этот атрибут служит в основном для повышения производительности; однако, прирост производительности сопряжен со значительными рисками безопасности. Если атрибут помещается на открытые члены, которые вызова собственных методов, вызывающих в стеке вызовов (кроме непосредственного вызывающего объекта) не требуется разрешение неуправляемого кода на исполнение неуправляемого кода. В зависимости от действий открытого члена и обрабатывать входные данные он может разрешить ненадежных вызывающих объектов для доступа к функциям, как правило, недоступны надежному коду.

 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] Зависит от проверки безопасности, чтобы предотвратить вызывающим объектам прямой доступ к диапазону адресов текущего процесса. Так как этот атрибут обходит обычную безопасность, код может представлять серьезную угрозу, если он может использоваться для чтения или записи памяти процесса. Обратите внимание на то, что риск не ограничивается методы, которые намеренно предоставляют доступ к памяти процесса; также присутствует в любом сценарии, где вредоносный код может получить доступ любыми средствами, например, предоставляя неожиданные, имеет неправильный формат или недопустимые входные данные.

 Политики безопасности по умолчанию не предоставляет разрешение неуправляемого кода к сборке, если он выполняется с локального компьютера, либо членом одной из следующих групп:

-   Моя группа кода зоны компьютера

-   Группа кода Microsoft строгого имени

-   Группа кода ECMA строгого имени

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Внимательно просмотрите код и убедиться, что этот атрибут является абсолютно необходимым. Если вы не знакомы с безопасности управляемого кода, или не понимаете последствия для системы безопасности с помощью этого атрибута, удалите его из кода. Если атрибут является обязательным, необходимо убедиться, что вызывающие объекты не может использовать код намеренно. Если код не имеет разрешения на выполнение неуправляемого кода, этот атрибут не влияет и должны быть удалены.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Чтобы безопасно подавить предупреждение из этого правила, необходимо убедиться, что ваш код не предоставляет вызывающему объекту доступ к встроенным операциям или ресурсам, которые могут использоваться в злонамеренных целях.

## <a name="example"></a>Пример
 Следующий пример приводит к нарушению правила.

 [!code-csharp[FxCop.Security.TypesDoNotSuppress#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TypesDoNotSuppress/cs/FxCop.Security.TypesDoNotSuppress.cs#1)]

## <a name="example"></a>Пример
 В следующем примере `DoWork` метод предоставляет доступ к общедоступным к методу вызова платформы `FormatHardDisk`.

 [!code-csharp[FxCop.Security.PInvokeAndSuppress#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.PInvokeAndSuppress/cs/FxCop.Security.PInvokeAndSuppress.cs#1)]

## <a name="example"></a>Пример
 В следующем примере, открытый метод `DoDangerousThing` вызывает нарушение. Чтобы устранить это нарушение `DoDangerousThing` следует делать закрытым, и к нему доступ должен предоставляться через открытый метод, защищенный требованием безопасности, как показано в `DoWork` метод.

 [!code-csharp[FxCop.Security.TypeInvokeAndSuppress#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TypeInvokeAndSuppress/cs/FxCop.Security.TypeInvokeAndSuppress.cs#1)]

## <a name="see-also"></a>См. также
 <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> [Правила написания безопасного кода](http://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) [Оптимизация безопасности](http://msdn.microsoft.com/en-us/cf255069-d85d-4de3-914a-e4625215a7c0) [данные и моделирование](http://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6) [требования связывания](http://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d)



