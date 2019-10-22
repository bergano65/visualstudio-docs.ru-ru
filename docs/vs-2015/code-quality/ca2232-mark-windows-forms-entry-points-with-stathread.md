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
ms.openlocfilehash: 084e7a093f92aa8eda9d9edc11865ac319adfad0
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662797"
---
# <a name="ca2232-mark-windows-forms-entry-points-with-stathread"></a>CA2232: отметьте точки входа Windows Forms меткой STAThread
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|MarkWindowsFormsEntryPointsWithStaThread|
|CheckId|CA2232|
|Категория|Microsoft. Usage|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Сборка ссылается на пространство имен <xref:System.Windows.Forms>, и его точка входа не помечена атрибутом <xref:System.STAThreadAttribute?displayProperty=fullName>.

## <a name="rule-description"></a>Описание правила
 <xref:System.STAThreadAttribute> указывает, что потоковая модель COM для приложения является однопотоковым апартаментом. Данный атрибут должен находиться в точке входа любого приложения, использующего Windows Forms; если он отсутствует, компоненты Windows могут работать неправильно. Если атрибут отсутствует, приложение использует модель многопоточного подразделения, которая не поддерживается для Windows Forms.

> [!NOTE]
> [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] проектов, использующих платформу приложений, не нужно помечать метод **Main** STAThread. Компилятор [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] выполняет его автоматически.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, добавьте к точке входа атрибут <xref:System.STAThreadAttribute>. Если атрибут <xref:System.MTAThreadAttribute?displayProperty=fullName> имеется, удалите его.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Предупреждение из этого правила можно отключить, если вы разрабатываете для .NET Compact Framework, для которого атрибут <xref:System.STAThreadAttribute> не требуется и не поддерживается.

## <a name="example"></a>Пример
 В следующих примерах демонстрируется правильное использование <xref:System.STAThreadAttribute>.

 [!code-csharp[FxCop.Usage.StaThread#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.StaThread/cs/FxCop.Usage.StaThread.cs#1)]
 [!code-vb[FxCop.Usage.StaThread#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.StaThread/vb/FxCop.Usage.StaThread.vb#1)]
