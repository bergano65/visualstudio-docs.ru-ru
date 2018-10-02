---
title: 'CA1300: Укажите MessageBoxOptions | Документация Майкрософт'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- SpecifyMessageBoxOptions
- CA1300
helpviewer_keywords:
- SpecifyMessageBoxOptions
- CA1300
ms.assetid: 9357a724-026e-4a3d-a03a-f14635064ec6
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: bf2cf17b41248032caf01b0cfedbe9b70ecbefb2
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2018
ms.locfileid: "47591956"
---
# <a name="ca1300-specify-messageboxoptions"></a>CA1300: укажите MessageBoxOptions
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [CA1300: укажите MessageBoxOptions](https://docs.microsoft.com/visualstudio/code-quality/ca1300-specify-messageboxoptions).

|||
|-|-|
|TypeName|SpecifyMessageBoxOptions|
|CheckId|CA1300|
|Категория|Microsoft.Globalization|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Метод вызывает перегрузку <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=fullName> метод, который не принимает <xref:System.Windows.Forms.MessageBoxOptions?displayProperty=fullName> аргумент.

## <a name="rule-description"></a>Описание правила
 Отображение окна сообщения для языков и региональных параметров, использующих порядок чтения справа налево, <xref:System.Windows.Forms.MessageBoxOptions> и <xref:System.Windows.Forms.MessageBoxOptions> членами <xref:System.Windows.Forms.MessageBoxOptions> перечисления должны быть переданы <xref:System.Windows.Forms.MessageBox.Show%2A> метод. Изучите <xref:System.Windows.Forms.Control.RightToLeft%2A?displayProperty=fullName> свойство содержащегося элемента управления, чтобы определить, следует ли использовать порядок чтения справа налево.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, вызовите перегрузку <xref:System.Windows.Forms.MessageBox.Show%2A> метода, принимающего <xref:System.Windows.Forms.MessageBoxOptions> аргумент.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Его можно безопасно подавить предупреждение из этого правила, если библиотека кода не будет локализовано для языка и региональных параметров, используется порядок чтения справа налево.

## <a name="example"></a>Пример
 Пример метода, который отображает окно сообщения, имеющий параметры, соответствующие порядку чтения языка и региональных параметров. Файл ресурсов, который не показан, необходим для построения примера. Следуйте указаниям в приведенном примере для построения примера без файла ресурсов и тестирование компонента справа налево.

 [!code-csharp[FxCop.Globalization.SpecifyMBOptions#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.SpecifyMBOptions/cs/FxCop.Globalization.SpecifyMBOptions.cs#1)]
 [!code-vb[FxCop.Globalization.SpecifyMBOptions#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Globalization.SpecifyMBOptions/vb/FxCop.Globalization.SpecifyMBOptions.vb#1)]

## <a name="see-also"></a>См. также
 <xref:System.Resources.ResourceManager?displayProperty=fullName> [Ресурсы в приложениях для настольных систем](http://msdn.microsoft.com/library/8ad495d4-2941-40cf-bf64-e82e85825890)



