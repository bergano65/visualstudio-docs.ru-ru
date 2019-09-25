---
title: CA1300. Укажите MessageBoxOptions
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SpecifyMessageBoxOptions
- CA1300
helpviewer_keywords:
- SpecifyMessageBoxOptions
- CA1300
ms.assetid: 9357a724-026e-4a3d-a03a-f14635064ec6
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 746475e60bbe72c4ebfc51f13d0b2d4d0552ff62
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2019
ms.locfileid: "71235196"
---
# <a name="ca1300-specify-messageboxoptions"></a>CA1300. Укажите MessageBoxOptions

|||
|-|-|
|TypeName|SpecifyMessageBoxOptions|
|CheckId|CA1300|
|Категория|Microsoft. Globalization|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина:

Метод вызывает перегрузку <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=fullName> метода, который не <xref:System.Windows.Forms.MessageBoxOptions?displayProperty=fullName> принимает аргумент.

## <a name="rule-description"></a>Описание правила

Чтобы правильно отобразить окно сообщения для языков и региональных параметров, использующих порядок чтения справа налево, передайте в <xref:System.Windows.Forms.MessageBox.Show%2A> метод поля [MessageBoxOptions. RightAlign](<xref:System.Windows.Forms.MessageBoxOptions.RightAlign>) и [MessageBoxOptions. RtlReading](<xref:System.Windows.Forms.MessageBoxOptions.RtlReading>) . Изучите <xref:System.Windows.Forms.Control.RightToLeft%2A?displayProperty=fullName> свойство содержащего элемента управления, чтобы определить, следует ли использовать порядок чтения справа налево.

## <a name="how-to-fix-violations"></a>Устранение нарушений

Чтобы устранить нарушение этого правила, вызовите перегрузку <xref:System.Windows.Forms.MessageBox.Show%2A> метода, <xref:System.Windows.Forms.MessageBoxOptions> принимающего аргумент.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения

Можно отключить вывод предупреждения из этого правила, если библиотека кода не будет локализована для языка и региональных параметров, в которых используется порядок чтения справа налево.

## <a name="example"></a>Пример

В следующем примере показан метод, который отображает окно сообщения с параметрами, подходящими для порядка чтения языка и региональных параметров. Для построения примера требуется файл ресурсов, который не отображается. Следуйте комментариям в примере, чтобы создать пример без файла ресурсов и проверить функцию "справа налево".

[!code-vb[FxCop.Globalization.SpecifyMBOptions#1](../code-quality/codesnippet/VisualBasic/ca1300-specify-messageboxoptions_1.vb)]
[!code-csharp[FxCop.Globalization.SpecifyMBOptions#1](../code-quality/codesnippet/CSharp/ca1300-specify-messageboxoptions_1.cs)]

## <a name="see-also"></a>См. также

- <xref:System.Resources.ResourceManager?displayProperty=fullName>
- [Ресурсы в классических приложениях (.NET Framework)](/dotnet/framework/resources/index)