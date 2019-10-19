---
title: 'CA1415: правильно объявляйте методы P-Invoke | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1415
- DeclarePInvokesCorrectly
helpviewer_keywords:
- CA1415
- DeclarePInvokesCorrectly
ms.assetid: 42a90796-0264-4460-bf97-2fb4a093dfdc
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 922cd713867e1e1017a0f13490a08c0950b2afbf
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652672"
---
# <a name="ca1415-declare-pinvokes-correctly"></a>CA1415: правильно объявляйте методы P/Invoke
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DeclarePInvokesCorrectly|
|CheckId|CA1415|
|Категория|Microsoft. взаимодействие|
|Критическое изменение|Не критическое — если P/Invoke, объявляющий параметр, не может просматриваться за пределами сборки. Критическое — если P/Invoke, объявляющий параметр, может отображаться за пределами сборки.|

## <a name="cause"></a>Причина
 Неверно объявлен метод вызова неуправляемого кода.

## <a name="rule-description"></a>Описание правила
 Метод вызова платформы обращается к неуправляемому коду и определяется с помощью ключевого слова `Declare` в [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] или <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>. В настоящее время это правило выполняет поиск объявлений методов вызова неуправляемого кода, предназначенных для функций Win32, имеющих указатель на параметр структуры OVERLAPPED, и соответствующий управляемый параметр не является указателем на структуру <xref:System.Threading.NativeOverlapped?displayProperty=fullName>.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, правильно объявите метод вызова неуправляемого кода.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
 В следующем примере показаны методы вызова неуправляемого кода, которые нарушают правило и удовлетворяют правилу.

 [!code-csharp[FxCop.Interoperability.DeclarePInvokes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.DeclarePInvokes/cs/FxCop.Interoperability.DeclarePInvokes.cs#1)]

## <a name="see-also"></a>См. также раздел
 [Взаимодействие с неуправляемым кодом](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)
