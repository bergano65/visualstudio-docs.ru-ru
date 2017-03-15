---
title: "Событие &quot;&lt;имя_события1&gt;&quot; не может содержать реализацию события &quot;&lt;имя_события2&gt;&quot;, так как его делегируемый тип не соответствует делегируемому типу другого события, реализуемого событием &quot;&lt;имя_события1&gt;&quot; | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc31407"
  - "vbc31407"
helpviewer_keywords: 
  - "BC31407"
ms.assetid: 0b9ffddb-4759-438b-b569-beac7062e986
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Событие &quot;&lt;имя_события1&gt;&quot; не может содержать реализацию события &quot;&lt;имя_события2&gt;&quot;, так как его делегируемый тип не соответствует делегируемому типу другого события, реализуемого событием &quot;&lt;имя_события1&gt;&quot;
[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] не удается реализовать событие, так как его тип делегата не соответствует типу делегата другого события. Эта ошибка может возникнуть при определении нескольких событий в интерфейсе и последующей попытке их совместной реализации с использованием одного события. Событие может реализовывать два или более событий, только если все они объявлены с помощью синтаксиса `As` и указывают один и тот же тип делегата.  
  
 **Идентификатор ошибки:** BC31407  
  
### Исправление ошибки  
  
-   Реализуйте события по отдельности.  
  
## См. также  
 [События](/dotnet/visual-basic/programming-guide/language-features/events/events)