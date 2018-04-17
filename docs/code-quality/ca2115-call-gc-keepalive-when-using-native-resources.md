---
title: 'CA2115: Вызывайте GC. KeepAlive при использовании собственных ресурсов | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- CallGCKeepAliveWhenUsingNativeResources
- CA2115
helpviewer_keywords:
- CA2115
- CallGCKeepAliveWhenUsingNativeResources
ms.assetid: f00a59a7-2c6a-4bbe-a1b3-7bf77d366f34
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 5ea82194eced9caed52e75216091060ff9350379
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="ca2115-call-gckeepalive-when-using-native-resources"></a>CA2115: вызывайте GC.KeepAlive при использовании собственных ресурсов
|||  
|-|-|  
|TypeName|CallGCKeepAliveWhenUsingNativeResources|  
|CheckId|CA2115|  
|Категория|Microsoft.Security|  
|Критическое изменение|Не критическое|  
  
## <a name="cause"></a>Причина  
 Метода, объявленного в типе с методом завершения ссылается <xref:System.IntPtr?displayProperty=fullName> или <xref:System.UIntPtr?displayProperty=fullName> поле, но не вызывает <xref:System.GC.KeepAlive%2A?displayProperty=fullName>.  
  
## <a name="rule-description"></a>Описание правила  
 Сборка мусора завершает объект, если на него больше нет ссылок в управляемом коде. Сборщик мусора не препятствуют неуправляемых ссылок на объекты. Данное правило обнаруживает ошибки, которые могут возникать из-за завершения неуправляемых ресурсов, по-прежнему используемых в машинном коде.  
  
 Это правило предполагает, что <xref:System.IntPtr> и <xref:System.UIntPtr> поля сохранения указателей на неуправляемые ресурсы. Поскольку назначением метода завершения освободить неуправляемые ресурсы, правиле предполагается, что метода завершения освободить неуправляемый ресурс, на который указывает указатель полей. Это правило также предполагает, что метод ссылается на поле указателя для передачи неуправляемого ресурса в неуправляемый код.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Чтобы устранить нарушение данного правила, добавьте вызов <xref:System.GC.KeepAlive%2A> в метод передачи текущего экземпляра (`this` в C# и C++) в качестве аргумента. Поместите этот вызов после последней строки кода, где объект должен быть защищен от сборки мусора. Сразу после вызова <xref:System.GC.KeepAlive%2A>, при условии, что на него нет ссылок из управляемого объекта снова считается готов для сборки мусора.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Это правило используется ряд предположений, которые могут привести к ложным положительным результатам. Можно безопасно подавить предупреждение из этого правила, если:  
  
-   Метод завершения не позволяет освободить содержимое <xref:System.IntPtr> или <xref:System.UIntPtr> поле, связанном с помощью метода.  
  
-   Метод не прошел <xref:System.IntPtr> или <xref:System.UIntPtr> полей в неуправляемый код.  
  
 Внимательно просмотрите другие сообщения, прежде чем отключать их. Данное правило обнаруживает ошибки, которые трудно воспроизвести и отладки.  
  
## <a name="example"></a>Пример  
 В следующем примере `BadMethod` не включает вызов `GC.KeepAlive` и поэтому нарушает правило. `GoodMethod` содержит Исправленный код.  
  
> [!NOTE]
>  В этом примере приведен код, несмотря на то, что код компилируется и выполняется, предупреждение не возникает из-за не создана или освобождения неуправляемых ресурсов.  
  
 [!code-csharp[FxCop.Security.IntptrAndFinalize#1](../code-quality/codesnippet/CSharp/ca2115-call-gc-keepalive-when-using-native-resources_1.cs)]  
  
## <a name="see-also"></a>См. также  
 <xref:System.GC.KeepAlive%2A?displayProperty=fullName>   
 <xref:System.IntPtr?displayProperty=fullName>   
 <xref:System.Object.Finalize%2A?displayProperty=fullName>   
 <xref:System.UIntPtr?displayProperty=fullName>   
 [Шаблон ликвидации](/dotnet/standard/design-guidelines/dispose-pattern)