---
title: 'CA1061: Не следует скрывать методы базового класса | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- CA1061
- DoNotHideBaseClassMethods
helpviewer_keywords:
- DoNotHideBaseClassMethods
- CA1061
ms.assetid: 0bda9dc8-87b4-4038-ab9d-563298387466
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f3119a088c0dfa7a976a12f0c6abb45e409da8d2
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="ca1061-do-not-hide-base-class-methods"></a>CA1061: не следует скрывать методы базового класса
|||  
|-|-|  
|TypeName|DoNotHideBaseClassMethods|  
|CheckId|CA1061|  
|Категория|Microsoft.Design|  
|Критическое изменение|Критическое|  
  
## <a name="cause"></a>Причина  
 Производный тип объявляет метод с тем же именем и с количеством параметров, как один из базовых методов; один или несколько параметров является допустимым базовым типом соответствующего параметра в базовом методе; и все остальные параметры имеют типы, которые совпадают с соответствующими параметрами в базовый метод.  
  
## <a name="rule-description"></a>Описание правила  
 Метод в базовом типе скрыт методом с таким же именем в производном типе, если сигнатура параметра производного метода отличается только типами, которые являются более слабыми, чем соответствующие типы в сигнатуре параметра базового метода.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
 Чтобы устранить нарушение данного правила, удалите или переименуйте метод или измените подпись параметра, чтобы метод не скрывает базового метода.  
  
## <a name="when-to-suppress-warnings"></a>Отключение предупреждений  
 Для этого правила отключать вывод предупреждений не следует.  
  
## <a name="example"></a>Пример  
 В следующем примере показано метод, который нарушает правила.  
  
 [!code-csharp[FxCop.Design.HideBaseMethod#1](../code-quality/codesnippet/CSharp/ca1061-do-not-hide-base-class-methods_1.cs)]