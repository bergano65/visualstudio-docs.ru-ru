---
title: 'CA1301: не следует допускать повторяющихся сочетаний клавиш быстрого доступа'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0a323ce01201dd4a3650d6da0ddde8edfeea0512
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
---
# <a name="ca1301-avoid-duplicate-accelerators"></a>CA1301: не следует допускать повторяющихся сочетаний клавиш быстрого доступа
|||
|-|-|
|TypeName|AvoidDuplicateAccelerators|
|CheckId|CA1301|
|Категория|Microsoft.Globalization|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Тип расширяет <xref:System.Windows.Forms.Control?displayProperty=fullName> и содержит два или более элементов управления верхнего уровня, которые имеют идентичный доступ ключей, хранящихся в файле ресурсов.

## <a name="rule-description"></a>Описание правила
 Клавиша доступа, также называемая клавишей быстрого доступа, обеспечивает клавиатурный доступ к элементу управления с помощью клавиши ALT. Если несколько элементов управления имеют дублирующиеся клавиши доступа, поведение клавиши доступа определено нечетко. Пользователь не сможет получить доступ к желаемому элементу управления с помощью клавиши доступа и могут быть включены элемент управления, отличной от той, которая предназначена.

 Текущая реализация это правило не учитывает пунктов меню. Тем не менее элементы меню в одном подменю не следует одинаковыми клавишами доступа.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение данного правила, определите уникальные клавиши доступа для всех элементов управления.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Для этого правила отключать вывод предупреждений не следует.

## <a name="example"></a>Пример
 В следующем примере показано простейшая форма содержит два элемента управления, имеющих одинаковые комбинации клавиш. Ключи хранятся в файле ресурсов, оно не отображается; Тем не менее, их значения отобразятся в закомментированному out `checkBox.Text` строк. Поведение совпадающих клавиш быстрого доступа, можно просмотреть в обмене `checkBox.Text` строки с аналогичными функциями закомментированы. Однако в этом случае выполняется не выдаст предупреждение из правила.

 [!code-csharp[FxCop.Globalization.AvoidDuplicateAccels#1](../code-quality/codesnippet/CSharp/ca1301-avoid-duplicate-accelerators_1.cs)]

## <a name="see-also"></a>См. также
 <xref:System.Resources.ResourceManager?displayProperty=fullName> [Ресурсы в приложениях для настольных систем](/dotnet/framework/resources/index)