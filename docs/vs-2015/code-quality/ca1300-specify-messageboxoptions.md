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
ms.openlocfilehash: 3e21866fce69f768d927882d3ddd47ae3e431265
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663607"
---
# <a name="ca1300-specify-messageboxoptions"></a>CA1300: укажите MessageBoxOptions
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|SpecifyMessageBoxOptions|
|CheckId|CA1300|
|Категория|Microsoft. Globalization|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Метод вызывает перегрузку метода <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=fullName>, который не принимает аргумент <xref:System.Windows.Forms.MessageBoxOptions?displayProperty=fullName>.

## <a name="rule-description"></a>Описание правила
 Чтобы правильно отобразить окно сообщения для языков и региональных параметров, использующих порядок чтения справа налево, <xref:System.Windows.Forms.MessageBoxOptions> и <xref:System.Windows.Forms.MessageBoxOptions> члены перечисления <xref:System.Windows.Forms.MessageBoxOptions> должны быть переданы в метод <xref:System.Windows.Forms.MessageBox.Show%2A>. Изучите свойство <xref:System.Windows.Forms.Control.RightToLeft%2A?displayProperty=fullName> содержащего элемента управления, чтобы определить, следует ли использовать порядок чтения справа налево.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, вызовите перегрузку метода <xref:System.Windows.Forms.MessageBox.Show%2A>, который принимает <xref:System.Windows.Forms.MessageBoxOptions> аргумент.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Можно отключить вывод предупреждения из этого правила, если библиотека кода не будет локализована для языка и региональных параметров, в которых используется порядок чтения справа налево.

## <a name="example"></a>Пример
 В следующем примере показан метод, который отображает окно сообщения с параметрами, подходящими для порядка чтения языка и региональных параметров. Для построения примера требуется файл ресурсов, который не отображается. Следуйте комментариям в примере, чтобы создать пример без файла ресурсов и проверить функцию "справа налево".

 [!code-csharp[FxCop.Globalization.SpecifyMBOptions#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.SpecifyMBOptions/cs/FxCop.Globalization.SpecifyMBOptions.cs#1)]
 [!code-vb[FxCop.Globalization.SpecifyMBOptions#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Globalization.SpecifyMBOptions/vb/FxCop.Globalization.SpecifyMBOptions.vb#1)]

## <a name="see-also"></a>См. также раздел
 <xref:System.Resources.ResourceManager?displayProperty=fullName> [ресурсов в классических приложениях](https://msdn.microsoft.com/library/8ad495d4-2941-40cf-bf64-e82e85825890)
