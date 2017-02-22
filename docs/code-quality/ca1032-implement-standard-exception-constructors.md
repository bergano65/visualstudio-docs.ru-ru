---
title: "CA1032: реализуйте стандартные конструкторы исключения | Microsoft Docs"
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
  - "CA1032"
  - "ImplementStandardExceptionConstructors"
helpviewer_keywords: 
  - "CA1032"
  - "ImplementStandardExceptionConstructors"
ms.assetid: a8623c56-273a-4c95-8d83-95911a042be7
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1032: реализуйте стандартные конструкторы исключения
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ImplementStandardExceptionConstructors|  
|CheckId|CA1032|  
|Категория|Microsoft.Design|  
|Критическое изменение|Не критическое|  
  
## Причина  
 Тип расширяет класс <xref:System.Exception?displayProperty=fullName>, однако не объявляет все обязательные конструкторы.  
  
## Описание правила  
 Типы исключений должны реализовывать следующие конструкторы:  
  
-   открытый NewException\(\)  
  
-   открытый NewException\(строка\)  
  
-   открытый NewException\(строка, исключение\)  
  
-   защищенный или закрытый NewException\(SerializationInfo, StreamingContext\)  
  
 Для правильной обработки исключений необходимо предоставить полный набор конструкторов.  Например, конструктор с сигнатурой `NewException(string, Exception)` используется для создания исключений, вызванных другими исключениями.  Без этого конструктора невозможно реализовать обычное поведение управляемого кода в таких ситуациях, то есть создать и вызвать экземпляр пользовательского исключения, которое содержит внутреннее \(вложенное\) исключение.  Первые три конструктора исключений являются открытыми по соглашению.  Четвертый конструктор является защищенным в незапечатанных классах и закрытым в запечатанных классах.  Дополнительные сведения см. в разделе [CA2229: применяйте конструкторы сериализации](../code-quality/ca2229-implement-serialization-constructors.md).  
  
## Устранение нарушений  
 Чтобы устранить нарушение данного правила, добавьте отсутствующие конструкторы в класс исключений и убедитесь, что они обладают правильной доступностью.  
  
## Отключение предупреждений  
 Отключение предупреждений о нарушении данного правила безопасно в том случае, если нарушение вызвано другим уровнем доступа для открытых конструкторов.  
  
## Пример  
 В следующем примере содержится тип исключений, который нарушает данное правило, а также правильно реализованный тип исключений.  
  
 [!code-cs[FxCop.Design.ExceptionMultipleCtors#1](../code-quality/codesnippet/CSharp/ca1032-implement-standard-exception-constructors_1.cs)]