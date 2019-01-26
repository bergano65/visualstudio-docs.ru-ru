---
title: CA1301. Избегайте повторяющихся акселераторов
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA1301
- AvoidDuplicateAccelerators
helpviewer_keywords:
- CA1301
- AvoidDuplicateAccelerators
ms.assetid: 20570a00-864b-459c-a1fa-a6e9db5f1001
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 04a6c105f2452392af5c7246508232df18385b5e
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "55018388"
---
# <a name="ca1301-avoid-duplicate-accelerators"></a>CA1301. Избегайте повторяющихся акселераторов

|||
|-|-|
|TypeName|AvoidDuplicateAccelerators|
|CheckId|CA1301|
|Категория|Microsoft.Globalization|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Тип расширяет <xref:System.Windows.Forms.Control?displayProperty=fullName> и содержит два или несколько элементов управления верхнего уровня, с одинаковыми клавишами доступа, которые хранятся в файле ресурсов.

## <a name="rule-description"></a>Описание правила

Ключ доступа, также известный как ускоритель, обеспечивает клавиатурный доступ к элементу управления с помощью **Alt** ключ. Если несколько элементов управления имеют один и тот же ключ доступа, поведение клавиши доступа не является правильно определенным. Пользователь не сможет получить доступ к желаемому элементу управления с помощью ключа доступа, и элемент управления, отличном от того, который предназначен может включаться.

Текущая реализация это правило не учитывает пунктов меню. Тем не менее элементы меню, в том же подменю не должно быть одинаковыми клавишами доступа.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение данного правила, определите уникальные клавиши доступа для всех элементов управления.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
 Следующий пример показывает простейшая форма содержит два элемента управления с одинаковыми клавишами доступа. Ключи хранятся в файле ресурсов, оно не отображается. Тем не менее, их значения отобразятся в закомментированного out `checkBox.Text` строки. Поведение повторяющиеся ускорители могут проверяться путем обмена `checkBox.Text` строки с их аналоги из комментариев. Однако в нашем примере не выдаст предупреждение из правила.

 [!code-csharp[FxCop.Globalization.AvoidDuplicateAccels#1](../code-quality/codesnippet/CSharp/ca1301-avoid-duplicate-accelerators_1.cs)]

## <a name="see-also"></a>См. также

- <xref:System.Resources.ResourceManager?displayProperty=fullName>
- [Ресурсы в приложениях для настольных систем](/dotnet/framework/resources/index)