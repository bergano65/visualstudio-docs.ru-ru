---
title: CA1001. Типы, которым принадлежат освобождаемые поля, должны быть освобождаемыми | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1001
- TypesThatOwnDisposableFieldsShouldBeDisposable
helpviewer_keywords:
- CA1001
- TypesThatOwnDisposableFieldsShouldBeDisposable
ms.assetid: c85c126c-2b16-4505-940a-b5ddf873fb22
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 98be3bafb582e4d48560108625be911e53acf664
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58992026"
---
# <a name="ca1001-types-that-own-disposable-fields-should-be-disposable"></a>CA1001. Типы, которым принадлежат освобождаемые поля, должны быть освобождаемыми
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|TypesThatOwnDisposableFieldsShouldBeDisposable|  
|CheckId|CA1001|  
|Категория|Microsoft.Design|  
|Критическое изменение|Non критическое, если тип не видимый за пределами сборки.<br /><br /> Критическое, если тип видим за пределами сборки.|  
  
## <a name="cause"></a>Причина  
 В классе объявляется и реализуется поле экземпляра, который является <xref:System.IDisposable?displayProperty=fullName> типа и класса не реализует <xref:System.IDisposable>.  
  
## <a name="rule-description"></a>Описание правила  
 Класс реализует <xref:System.IDisposable> интерфейс, чтобы освободить неуправляемые ресурсы, удерживаемые им. Поля экземпляра, <xref:System.IDisposable> тип указывает, что поле владеет неуправляемым ресурсом. Класс, который объявляет <xref:System.IDisposable> поле неявно владеет неуправляемым ресурсом и должен реализовывать <xref:System.IDisposable> интерфейс. Если класс не владеет непосредственно неуправляемые ресурсы, он не должен реализовывать метод завершения.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Чтобы устранить нарушение этого правила, реализуйте <xref:System.IDisposable> и из <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> вызов метода <xref:System.IDisposable.Dispose%2A> метод поля.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Для этого правила отключать вывод предупреждений не следует.  
  
## <a name="example"></a>Пример  
 В следующем примере показано, класс, который нарушает правило и класс, соответствующий этому правилу, реализовав <xref:System.IDisposable>. Класс не реализует метод завершения, так как этот класс не владеет неуправляемых ресурсов.  
  
 [!code-csharp[FxCop.Design.DisposableFields#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.DisposableFields/cs/FxCop.Design.DisposableFields.cs#1)]
 [!code-vb[FxCop.Design.DisposableFields#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.DisposableFields/vb/FxCop.Design.DisposableFields.vb#1)]  
  
## <a name="related-rules"></a>Связанные правила  
 [CA2213: следует высвобождать высвобождаемые поля](../code-quality/ca2213-disposable-fields-should-be-disposed.md)  
  
 [CA2216: Высвобождаемые типы должны объявлять метод завершения](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)  
  
 [CA2215: Методы Dispose должны вызывать метод dispose базового класса](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)  
  
 [CA1049: Типы, которым принадлежат собственные ресурсы, должны быть освобождаемыми](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)
