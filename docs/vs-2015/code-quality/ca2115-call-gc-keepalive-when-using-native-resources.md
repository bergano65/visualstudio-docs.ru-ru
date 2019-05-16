---
title: CA2115. Вызовите GC. KeepAlive при использовании машинных ресурсов | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CallGCKeepAliveWhenUsingNativeResources
- CA2115
helpviewer_keywords:
- CA2115
- CallGCKeepAliveWhenUsingNativeResources
ms.assetid: f00a59a7-2c6a-4bbe-a1b3-7bf77d366f34
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: c035c05480279012fba1101c3a60b020d34b1890
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65687344"
---
# <a name="ca2115-call-gckeepalive-when-using-native-resources"></a>CA2115. Вызывайте GC.KeepAlive при использовании собственных ресурсов
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|CallGCKeepAliveWhenUsingNativeResources|
|CheckId|CA2115|
|Категория|Microsoft.Security|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Метод, объявленный в тип с методом завершения ссылается на <xref:System.IntPtr?displayProperty=fullName> или <xref:System.UIntPtr?displayProperty=fullName> поле, но не вызывает <xref:System.GC.KeepAlive%2A?displayProperty=fullName>.

## <a name="rule-description"></a>Описание правила
 Сборка мусора завершает объект, если больше нет ссылок на него в управляемом коде. Сборка мусора не препятствует неуправляемых ссылок на объекты. Данное правило обнаруживает ошибки, которые могут возникать из-за завершения неуправляемых ресурсов, по-прежнему используемых в машинном коде.

 Это правило предполагает, что <xref:System.IntPtr> и <xref:System.UIntPtr> поля сохранения указателей на неуправляемые ресурсы. Поскольку финализатор предназначена для того, чтобы освободить неуправляемые ресурсы, правиле предполагается, что метод завершения будет освободить неуправляемый ресурс, на которые указывает указатель полей. Это правило также предполагается, что метод ссылается на поле указателя для передачи неуправляемого ресурса в неуправляемый код.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, добавьте вызов <xref:System.GC.KeepAlive%2A> методу, передачи текущего экземпляра (`this` в C# и C++) в качестве аргумента. Поместите этот вызов после последней строки кода, где объект должен быть защищен от сборщика мусора. Сразу после вызова <xref:System.GC.KeepAlive%2A>, объект снова считается готовым для сборки мусора при условии, что на него нет управляемых ссылок.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Это правило обеспечивает ряд предположений, которые могут привести к ложным положительным результатам. Можно безопасно подавить предупреждение из этого правила, если:

- Метод завершения не позволяет освободить содержимое <xref:System.IntPtr> или <xref:System.UIntPtr> поле ссылается на метод.

- Метод не выполняет <xref:System.IntPtr> или <xref:System.UIntPtr> полей в неуправляемый код.

  Внимательно просмотрите другие сообщения, прежде чем отключать их. Это правило обнаруживает ошибки, которые трудно воспроизвести и отладки.

## <a name="example"></a>Пример
 В следующем примере `BadMethod` не включает вызов `GC.KeepAlive` и таким образом нарушает правило. `GoodMethod` содержит Исправленный код.

> [!NOTE]
> В этом примере приведен код, несмотря на то, что код компилируется и выполняется, предупреждение не возникает, так как неуправляемый ресурс не при создании или освобождении.

 [!code-csharp[FxCop.Security.IntptrAndFinalize#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.IntptrAndFinalize/cs/FxCop.Security.IntptrAndFinalize.cs#1)]

## <a name="see-also"></a>См. также
 <xref:System.GC.KeepAlive%2A?displayProperty=fullName> <xref:System.IntPtr?displayProperty=fullName>
 <xref:System.Object.Finalize%2A?displayProperty=fullName>
 <xref:System.UIntPtr?displayProperty=fullName>
 [Шаблон ликвидации](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)
