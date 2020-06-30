---
title: 'CA1300: укажите MessageBoxOptions | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- SpecifyMessageBoxOptions
- CA1300
helpviewer_keywords:
- SpecifyMessageBoxOptions
- CA1300
ms.assetid: 9357a724-026e-4a3d-a03a-f14635064ec6
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: af0017a7ee6918a80a93ca90c7cf3de78885d61f
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/30/2020
ms.locfileid: "85539195"
---
# <a name="ca1300-specify-messageboxoptions"></a>CA1300. Укажите MessageBoxOptions
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Item|Значение|
|-|-|
|TypeName|SpecifyMessageBoxOptions|
|CheckId|CA1300|
|Категория|Microsoft. Globalization|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Метод вызывает перегрузку <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=fullName> метода, который не принимает <xref:System.Windows.Forms.MessageBoxOptions?displayProperty=fullName> аргумент.

## <a name="rule-description"></a>Описание правила
 Чтобы правильно отобразить окно сообщения для языков и региональных параметров, использующих порядок чтения справа налево, <xref:System.Windows.Forms.MessageBoxOptions> <xref:System.Windows.Forms.MessageBoxOptions> элементы и <xref:System.Windows.Forms.MessageBoxOptions> перечисления должны передаваться в <xref:System.Windows.Forms.MessageBox.Show%2A> метод. Изучите <xref:System.Windows.Forms.Control.RightToLeft%2A?displayProperty=fullName> свойство содержащего элемента управления, чтобы определить, следует ли использовать порядок чтения справа налево.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, вызовите перегрузку <xref:System.Windows.Forms.MessageBox.Show%2A> метода, принимающего <xref:System.Windows.Forms.MessageBoxOptions> аргумент.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Можно отключить вывод предупреждения из этого правила, если библиотека кода не будет локализована для языка и региональных параметров, в которых используется порядок чтения справа налево.

## <a name="example"></a>Пример
 В следующем примере показан метод, который отображает окно сообщения с параметрами, подходящими для порядка чтения языка и региональных параметров. Для построения примера требуется файл ресурсов, который не отображается. Следуйте комментариям в примере, чтобы создать пример без файла ресурсов и проверить функцию "справа налево".

 [!code-csharp[FxCop.Globalization.SpecifyMBOptions#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.SpecifyMBOptions/cs/FxCop.Globalization.SpecifyMBOptions.cs#1)]
 [!code-vb[FxCop.Globalization.SpecifyMBOptions#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Globalization.SpecifyMBOptions/vb/FxCop.Globalization.SpecifyMBOptions.vb#1)]

## <a name="see-also"></a>См. также
 <xref:System.Resources.ResourceManager?displayProperty=fullName> [Ресурсы в приложениях для настольных систем](https://msdn.microsoft.com/library/8ad495d4-2941-40cf-bf64-e82e85825890)
