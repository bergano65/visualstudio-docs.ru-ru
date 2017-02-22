---
title: "CA1061: не следует скрывать методы базового класса | Microsoft Docs"
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
  - "CA1061"
  - "DoNotHideBaseClassMethods"
helpviewer_keywords: 
  - "CA1061"
  - "DoNotHideBaseClassMethods"
ms.assetid: 0bda9dc8-87b4-4038-ab9d-563298387466
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1061: не следует скрывать методы базового класса
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotHideBaseClassMethods|  
|CheckId|CA1061|  
|Категория|Microsoft.Design|  
|Критическое изменение|Критическое изменение|  
  
## Причина  
 Производный тип объявляет метод с таким же именем и числом параметров, как у одного из базовых методов; один или несколько параметров являются базовым типом соответствующего параметра в базовом методе; остальные параметры имеют типы, идентичные соответствующим параметрам в базовом методе.  
  
## Описание правила  
 Метод в базовом типе скрыт методом с таким же именем в производном типе. Подпись параметра производного метода отличается только типами, которые являются более слабыми, чем соответствующие типы в подписи параметра базового типа.  
  
## Устранение нарушений  
 Чтобы устранить нарушение этого правила, удалите или переименуйте метод или измените подпись параметра, чтобы метод не скрывал базовый метод.  
  
## Отключение предупреждений  
 Для этого правила отключать вывод предупреждений не следует.  
  
## Пример  
 В следующем примере демонстрируется метод, нарушающий это правило.  
  
 [!code-cs[FxCop.Design.HideBaseMethod#1](../code-quality/codesnippet/CSharp/ca1061-do-not-hide-base-class-methods_1.cs)]