---
title: "CA1300: Укажите MessageBoxOptions | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SpecifyMessageBoxOptions
- CA1300
helpviewer_keywords:
- SpecifyMessageBoxOptions
- CA1300
ms.assetid: 9357a724-026e-4a3d-a03a-f14635064ec6
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: b47c5f2297d9b13e33dc064a203bfd84ce2d196f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="ca1300-specify-messageboxoptions"></a>CA1300: укажите MessageBoxOptions
|||  
|-|-|  
|TypeName|SpecifyMessageBoxOptions|  
|CheckId|CA1300|  
|Категория|Microsoft.Globalization|  
|Критическое изменение|Не критическое|  
  
## <a name="cause"></a>Причина  
 Метод вызывает перегрузку <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=fullName> метод, который не принимает <xref:System.Windows.Forms.MessageBoxOptions?displayProperty=fullName> аргумент.  
  
## <a name="rule-description"></a>Описание правила  
 Чтобы отобразить окно сообщения для языков, в которых используется порядок чтения справа налево, <xref:System.Windows.Forms.MessageBoxOptions> и <xref:System.Windows.Forms.MessageBoxOptions> члены <xref:System.Windows.Forms.MessageBoxOptions> перечисления должны быть переданы <xref:System.Windows.Forms.MessageBox.Show%2A> метод. Изучите <xref:System.Windows.Forms.Control.RightToLeft%2A?displayProperty=fullName> вмещающего элемента управления для определения необходимости используется порядок чтения справа налево.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Чтобы устранить нарушение данного правила, вызовите перегрузку <xref:System.Windows.Forms.MessageBox.Show%2A> метода, принимающего <xref:System.Windows.Forms.MessageBoxOptions> аргумент.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Можно безопасно отключать предупреждение из этого правила, если библиотека кода не быть локализован для языка и региональных параметров используется порядок чтения справа налево.  
  
## <a name="example"></a>Пример  
 В следующем примере показано метод, который отображает окно сообщения, который имеет параметры, соответствующие порядку чтения языка и региональных параметров. В примере требуется файл ресурсов, оно не отображается. Следуйте комментариям в примере для построения примера без файла ресурсов и тестирование компонента справа налево.  
  
 [!code-vb[FxCop.Globalization.SpecifyMBOptions#1](../code-quality/codesnippet/VisualBasic/ca1300-specify-messageboxoptions_1.vb)]
 [!code-csharp[FxCop.Globalization.SpecifyMBOptions#1](../code-quality/codesnippet/CSharp/ca1300-specify-messageboxoptions_1.cs)]  
  
## <a name="see-also"></a>См. также  
 <xref:System.Resources.ResourceManager?displayProperty=fullName>   
 [Ресурсы в приложениях для настольных систем](/dotnet/framework/resources/index)