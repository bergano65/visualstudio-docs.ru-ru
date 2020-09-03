---
title: 'CA2232: Пометьте Windows Forms точки входа с помощью STAThread | Документация Майкрософт'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 42bb554f8e57c036d41a89fdc2657a25ecc74e20
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "85540287"
---
# <a name="ca2232-mark-windows-forms-entry-points-with-stathread"></a>CA2232. Отметьте точки входа Windows Forms меткой STAThread
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Элемент|Значение|
|-|-|
|TypeName|MarkWindowsFormsEntryPointsWithStaThread|
|CheckId|CA2232|
|Категория|Microsoft. Usage|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Сборка ссылается на <xref:System.Windows.Forms> пространство имен, а точка входа не помечена <xref:System.STAThreadAttribute?displayProperty=fullName> атрибутом.

## <a name="rule-description"></a>Описание правила
 <xref:System.STAThreadAttribute> Указывает, что потоковая модель COM для приложения является однопотоковым апартаментом. Данный атрибут должен находиться в точке входа любого приложения, использующего Windows Forms; если он отсутствует, компоненты Windows могут работать неправильно. Если атрибут отсутствует, приложение использует модель многопоточного подразделения, которая не поддерживается для Windows Forms.

> [!NOTE]
> [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] в проектах, использующих платформу приложений, метод **Main** не должен помечаться STAThread. [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]Компилятор выполняет его автоматически.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, добавьте <xref:System.STAThreadAttribute> атрибут в точку входа. Если <xref:System.MTAThreadAttribute?displayProperty=fullName> атрибут имеется, удалите его.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Предупреждение из этого правила можно отключить, если вы разрабатываете для .NET Compact Framework, для которого <xref:System.STAThreadAttribute> атрибут не требуется и не поддерживается.

## <a name="example"></a>Пример
 В следующих примерах демонстрируется правильное использование <xref:System.STAThreadAttribute> .

 [!code-csharp[FxCop.Usage.StaThread#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.StaThread/cs/FxCop.Usage.StaThread.cs#1)]
 [!code-vb[FxCop.Usage.StaThread#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.StaThread/vb/FxCop.Usage.StaThread.vb#1)]
