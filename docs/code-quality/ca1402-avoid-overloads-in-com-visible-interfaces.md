---
title: "CA1402: Не используйте перегрузки в интерфейсах, видимых COM | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- AvoidOverloadsInComVisibleInterfaces
- CA1402
helpviewer_keywords:
- AvoidOverloadsInComVisibleInterfaces
- CA1402
ms.assetid: 2724c1f9-d5d3-4704-b124-21c4d398e5df
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: fdba95f57b969173cdcbfecbb8c2d8bcbc298d32
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="ca1402-avoid-overloads-in-com-visible-interfaces"></a>CA1402: не используйте перегрузки в интерфейсах, видимых в COM
|||  
|-|-|  
|TypeName|AvoidOverloadsInComVisibleInterfaces|  
|CheckId|CA1402|  
|Категория|Microsoft.Interoperability|  
|Критическое изменение|Критическое|  
  
## <a name="cause"></a>Причина  
 Компонент модели объектов (COM) отображается интерфейс объявляет перегруженные методы.  
  
## <a name="rule-description"></a>Описание правила  
 Когда перегруженные методы предоставляются клиентам COM, сохраняется имя только первой перегрузки метода. Последующие перегрузки переименовываются уникальным образом путем добавления к имени символа подчеркивания «_» и целого числа, соответствующего порядку объявления перегрузки. Например рассмотрим следующие методы.  
  
```  
void SomeMethod(int valueOne);  
void SomeMethod(int valueOne, int valueTwo, int valueThree);  
void SomeMethod(int valueOne, int valueTwo);  
```  
  
 Эти методы предоставляются клиентам COM, следующим образом.  
  
```  
void SomeMethod(int valueOne);  
void SomeMethod_2(int valueOne, int valueTwo, int valueThree);  
void SomeMethod_3(int valueOne, int valueTwo);  
```  
  
 Клиенты COM Visual Basic 6 не могут реализовывать методы интерфейса с помощью символа подчеркивания в имени.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Чтобы устранить нарушение данного правила, переименуйте перегруженные методы, чтобы имена были уникальными. Кроме того, сделать интерфейс невидимый для COM, изменив специальные возможности `internal` (`Friend` в [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) или путем применения <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> атрибуту присвоено значение `false`.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Для этого правила отключать вывод предупреждений не следует.  
  
## <a name="example"></a>Пример  
 В следующем примере показано, интерфейс, который нарушает правило и интерфейс, соответствующий этому правилу.  
  
 [!code-vb[FxCop.Interoperability.OverloadsInterface#1](../code-quality/codesnippet/VisualBasic/ca1402-avoid-overloads-in-com-visible-interfaces_1.vb)]
 [!code-csharp[FxCop.Interoperability.OverloadsInterface#1](../code-quality/codesnippet/CSharp/ca1402-avoid-overloads-in-com-visible-interfaces_1.cs)]  
  
## <a name="related-rules"></a>Связанные правила  
 [CA1413: избегайте использования не открытых полей в видимых типах значений COM](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)  
  
 [CA1407: не используйте статические члены в видимых COM типах](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)  
  
 [CA1017: помечайте сборки атрибутом ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)  
  
## <a name="see-also"></a>См. также  
 [Взаимодействие с неуправляемым кодом](/dotnet/framework/interop/index)   
 [Тип данных Long](/dotnet/visual-basic/language-reference/data-types/long-data-type)