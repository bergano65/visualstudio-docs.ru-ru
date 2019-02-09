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
ms.openlocfilehash: bd269b099095326a260da7613bf3c2c402e864be
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2019
ms.locfileid: "55914206"
---
# <a name="ca1300-specify-messageboxoptions"></a>CA1300. Укажите MessageBoxOptions

|||
|-|-|
|TypeName|SpecifyMessageBoxOptions|
|CheckId|CA1300|
|Категория|Microsoft.Globalization|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина

Метод вызывает перегрузку <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=fullName> метод, который не принимает <xref:System.Windows.Forms.MessageBoxOptions?displayProperty=fullName> аргумент.

## <a name="rule-description"></a>Описание правила

Чтобы отобразить окно сообщения для языков и региональных параметров, использующих порядок чтения справа налево, передайте [установлены значения MessageBoxOptions.RightAlign](<xref:System.Windows.Forms.MessageBoxOptions.RightAlign>) и [MessageBoxOptions.RtlReading](<xref:System.Windows.Forms.MessageBoxOptions.RtlReading>) поля <xref:System.Windows.Forms.MessageBox.Show%2A> метод. Изучите <xref:System.Windows.Forms.Control.RightToLeft%2A?displayProperty=fullName> свойство содержащегося элемента управления, чтобы определить, следует ли использовать порядок чтения справа налево.

## <a name="how-to-fix-violations"></a>Устранение нарушений

Чтобы устранить нарушение этого правила, вызовите перегрузку <xref:System.Windows.Forms.MessageBox.Show%2A> метода, принимающего <xref:System.Windows.Forms.MessageBoxOptions> аргумент.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений

Его можно безопасно подавить предупреждение из этого правила, если библиотека кода не будет локализовано для языка и региональных параметров, используется порядок чтения справа налево.

## <a name="example"></a>Пример

Пример метода, который отображает окно сообщения, имеющий параметры, соответствующие порядку чтения языка и региональных параметров. Файл ресурсов, который не показан, необходим для построения примера. Следуйте указаниям в приведенном примере для построения примера без файла ресурсов и тестирование компонента справа налево.

[!code-vb[FxCop.Globalization.SpecifyMBOptions#1](../code-quality/codesnippet/VisualBasic/ca1300-specify-messageboxoptions_1.vb)]
[!code-csharp[FxCop.Globalization.SpecifyMBOptions#1](../code-quality/codesnippet/CSharp/ca1300-specify-messageboxoptions_1.cs)]

## <a name="see-also"></a>См. также

- <xref:System.Resources.ResourceManager?displayProperty=fullName>
- [Ресурсы в классических приложениях (.NET Framework)](/dotnet/framework/resources/index)