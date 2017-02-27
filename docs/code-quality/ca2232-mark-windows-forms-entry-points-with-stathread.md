---
title: "CA2232: отметьте точки входа Windows Forms меткой STAThread | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MarkWindowsFormsEntryPointsWithStaThread"
  - "CA2232"
helpviewer_keywords: 
  - "CA2232"
  - "MarkWindowsFormsEntryPointsWithStaThread"
ms.assetid: a3c95130-8e7f-4419-9fcd-b67d077e8efb
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 16
---
# CA2232: отметьте точки входа Windows Forms меткой STAThread
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|MarkWindowsFormsEntryPointsWithStaThread|  
|CheckId|CA2232|  
|Категория|Microsoft.Usage|  
|Критическое изменение|Не критическое|  
  
## Причина  
 Сборка ссылается на пространство имен <xref:System.Windows.Forms>, однако ее точка входа не помечена атрибутом <xref:System.STAThreadAttribute?displayProperty=fullName>.  
  
## Описание правила  
 Атрибут <xref:System.STAThreadAttribute> указывает, что потоковой моделью COM для приложения является однопотоковое подразделение.  Данный атрибут должен находиться в точке входа любого приложения, использующего Windows Forms; если он отсутствует, компоненты Windows могут работать неправильно.  Если этот атрибут не указан, приложение использует модель многопотокового подразделения, которая не поддерживается для Windows Forms.  
  
> [!NOTE]
>  В проектах [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], использующих платформу приложений, метод **Main** не требуется помечать атрибутом STAThread.  Компилятор [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] делает это автоматически.  
  
## Устранение нарушений  
 Чтобы устранить нарушение данного правила, добавьте в точку входа атрибут <xref:System.STAThreadAttribute>.  Если в точке входа присутствует атрибут <xref:System.MTAThreadAttribute?displayProperty=fullName>, удалите его.  
  
## Отключение предупреждений  
 Отключение предупреждений о нарушении данного правила безопасно в том случае, если приложение разрабатывается для платформы .NET Compact Framework, для которой атрибут <xref:System.STAThreadAttribute> не требуется и не поддерживается.  
  
## Пример  
 В следующем примере демонстрируется правильное применение атрибута <xref:System.STAThreadAttribute>.  
  
 [!code-cs[FxCop.Usage.StaThread#1](../code-quality/codesnippet/CSharp/ca2232-mark-windows-forms-entry-points-with-stathread_1.cs)]
 [!code-vb[FxCop.Usage.StaThread#1](../code-quality/codesnippet/VisualBasic/ca2232-mark-windows-forms-entry-points-with-stathread_1.vb)]