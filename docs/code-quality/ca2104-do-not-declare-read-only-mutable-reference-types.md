---
title: "CA2104: не объявляйте изменяемые ссылочные типы, доступные только для чтения | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DoNotDeclareReadOnlyMutableReferenceTypes"
  - "CA2104"
helpviewer_keywords: 
  - "CA2104"
  - "DoNotDeclareReadOnlyMutableReferenceTypes"
ms.assetid: 81b83ee5-4db5-4be0-9f8d-90b53894ec3b
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 18
---
# CA2104: не объявляйте изменяемые ссылочные типы, доступные только для чтения
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotDeclareReadOnlyMutableReferenceTypes|  
|CheckId|CA2104|  
|Категория|Microsoft.Security|  
|Критическое изменение|Не критическое|  
  
## Причина  
 Видимый извне тип содержит видимое извне и доступное только для чтение поле, являющееся изменяемым ссылочным типом.  
  
## Описание правила  
 Изменяемый тип — это тип, экземпляр которого может быть изменен.  Примером изменяемого ссылочного типа может служить класс <xref:System.Text.StringBuilder?displayProperty=fullName>.  Он содержит члены, которые могут изменять значение экземпляра класса.  Примером неизменяемого ссылочного типа может служить класс <xref:System.String?displayProperty=fullName>.  После создания экземпляра его значение изменить нельзя.  
  
 Модификатор доступа только для чтения \([readonly](/dotnet/csharp/language-reference/keywords/readonly) в C\#, [ReadOnly](/dotnet/visual-basic/language-reference/modifiers/readonly) в [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], и [const](/visual-cpp/cpp/const-cpp) в C\+\+\) по ссылке на поле типа \(указателя в C\+\+\) препятствует замене поля на другой экземпляр типа ссылки.  Тем не менее модификатор не запрещает, чтобы данные экземпляра этого поля изменялись посредством ссылочного типа.  
  
 Это правило не касается доступных только для чтения полей массива; они вызывают нарушение правила [CA2105: поля массивов не должны быть доступны только для чтения](../code-quality/ca2105-array-fields-should-not-be-read-only.md).  
  
## Устранение нарушений  
 Чтобы устранить нарушение этого правила, удалите модификатор доступа только для чтения, или, если возможно критическое изменение, замените поле, используя неизменяемый тип.  
  
## Отключение предупреждений  
 Можно отключать предупреждения этого правила, если тип поля является неизменяемым.  
  
## Пример  
 В следующем примере показано объявление поля, нарушающее это правило.  
  
 [!code-cpp[FxCop.Security.MutableReferenceTypes#1](../code-quality/codesnippet/CPP/ca2104-do-not-declare-read-only-mutable-reference-types_1.cpp)]
 [!code-cs[FxCop.Security.MutableReferenceTypes#1](../code-quality/codesnippet/CSharp/ca2104-do-not-declare-read-only-mutable-reference-types_1.cs)]
 [!code-vb[FxCop.Security.MutableReferenceTypes#1](../code-quality/codesnippet/VisualBasic/ca2104-do-not-declare-read-only-mutable-reference-types_1.vb)]