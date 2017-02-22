---
title: "CA1009: правильно объявите обработчики событий | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1009"
  - "DeclareEventHandlersCorrectly"
helpviewer_keywords: 
  - "CA1009"
  - "DeclareEventHandlersCorrectly"
ms.assetid: ab65c471-1449-49d2-9896-7b9af74284b4
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1009: правильно объявите обработчики событий
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DeclareEventHandlersCorrectly|  
|CheckId|CA1009|  
|Категория|Microsoft.Design|  
|Критическое изменение|Критическое изменение|  
  
## Причина  
 Делегат, который обрабатывает открытое или защищенное событие, имеет неправильную подпись, тип возвращаемого значения или имена параметров.  
  
## Описание правила  
 Методы обработчиков событий принимают два параметра.  Первый параметр принадлежит типу <xref:System.Object?displayProperty=fullName> и называется "sender".  Это объект, вызвавший событие.  Второй параметр принадлежит типу <xref:System.EventArgs?displayProperty=fullName> и называется "e".  Это данные, связанные с событием.  Например, если событие создается при открытии файла, данные события, как правило, содержат имя файла.  
  
 Методы обработчиков событий не должны возвращать значение.  В языке программирования C\# это обозначается типом возвращаемого значения `void`.  Обработчик событий может вызывать несколько методов в нескольких объектах.  Если методам разрешено возвращать значения, для каждого события будет возвращаться несколько значений, однако доступным является только значение последнего вызванного метода.  
  
## Устранение нарушений  
 Чтобы устранить нарушение данного правила, исправьте подпись, тип возвращаемого значения или имена параметров делегата.  Подробные сведения см. в следующем примере.  
  
## Отключение предупреждений  
 Для этого правила отключать вывод предупреждений не следует.  
  
## Пример  
 В следующем примере показан делегат, который можно использовать в качестве обработчика событий.  Подписи методов, которые могут вызываться данным обработчиком событий, соответствуют правилам разработки.  `AlarmEventHandler` — имя типа делегата.  `AlarmEventArgs` наследует от базового класса <xref:System.EventArgs> для данных события и содержит данные события оповещения.  
  
 [!code-cpp[FxCop.Design.EventsTwoParams#1](../code-quality/codesnippet/CPP/ca1009-declare-event-handlers-correctly_1.cpp)]
 [!code-cs[FxCop.Design.EventsTwoParams#1](../code-quality/codesnippet/CSharp/ca1009-declare-event-handlers-correctly_1.cs)]
 [!code-vb[FxCop.Design.EventsTwoParams#1](../code-quality/codesnippet/VisualBasic/ca1009-declare-event-handlers-correctly_1.vb)]  
  
## Связанные правила  
 [CA2109: проверьте видимые обработчики событий](../code-quality/ca2109-review-visible-event-handlers.md)  
  
## См. также  
 <xref:System.EventArgs?displayProperty=fullName>   
 <xref:System.Object?displayProperty=fullName>   
 [События и делегаты](http://msdn.microsoft.com/ru-ru/d98fd58b-fa4f-4598-8378-addf4355a115)