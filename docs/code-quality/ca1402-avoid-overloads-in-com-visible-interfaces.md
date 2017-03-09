---
title: "CA1402: не используйте перегрузки в интерфейсах, видимых в COM | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "AvoidOverloadsInComVisibleInterfaces"
  - "CA1402"
helpviewer_keywords: 
  - "AvoidOverloadsInComVisibleInterfaces"
  - "CA1402"
ms.assetid: 2724c1f9-d5d3-4704-b124-21c4d398e5df
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1402: не используйте перегрузки в интерфейсах, видимых в COM
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AvoidOverloadsInComVisibleInterfaces|  
|CheckId|CA1402|  
|Категория|Microsoft.Interoperability|  
|Критическое изменение|Критическое изменение|  
  
## Причина  
 Видимый интерфейс модели компонентных объектов \(COM\) объявляет перегруженные методы.  
  
## Описание правила  
 Когда перегруженные методы предоставляются клиентам COM, сохраняется имя только первой перегрузки метода.  Последующие перегрузки переименовываются уникальным образом путем добавления к имени символа подчеркивания \("\_"\) и целого числа, соответствующего порядку объявления перегрузки.  В качестве примера рассмотрим следующие методы.  
  
```  
void SomeMethod(int valueOne);  
void SomeMethod(int valueOne, int valueTwo, int valueThree);  
void SomeMethod(int valueOne, int valueTwo);  
```  
  
 Эти методы предоставляются клиентам COM:  
  
```  
void SomeMethod(int valueOne);  
void SomeMethod_2(int valueOne, int valueTwo, int valueThree);  
void SomeMethod_3(int valueOne, int valueTwo);  
```  
  
 Клиенты COM Visual Basic 6 не могут реализовывать методы интерфейса с помощью символа подчеркивания в имени.  
  
## Устранение нарушений  
 Чтобы устранить нарушение этого правила, переименуйте перегруженные методы так, чтобы имена были уникальными.  Второй вариант: сделайте интерфейсы невидимыми для COM, изменив их доступность на `internal` \(`Friend` в [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\) или присвоив атрибуту <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> значение `false`.  
  
## Отключение предупреждений  
 Для этого правила отключать вывод предупреждений не следует.  
  
## Пример  
 В следующем примере демонстрируется интерфейс, нарушающий описанное правило, а также интерфейс, выполняющий его.  
  
 [!code-vb[FxCop.Interoperability.OverloadsInterface#1](../code-quality/codesnippet/VisualBasic/ca1402-avoid-overloads-in-com-visible-interfaces_1.vb)]
 [!code-cs[FxCop.Interoperability.OverloadsInterface#1](../code-quality/codesnippet/CSharp/ca1402-avoid-overloads-in-com-visible-interfaces_1.cs)]  
  
## Связанные правила  
 [CA1413: избегайте использования не открытых полей в видимых типах значений COM](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)  
  
 [CA1407: не используйте статические члены в видимых COM типах](../Topic/CA1407:%20Avoid%20static%20members%20in%20COM%20visible%20types.md)  
  
 [CA1017: помечайте сборки атрибутом ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)  
  
## См. также  
 [Interoperating with Unmanaged Code](../Topic/Interoperating%20with%20Unmanaged%20Code.md)   
 [Тип данных Long](/dotnet/visual-basic/language-reference/data-types/long-data-type)