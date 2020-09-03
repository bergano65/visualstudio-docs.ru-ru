---
title: 'CA2115: вызов GC. KeepAlive при использовании машинных ресурсов | Документация Майкрософт'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: c668172ca318000068fb4e90f4848e456c32208d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "85543628"
---
# <a name="ca2115-call-gckeepalive-when-using-native-resources"></a>CA2115. Вызывайте GC.KeepAlive при использовании собственных ресурсов
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Элемент|Значение|
|-|-|
|TypeName|CallGCKeepAliveWhenUsingNativeResources|
|CheckId|CA2115|
|Категория|Microsoft.Security|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Метод, объявленный в типе с методом завершения, ссылается на <xref:System.IntPtr?displayProperty=fullName> <xref:System.UIntPtr?displayProperty=fullName> поле или, но не вызывает <xref:System.GC.KeepAlive%2A?displayProperty=fullName> .

## <a name="rule-description"></a>Описание правила
 Сборка мусора завершает объект, если в управляемом коде больше нет ссылок на него. Неуправляемые ссылки на объекты не предотвращают сбор мусора. Данное правило обнаруживает ошибки, которые могут возникать из-за завершения неуправляемых ресурсов, по-прежнему используемых в машинном коде.

 Это правило предполагает, <xref:System.IntPtr> что <xref:System.UIntPtr> поля и хранят указатели на неуправляемые ресурсы. Поскольку цель метода завершения — освободить неуправляемые ресурсы, правило предполагает, что метод завершения освобождает неуправляемый ресурс, на который указывает поле указателя. В этом правиле также предполагается, что метод ссылается на поле указателя, чтобы передать неуправляемый ресурс в неуправляемый код.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, добавьте вызов <xref:System.GC.KeepAlive%2A> в метод, передав текущий экземпляр ( `this` в C# и C++) в качестве аргумента. Поместите вызов после последней строки кода, в которой объект должен быть защищен от сборки мусора. Сразу после вызова <xref:System.GC.KeepAlive%2A> объект снова считается готовым к сборке мусора, если нет управляемых ссылок на нее.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Это правило делает некоторые предположения, которые могут привести к ложным срабатываниям. Предупреждение из этого правила можно спокойно отключить, если:

- Финализатор не освобождает содержимое <xref:System.IntPtr> поля или, <xref:System.UIntPtr> на которое ссылается метод.

- Метод не передает <xref:System.IntPtr> поле или в <xref:System.UIntPtr> неуправляемый код.

  Внимательно проверьте другие сообщения, прежде чем исключать их. Это правило обнаруживает ошибки, которые трудно воспроизвести и отладить.

## <a name="example"></a>Пример
 В следующем примере не `BadMethod` включает вызов `GC.KeepAlive` и, следовательно, нарушает правило. `GoodMethod` содержит исправленный код.

> [!NOTE]
> Этот пример является псевдо-кодом, хотя код компилируется и выполняется, предупреждение не срабатывает, так как неуправляемый ресурс не создается или освобождается.

 [!code-csharp[FxCop.Security.IntptrAndFinalize#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.IntptrAndFinalize/cs/FxCop.Security.IntptrAndFinalize.cs#1)]

## <a name="see-also"></a>См. также:
 <xref:System.GC.KeepAlive%2A?displayProperty=fullName> <xref:System.IntPtr?displayProperty=fullName>
 <xref:System.Object.Finalize%2A?displayProperty=fullName>
 <xref:System.UIntPtr?displayProperty=fullName>
 [Шаблон ликвидации](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)
