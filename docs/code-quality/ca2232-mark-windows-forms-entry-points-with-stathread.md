---
title: CA2232. Отметьте точки входа Windows Forms меткой STAThread
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MarkWindowsFormsEntryPointsWithStaThread
- CA2232
helpviewer_keywords:
- CA2232
- MarkWindowsFormsEntryPointsWithStaThread
ms.assetid: a3c95130-8e7f-4419-9fcd-b67d077e8efb
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 06772f8dd91c27834b329293d06cfbc2a7dcfcef
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/24/2019
ms.locfileid: "71230761"
---
# <a name="ca2232-mark-windows-forms-entry-points-with-stathread"></a>CA2232. Отметьте точки входа Windows Forms меткой STAThread

|||
|-|-|
|TypeName|MarkWindowsFormsEntryPointsWithStaThread|
|CheckId|CA2232|
|Категория|Microsoft. Usage|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина:
Сборка ссылается <xref:System.Windows.Forms> на пространство имен, а точка входа не помечена <xref:System.STAThreadAttribute?displayProperty=fullName> атрибутом.

## <a name="rule-description"></a>Описание правила
 <xref:System.STAThreadAttribute>Указывает, что потоковая модель COM для приложения является однопотоковым апартаментом. Данный атрибут должен находиться в точке входа любого приложения, использующего Windows Forms; если он отсутствует, компоненты Windows могут работать неправильно. Если атрибут отсутствует, приложение использует модель многопоточного подразделения, которая не поддерживается для Windows Forms.

> [!NOTE]
> [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]в проектах, использующих платформу приложений, метод **Main** не должен помечаться STAThread. [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] Компилятор выполняет его автоматически.

## <a name="how-to-fix-violations"></a>Устранение нарушений
Чтобы устранить нарушение этого правила, добавьте <xref:System.STAThreadAttribute> атрибут в точку входа. <xref:System.MTAThreadAttribute?displayProperty=fullName> Если атрибут имеется, удалите его.

## <a name="when-to-suppress-warnings"></a>Когда следует подавлять предупреждения
Предупреждение из этого правила можно отключить, если вы разрабатываете для .NET Compact Framework, для которого <xref:System.STAThreadAttribute> атрибут не требуется и не поддерживается.

## <a name="example"></a>Пример
В следующих примерах показано правильное использование <xref:System.STAThreadAttribute>:

[!code-csharp[FxCop.Usage.StaThread#1](../code-quality/codesnippet/CSharp/ca2232-mark-windows-forms-entry-points-with-stathread_1.cs)]
[!code-vb[FxCop.Usage.StaThread#1](../code-quality/codesnippet/VisualBasic/ca2232-mark-windows-forms-entry-points-with-stathread_1.vb)]