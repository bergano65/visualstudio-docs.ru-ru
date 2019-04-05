---
title: CA2232. Точки входа Windows Forms Марк STAThread | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- MarkWindowsFormsEntryPointsWithStaThread
- CA2232
helpviewer_keywords:
- CA2232
- MarkWindowsFormsEntryPointsWithStaThread
ms.assetid: a3c95130-8e7f-4419-9fcd-b67d077e8efb
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: d486189b557c0c1146be68e6c0328cb49d5ed291
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58993819"
---
# <a name="ca2232-mark-windows-forms-entry-points-with-stathread"></a>CA2232. Отметьте точки входа Windows Forms меткой STAThread
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|MarkWindowsFormsEntryPointsWithStaThread|
|CheckId|CA2232|
|Категория|Microsoft.Usage|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Ссылается на сборку <xref:System.Windows.Forms> пространство имен и его точки входа не помечен атрибутом <xref:System.STAThreadAttribute?displayProperty=fullName> атрибута.

## <a name="rule-description"></a>Описание правила
 <xref:System.STAThreadAttribute> Указывает, что потоковой моделью COM для приложения является однопотоковое подразделение. Данный атрибут должен находиться в точке входа любого приложения, использующего Windows Forms; если он отсутствует, компоненты Windows могут работать неправильно. Если атрибут отсутствует, приложение использует модель многопотокового подразделения, которая не поддерживается для Windows Forms.

> [!NOTE]
>  [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] проекты, использующие платформы приложений нет необходимости пометить **Main** метод с STAThread. [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] Компилятор делает это автоматически.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, добавьте <xref:System.STAThreadAttribute> атрибута к точке входа. Если <xref:System.MTAThreadAttribute?displayProperty=fullName> присутствует атрибут, удалите ее.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Его можно безопасно подавить предупреждение из этого правила, при разработке для .NET Compact Framework, для которого <xref:System.STAThreadAttribute> атрибута требуется и не поддерживается.

## <a name="example"></a>Пример
 В следующих примерах демонстрируется правильное применение атрибута <xref:System.STAThreadAttribute>.

 [!code-csharp[FxCop.Usage.StaThread#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.StaThread/cs/FxCop.Usage.StaThread.cs#1)]
 [!code-vb[FxCop.Usage.StaThread#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.StaThread/vb/FxCop.Usage.StaThread.vb#1)]
