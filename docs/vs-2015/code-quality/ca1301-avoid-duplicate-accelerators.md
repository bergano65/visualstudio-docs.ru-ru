---
title: CA1301. Не | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1301
- AvoidDuplicateAccelerators
helpviewer_keywords:
- CA1301
- AvoidDuplicateAccelerators
ms.assetid: 20570a00-864b-459c-a1fa-a6e9db5f1001
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 407397eea761d9d44ffa840d2d632d5b037b8e8b
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58978965"
---
# <a name="ca1301-avoid-duplicate-accelerators"></a>CA1301. Избегайте повторяющихся акселераторов
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AvoidDuplicateAccelerators|
|CheckId|CA1301|
|Категория|Microsoft.Globalization|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Тип расширяет <xref:System.Windows.Forms.Control?displayProperty=fullName> и содержит два или несколько элементов верхнего уровня, с одинаковыми клавишами доступа, которые хранятся в файле ресурсов.

## <a name="rule-description"></a>Описание правила
 Клавиша доступа, также называемая клавишей быстрого доступа, обеспечивает клавиатурный доступ к элементу управления с помощью клавиши ALT. Если несколько элементов управления имеют дублирующиеся клавиши доступа, поведение клавиши доступа определено нечетко. Пользователь не сможет получить доступ к желаемому элементу управления с помощью ключа доступа и может включаться элемент управления, отличном от того, который предназначен.

 Текущая реализация это правило не учитывает пунктов меню. Тем не менее элементы меню, в том же подменю не должно быть одинаковыми клавишами доступа.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение данного правила, определите уникальные клавиши доступа для всех элементов управления.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
 Следующий пример показывает простейшая форма содержит два элемента управления с одинаковыми клавишами доступа. Ключи хранятся в файле ресурсов, оно не отображается; Тем не менее, их значения отобразятся в закомментированного out `checkBox.Text` строки. Поведение повторяющиеся ускорители могут проверяться путем обмена `checkBox.Text` строки с их аналоги из комментариев. Однако в нашем примере не выдаст предупреждение из правила.

 [!code-csharp[FxCop.Globalization.AvoidDuplicateAccels#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.AvoidDuplicateAccels/cs/FxCop.Globalization.AvoidDuplicateAccels.cs#1)]

## <a name="see-also"></a>См. также
 <xref:System.Resources.ResourceManager?displayProperty=fullName> [Ресурсы в приложениях для настольных систем](http://msdn.microsoft.com/library/8ad495d4-2941-40cf-bf64-e82e85825890)
