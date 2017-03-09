---
title: "Предварительные условия для развертывания 64-разрядных приложений | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "64-разрядные [Visual Studio]"
  - "64-разрядные приложения [Visual Studio]"
  - "программирование 64-разрядных приложений [Visual Studio]"
  - "развертывание приложений [Visual Studio], 64-разрядные"
ms.assetid: 87399e20-5510-41e4-b5b7-4a87c5773f21
caps.latest.revision: 23
caps.handback.revision: 23
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Предварительные условия для развертывания 64-разрядных приложений
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Развертывание приложений ClickOnce поддерживает установку приложений на 64\-разрядные платформы.  Целевыми платформами являются **x86** для 32\-разрядных платформ, **x64** для машин, поддерживающих наборы инструкций AMD64 и EM64T, а также **Itanium** для 64\-разрядного процессора Itanium.  
  
## Предварительные требования  
 В следующей таблице перечислены распространяемые компоненты, которые можно использовать в качестве необходимых компонентов для установки 64\-разрядных приложений.  
  
 Если вы выбрали необходимый компонент, не включающий 64\-разрядные элементы, система выдаст предупреждение о том, что выбранные пакеты недоступны для 64\-разрядных платформ.  
  
|Распространяемые компоненты|Поддержка x64|Поддержка IA64|  
|---------------------------------|-------------------|--------------------|  
|[!INCLUDE[vsto_runtime](../deployment/includes/vsto_runtime_md.md)]|Да|Нет|  
|Библиотеки среды выполнения Visual C\+\+ 2010 \(IA64\)|Нет|Да|  
|Библиотеки среды выполнения Visual C\+\+ 2010 \(x64\)|Да|Нет|  
|Microsoft .NET Framework 4 \(x86 и x64\)|Да||  
|Клиентский профиль Microsoft .NET Framework 4 \(x86 и x64\)|Да||  
  
## См. также  
 [Развертывание приложений, служб и компонентов](../deployment/deploying-applications-services-and-components.md)   
 [Практическое руководство. Установка необходимых компонентов при помощи ClickOnce\-приложения](../Topic/How%20to:%20Install%20Prerequisites%20with%20a%20ClickOnce%20Application.md)   
 [64\-разрядные приложения](../Topic/64-bit%20Applications.md)