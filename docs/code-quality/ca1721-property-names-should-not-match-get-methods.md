---
title: "CA1721: имена свойств не должны совпадать с именами методов get | Microsoft Docs"
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
  - "CA1721"
  - "PropertyNamesShouldNotMatchGetMethods"
helpviewer_keywords: 
  - "CA1721"
  - "PropertyNamesShouldNotMatchGetMethods"
ms.assetid: 45a0e853-1f06-4688-af1b-cc634409e295
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1721: имена свойств не должны совпадать с именами методов get
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|PropertyNamesShouldNotMatchGetMethods|  
|CheckId|CA1721|  
|Категория|Microsoft.Naming|  
|Критическое изменение|Критическое изменение|  
  
## Причина  
 Имя открытого или защищенного члена начинается с "Get" и иным образом совпадает с именем открытого или защищенного свойства.  Например, тип содержит метод "GetColor", а свойство "Color" нарушает это правило.  
  
## Описание правила  
 Методы Get и свойства должны иметь имена, явно различающие их функции.  
  
 Соглашения об именах обеспечивают единообразие библиотек, предназначенных для выполнения в среде CLR.  Это позволяет сократить время обучения, необходимое для освоения новой библиотеки программного обеспечения, и укрепить уверенность клиента в том, что библиотека была разработана опытным разработчиком управляемого кода.  
  
## Устранение нарушений  
 Измените имя, чтобы оно не совпадало с именем метода с префиксом "Get".  
  
## Отключение предупреждений  
 Для этого правила отключать вывод предупреждений не следует.  
  
> [!NOTE]
>  Это предупреждение можно отключить, если метод Get вызван реализацией интерфейса IExtenderProvider.  
  
## Пример  
 В следующем примере показаны метод и свойство, нарушающие это правило.  
  
 [!CODE [FxCop.Naming.GetMethod#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Naming.GetMethod#1)]  
  
## Связанные правила  
 [CA1024: используйте свойства, если это уместно](../code-quality/ca1024-use-properties-where-appropriate.md)