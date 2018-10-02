---
title: 'CA2115: Вызывайте GC. KeepAlive при использовании машинных ресурсов | Документация Майкрософт'
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
ms.openlocfilehash: 461b0dfe0448636b33e4e2e09a5c15e3aa1e0773
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2018
ms.locfileid: "47591117"
---
# <a name="ca2115-call-gckeepalive-when-using-native-resources"></a>CA2115: вызывайте GC.KeepAlive при использовании собственных ресурсов
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [CA2115: вызов сборки Мусора. KeepAlive при использовании машинных ресурсов](https://docs.microsoft.com/visualstudio/code-quality/ca2115-call-gc-keepalive-when-using-native-resources).

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

-   Метод завершения не позволяет освободить содержимое <xref:System.IntPtr> или <xref:System.UIntPtr> поле ссылается на метод.

-   Метод не выполняет <xref:System.IntPtr> или <xref:System.UIntPtr> полей в неуправляемый код.

 Внимательно просмотрите другие сообщения, прежде чем отключать их. Это правило обнаруживает ошибки, которые трудно воспроизвести и отладки.

## <a name="example"></a>Пример
 В следующем примере `BadMethod` не включает вызов `GC.KeepAlive` и таким образом нарушает правило. `GoodMethod` содержит Исправленный код.

> [!NOTE]
>  В этом примере приведен код, несмотря на то, что код компилируется и выполняется, предупреждение не возникает, так как неуправляемый ресурс не при создании или освобождении.

 [!code-csharp[FxCop.Security.IntptrAndFinalize#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.IntptrAndFinalize/cs/FxCop.Security.IntptrAndFinalize.cs#1)]

## <a name="see-also"></a>См. также
 <xref:System.GC.KeepAlive%2A?displayProperty=fullName> <xref:System.IntPtr?displayProperty=fullName>
 <xref:System.Object.Finalize%2A?displayProperty=fullName>
 <xref:System.UIntPtr?displayProperty=fullName>
 [Шаблон ликвидации](http://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)



