---
title: "CA2208: правильно создавайте экземпляры аргументов исключений | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2208"
  - "InstantiateArgumentExceptionsCorrectly"
helpviewer_keywords: 
  - "CA2208"
  - "InstantiateArgumentExceptionsCorrectly"
ms.assetid: e2a48939-d9fa-478c-b2f9-3bdbce07dff7
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 19
---
# CA2208: правильно создавайте экземпляры аргументов исключений
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|InstantiateArgumentExceptionsCorrectly|  
|CheckId|CA2208|  
|Категория|Microsoft.Usage|  
|Критическое изменение|Не критическое|  
  
## Причина  
 Возможные причины:  
  
-   Выполнен вызов конструктора по умолчанию \(не принимающего параметров\), который принадлежит к типу [System.ArgumentException](assetId:///System.ArgumentException?qualifyHint=True&autoUpgrade=True) или наследует от этого типа.  
  
-   Неверный строковый аргумент передан параметризованному конструктору, который принадлежит к типу [System.ArgumentException.](assetId:///System.ArgumentException.?qualifyHint=True&autoUpgrade=True) или наследуется от этого типа.  
  
## Описание правила  
 Вместо конструктора по умолчанию вызовите одну из перегрузок этого конструктора, которая позволяет предоставлять более содержательные сообщения об исключениях.  Сообщение об исключении должно предназначаться разработчикам и предоставлять четкие сведения о состоянии ошибки и способах устранения этой ошибки или предотвращения ее появления.  
  
 Подписи одного или двух строковых конструкторов типа <xref:System.ArgumentException> или одного из его производных типов не соответствуют объявлению с точки зрения использования параметров `message` и `paramName`.  Убедитесь, что эти конструкторы вызываются с правильными строковыми аргументами.  Подписи должны выглядеть следующим образом:  
  
 <xref:System.ArgumentException>\(строка `message`\)  
  
 <xref:System.ArgumentException>\(строка `message`, строка `paramName`\)  
  
 <xref:System.ArgumentNullException>\(строка `paramName`\)  
  
 <xref:System.ArgumentNullException>\(строка `paramName`, строка `message`\)  
  
 <xref:System.ArgumentOutOfRangeException>\(строка `paramName`\)  
  
 <xref:System.ArgumentOutOfRangeException>\(строка `paramName`, строка `message`\)  
  
 <xref:System.DuplicateWaitObjectException>\(строка `parameterName`\)  
  
 <xref:System.DuplicateWaitObjectException>\(строка `parameterName`, строка `message`\)  
  
## Устранение нарушений  
 Для устранения нарушения данного правила вызовите конструктор, который принимает сообщение, имя параметра или оба этих аргумента, и убедитесь, что аргументы соответствуют типу <xref:System.ArgumentException> вызываемого конструктора.  
  
## Отключение предупреждений  
 Отключение предупреждений о нарушении данного правила безопасно только в том случае, если параметризованный конструктор вызывается с правильными аргументами.  
  
## Пример  
 В следующем примере показан конструктор, который неверно создает экземпляр типа ArgumentNullException.  
  
 [!code-cpp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../code-quality/codesnippet/CPP/ca2208-instantiate-argument-exceptions-correctly_1.cpp)]
 [!code-cs[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../code-quality/codesnippet/CSharp/ca2208-instantiate-argument-exceptions-correctly_1.cs)]
 [!code-vb[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#1](../code-quality/codesnippet/VisualBasic/ca2208-instantiate-argument-exceptions-correctly_1.vb)]  
  
## Пример  
 В следующем примере описанное нарушение устраняется посредством изменения порядка аргументов конструктора.  
  
 [!code-cpp[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../code-quality/codesnippet/CPP/ca2208-instantiate-argument-exceptions-correctly_2.cpp)]
 [!code-cs[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../code-quality/codesnippet/CSharp/ca2208-instantiate-argument-exceptions-correctly_2.cs)]
 [!code-vb[FxCop.Usage.InstantiateArgumentExceptionsCorrectly#2](../code-quality/codesnippet/VisualBasic/ca2208-instantiate-argument-exceptions-correctly_2.vb)]