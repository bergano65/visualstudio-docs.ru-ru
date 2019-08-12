---
title: CA1415. Правильно объявляйте методы P/Invoke
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1415
- DeclarePInvokesCorrectly
helpviewer_keywords:
- CA1415
- DeclarePInvokesCorrectly
ms.assetid: 42a90796-0264-4460-bf97-2fb4a093dfdc
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c5cc12d5d0a62f8d2530f13fcf860aba4e118ca4
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/09/2019
ms.locfileid: "68921854"
---
# <a name="ca1415-declare-pinvokes-correctly"></a>CA1415. Правильно объявляйте методы P/Invoke

|||
|-|-|
|TypeName|DeclarePInvokesCorrectly|
|CheckId|CA1415|
|Категория|Microsoft. взаимодействие|
|Критическое изменение|Не критическое — если P/Invoke, объявляющий параметр, не может просматриваться за пределами сборки. Критическое — если P/Invoke, объявляющий параметр, может отображаться за пределами сборки.|

## <a name="cause"></a>Причина
Неверно объявлен метод вызова неуправляемого кода.

## <a name="rule-description"></a>Описание правила
Метод вызова платформы обращается к неуправляемому коду и определяется с помощью `Declare` ключевого слова в [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] или. <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> В настоящее время это правило выполняет поиск объявлений методов вызова неуправляемого кода, предназначенных для функций Win32, которые имеют указатель на параметр структуры OVERLAPPED, а соответствующий управляемый параметр не <xref:System.Threading.NativeOverlapped?displayProperty=fullName> является указателем на структуру.

## <a name="how-to-fix-violations"></a>Устранение нарушений
Чтобы устранить нарушение этого правила, правильно объявите метод вызова неуправляемого кода.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения
Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
В следующем примере показаны методы вызова неуправляемого кода, которые нарушают правило и удовлетворяют правилу.

[!code-csharp[FxCop.Interoperability.DeclarePInvokes#1](../code-quality/codesnippet/CSharp/ca1415-declare-p-invokes-correctly_1.cs)]

## <a name="see-also"></a>См. также
[Взаимодействие с неуправляемым кодом](/dotnet/framework/interop/index)