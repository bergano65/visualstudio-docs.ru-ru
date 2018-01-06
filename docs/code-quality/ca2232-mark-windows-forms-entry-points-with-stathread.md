---
title: "CA2232: Точки входа знак Windows Forms меткой STAThread | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- MarkWindowsFormsEntryPointsWithStaThread
- CA2232
helpviewer_keywords:
- CA2232
- MarkWindowsFormsEntryPointsWithStaThread
ms.assetid: a3c95130-8e7f-4419-9fcd-b67d077e8efb
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: fe12ce5947a22414aaf07c59945fd667b106101f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="ca2232-mark-windows-forms-entry-points-with-stathread"></a>CA2232: отметьте точки входа Windows Forms меткой STAThread
|||  
|-|-|  
|TypeName|MarkWindowsFormsEntryPointsWithStaThread|  
|CheckId|CA2232|  
|Категория|Microsoft.Usage|  
|Критическое изменение|Не критическое|  
  
## <a name="cause"></a>Причина  
 Ссылается на сборку <xref:System.Windows.Forms> пространство имен и его точки входа не помечен атрибутом <xref:System.STAThreadAttribute?displayProperty=fullName> атрибута.  
  
## <a name="rule-description"></a>Описание правила  
 <xref:System.STAThreadAttribute>Указывает, что потоковой моделью COM для приложения является однопотоковое подразделение. Данный атрибут должен находиться в точке входа любого приложения, использующего Windows Forms; если он отсутствует, компоненты Windows могут работать неправильно. Если атрибут отсутствует, приложение использует модель многопотокового подразделения, которая не поддерживается для Windows Forms.  
  
> [!NOTE]
>  [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]проекты, использующие платформу приложения нет необходимости пометить **Main** метод меткой STAThread. [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] Компилятор делает это автоматически.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Чтобы устранить нарушение данного правила, добавьте <xref:System.STAThreadAttribute> атрибута к точке входа. Если <xref:System.MTAThreadAttribute?displayProperty=fullName> присутствует атрибут, удалите его.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Его можно безопасно подавить предупреждение из этого правила, при разработке для .NET Compact Framework, для которого <xref:System.STAThreadAttribute> атрибута требуется и не поддерживается.  
  
## <a name="example"></a>Пример  
 В следующих примерах демонстрируется правильное применение <xref:System.STAThreadAttribute>.  
  
 [!code-csharp[FxCop.Usage.StaThread#1](../code-quality/codesnippet/CSharp/ca2232-mark-windows-forms-entry-points-with-stathread_1.cs)]
 [!code-vb[FxCop.Usage.StaThread#1](../code-quality/codesnippet/VisualBasic/ca2232-mark-windows-forms-entry-points-with-stathread_1.vb)]