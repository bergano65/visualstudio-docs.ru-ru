---
title: CA1301. Избегайте повторяющихся акселераторов
ms.date: 11/04/2016
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
ms.openlocfilehash: 16cd44f00db13027d737b6a6b496877075ac6fa9
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/09/2019
ms.locfileid: "68922264"
---
# <a name="ca1301-avoid-duplicate-accelerators"></a>CA1301. Избегайте повторяющихся акселераторов

|||
|-|-|
|TypeName|AvoidDuplicateAccelerators|
|CheckId|CA1301|
|Категория|Microsoft. Globalization|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
Тип расширяет <xref:System.Windows.Forms.Control?displayProperty=fullName> и содержит два или более элементов управления верхнего уровня, имеющих одинаковые ключи доступа, которые хранятся в файле ресурсов.

## <a name="rule-description"></a>Описание правила

Клавиша доступа, также называемая ускорителем, обеспечивает клавиатурный доступ к элементу управления с помощью клавиши **ALT** . Если несколько элементов управления имеют одинаковый ключ доступа, поведение ключа доступа четко не определено. Возможно, пользователь не сможет получить доступ к предполагаемому элементу управления с помощью ключа доступа, а элемент управления, отличный от предполагаемого, может быть включен.

Текущая реализация этого правила не учитывает пункты меню. Однако пункты меню в одном подменю не должны иметь одинаковые ключи доступа.

## <a name="how-to-fix-violations"></a>Устранение нарушений
Чтобы устранить нарушение этого правила, Определите уникальные ключи доступа для всех элементов управления.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения
Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
В следующем примере показана минимальная форма, содержащая два элемента управления с одинаковыми ключами доступа. Ключи хранятся в файле ресурсов, который не отображается. Однако их значения отображаются в `checkBox.Text` строках с комментариями. Поведение повторяющихся сочетаний клавиш можно проверить, заменив `checkBox.Text` строки своими аналогами с комментариями. Однако в этом случае предупреждение не будет создано в примере.

[!code-csharp[FxCop.Globalization.AvoidDuplicateAccels#1](../code-quality/codesnippet/CSharp/ca1301-avoid-duplicate-accelerators_1.cs)]

## <a name="see-also"></a>См. также

- <xref:System.Resources.ResourceManager?displayProperty=fullName>
- [Ресурсы в приложениях для настольных систем](/dotnet/framework/resources/index)