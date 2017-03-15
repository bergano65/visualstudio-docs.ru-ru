---
title: "CA1806: не игнорируйте результаты метода | Microsoft Docs"
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
  - "CA1806"
  - "DoNotIgnoreMethodResults"
helpviewer_keywords: 
  - "CA1806"
  - "DoNotIgnoreMethodResults"
ms.assetid: fd805687-0817-481e-804e-b62cfb3b1076
caps.latest.revision: 27
caps.handback.revision: 27
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1806: не игнорируйте результаты метода
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotIgnoreMethodResults|  
|CheckId|CA1806|  
|Категория|Microsoft.Usage|  
|Критическое изменение|Не критическое|  
  
## Причина  
 Это предупреждение может возникать по нескольким причинам.  
  
-   Создается новый объект, который нигде не используется.  
  
-   Вызывается метод, который создает и возвращает новую строку, однако эта строка нигде не используется.  
  
-   Метод COM или P\/Invoke возвращает значение HRESULT или код ошибки, который никогда не используется.  Описание правила  
  
 Ненужное создание объекта и связанная с ним сборка мусора для неиспользуемого объекта понижает производительность.  
  
 Строки невозможно изменить, и такие методы как String.ToUpper возвращают новый экземпляр строки, а не изменяют экземпляр строки в вызывающем методе.  
  
 Игнорирование HRESULT или кода ошибки может привести к непредвиденному поведению в состоянии ошибки или к нехватке ресурсов.  
  
## Устранение нарушений  
 Если метод А создает новый экземпляр объекта В, который никогда не используется, передайте этот экземпляр в качестве аргумента другому методу или присвойте экземпляр переменной.  Если не требуется создавать объект, удалите его; или  
  
 Если метод A вызывает метод B, но не использует новый экземпляр строки, возвращаемый методом B.  Передайте этот экземпляр другому методу в качестве аргумента, присвойте экземпляр переменной.  Или удалите вызов, если он не нужен.  
  
 – или –  
  
 Если метод A вызывает метод B, но не использует значение HRESULT или код ошибки, возвращаемый методом B.  Используйте результат в условном операторе, присвойте его переменной или передайте его в качестве аргумента другому методу.  
  
## Отключение предупреждений  
 Предупреждения о нарушении данного правила можно отключить только в том случае, если создание объекта необходимо для какой\-либо цели.  
  
## Пример  
 В следующем примере показан класс, игнорирующий результат вызова метода String.Trim.  
  
 [!CODE [FxCop.Usage.DoNotIgnoreMethodResults#1](FxCop.Usage.DoNotIgnoreMethodResults#1)]  
  
## Пример  
 В следующем примере предыдущее нарушение устраняется присвоением результата метода String.Trim переменной, для которой он вызывался.  
  
 [!CODE [FxCop.Usage.DoNotIgnoreMethodResults2#1](FxCop.Usage.DoNotIgnoreMethodResults2#1)]  
  
## Пример  
 В следующем примере показан метод, который не использует создаваемый им объект.  
  
> [!NOTE]
>  Это нарушение нельзя воспроизвести в Visual Basic.  
  
 [!code-cs[FxCop.Usage.DoNotIgnoreMethodResults3#1](../code-quality/codesnippet/CSharp/ca1806-do-not-ignore-method-results_1.cs)]
 [!code-vb[FxCop.Usage.DoNotIgnoreMethodResults3#1](../code-quality/codesnippet/VisualBasic/ca1806-do-not-ignore-method-results_1.vb)]
 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults3#1](../code-quality/codesnippet/CPP/ca1806-do-not-ignore-method-results_1.cpp)]  
  
## Пример  
 В следующем примере предыдущее нарушение устраняется посредством удаления ненужного создания объекта.  
  
 [!code-cs[FxCop.Usage.DoNotIgnoreMethodResults4#1](../code-quality/codesnippet/CSharp/ca1806-do-not-ignore-method-results_2.cs)]
 [!code-vb[FxCop.Usage.DoNotIgnoreMethodResults4#1](../code-quality/codesnippet/VisualBasic/ca1806-do-not-ignore-method-results_2.vb)]
 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults4#1](../code-quality/codesnippet/CPP/ca1806-do-not-ignore-method-results_2.cpp)]  
  
## Пример  
 В следующем примере показан метод, игнорирующий код ошибки, который возвращается собственным методом GetShortPathName.  
  
 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults5#1](../code-quality/codesnippet/CPP/ca1806-do-not-ignore-method-results_3.cpp)]
 [!code-cs[FxCop.Usage.DoNotIgnoreMethodResults5#1](../code-quality/codesnippet/CSharp/ca1806-do-not-ignore-method-results_3.cs)]  
  
## Пример  
 В следующем примере предыдущее нарушение устраняется посредством проверки кода ошибки и создания исключения при сбое вызова.  
  
 [!code-cs[FxCop.Usage.DoNotIgnoreMethodResults6#1](../code-quality/codesnippet/CSharp/ca1806-do-not-ignore-method-results_4.cs)]
 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults6#1](../code-quality/codesnippet/CPP/ca1806-do-not-ignore-method-results_4.cpp)]