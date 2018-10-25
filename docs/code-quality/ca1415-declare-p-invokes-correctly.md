---
title: 'CA1415: правильно объявляйте методы P-Invoke'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f95c3e68190acbd53c4b75ceb81abf2885d15bce
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49922631"
---
# <a name="ca1415-declare-pinvokes-correctly"></a>CA1415: правильно объявляйте методы P/Invoke

|||
|-|-|
|TypeName|DeclarePInvokesCorrectly|
|CheckId|CA1415|
|Категория|Microsoft.Interoperability|
|Критическое изменение|Non критическое, если P/Invoke, который объявляет, что параметры, которые не видны за пределами сборки. Критическое, если P/Invoke, который объявляет, что параметры видно за пределами сборки.|

## <a name="cause"></a>Причина
 Метод вызова неуправляемого объявлен.

## <a name="rule-description"></a>Описание правила
 Вызов метода доступа неуправляемого кода платформы и определяется с помощью `Declare` ключевое слово в [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] или <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>. В настоящее время это правило ищет объявления методов, предназначенных для функций Win32, имеющих указатель на параметр структуры OVERLAPPED при вызове неуправляемого кода и соответствующий управляемый параметр не является указателем на <xref:System.Threading.NativeOverlapped?displayProperty=fullName> структуры.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, правильно объявите платформы вызова метода.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
 В следующем примере показан методы, которые нарушают правила и удовлетворяют правилу при вызове неуправляемого кода.

 [!code-csharp[FxCop.Interoperability.DeclarePInvokes#1](../code-quality/codesnippet/CSharp/ca1415-declare-p-invokes-correctly_1.cs)]

## <a name="see-also"></a>См. также
 [Взаимодействие с неуправляемым кодом](/dotnet/framework/interop/index)