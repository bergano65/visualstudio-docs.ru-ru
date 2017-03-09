---
title: "CA1300: укажите MessageBoxOptions | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SpecifyMessageBoxOptions"
  - "CA1300"
helpviewer_keywords: 
  - "SpecifyMessageBoxOptions"
  - "CA1300"
ms.assetid: 9357a724-026e-4a3d-a03a-f14635064ec6
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1300: укажите MessageBoxOptions
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|SpecifyMessageBoxOptions|  
|CheckId|CA1300|  
|Категория|Microsoft.Globalization|  
|Критическое изменение|Не критическое|  
  
## Причина  
 Метод вызывает перегрузку метода <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=fullName>, которая не принимает аргумент <xref:System.Windows.Forms.MessageBoxOptions?displayProperty=fullName>.  
  
## Описание правила  
 Чтобы правильно отображать окно сообщения для языков, в которых используется порядок чтения справа налево, методу <xref:System.Windows.Forms.MessageBox.Show%2A> следует передать члены <xref:System.Windows.Forms.MessageBoxOptions> и <xref:System.Windows.Forms.MessageBoxOptions> перечисления <xref:System.Windows.Forms.MessageBoxOptions>.  Чтобы определить, следует ли использовать порядок чтения справа налево, изучите свойство <xref:System.Windows.Forms.Control.RightToLeft%2A?displayProperty=fullName> элемента управления, содержащего окно сообщения.  
  
## Устранение нарушений  
 Чтобы устранить нарушение данного правила, вызовите перегрузку метода <xref:System.Windows.Forms.MessageBox.Show%2A>, которая принимает аргумент <xref:System.Windows.Forms.MessageBoxOptions>.  
  
## Отключение предупреждений  
 Отключение предупреждений о нарушении данного правила безопасно в том случае, если библиотека кода не предназначена для локализации на языки, в которых используется порядок чтения справа налево.  
  
## Пример  
 В следующем примере показан метод, который отображает окно сообщения с параметрами, соответствующими порядку чтения языка.  Для построения данного примера требуется файл ресурсов, который здесь не показан.  Для построения примера без файла ресурса и проверки возможности чтения права налево следуйте комментариям в примере.  
  
 [!code-vb[FxCop.Globalization.SpecifyMBOptions#1](../code-quality/codesnippet/VisualBasic/ca1300-specify-messageboxoptions_1.vb)]
 [!code-cs[FxCop.Globalization.SpecifyMBOptions#1](../code-quality/codesnippet/CSharp/ca1300-specify-messageboxoptions_1.cs)]  
  
## См. также  
 <xref:System.Resources.ResourceManager?displayProperty=fullName>   
 [Ресурсы в приложениях для настольных систем](../Topic/Resources%20in%20Desktop%20Apps.md)