---
title: 'CA1415: Правильно объявляйте методы P вызывает | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- CA1415
- DeclarePInvokesCorrectly
helpviewer_keywords:
- CA1415
- DeclarePInvokesCorrectly
ms.assetid: 42a90796-0264-4460-bf97-2fb4a093dfdc
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bfad5d5a699fda54c91e674365b65305ef7fad0d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="ca1415-declare-pinvokes-correctly"></a>CA1415: правильно объявляйте методы P/Invoke
|||  
|-|-|  
|TypeName|DeclarePInvokesCorrectly|  
|CheckId|CA1415|  
|Категория|Microsoft.Interoperability|  
|Критическое изменение|Non критическое, если метод P/Invoke, объявляющий параметр не может быть видим за пределами сборки. Критическое, если метод P/Invoke, объявляющий параметр может отображаться за пределами сборки.|  
  
## <a name="cause"></a>Причина  
 Метод вызова платформы объявлен неправильно.  
  
## <a name="rule-description"></a>Описание правила  
 Платформа вызывать неуправляемый код метода доступа и определяется с помощью `Declare` ключевое слово в [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] или <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>. В настоящее время это правило ищет объявления методов, предназначенных для функций Win32, имеющих указатель на параметр структуры OVERLAPPED вызова платформы и соответствующий управляемый параметр не является указателем на <xref:System.Threading.NativeOverlapped?displayProperty=fullName> структуры.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Чтобы устранить нарушение этого правила, следует правильно объявлять платформы вызова метода.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Для этого правила отключать вывод предупреждений не следует.  
  
## <a name="example"></a>Пример  
 В следующем примере показан вызов методов, которые нарушают правила и удовлетворяют правилу платформы.  
  
 [!code-csharp[FxCop.Interoperability.DeclarePInvokes#1](../code-quality/codesnippet/CSharp/ca1415-declare-p-invokes-correctly_1.cs)]  
  
## <a name="see-also"></a>См. также  
 [Взаимодействие с неуправляемым кодом](/dotnet/framework/interop/index)