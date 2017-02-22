---
title: "Языки нейтральных ресурсов для локализации | Microsoft Docs"
ms.custom: ""
ms.date: "12/08/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "язык и региональные параметры, обнаружение ресурсов"
  - "глобализация [Visual Studio], ресурсы"
  - "локализация [Visual Studio], ресурсы"
  - "нейтральные ресурсы"
  - "NeutralResourcesLanguageAttribute - класс"
  - "ресурсы [Visual Studio], система резервного использования"
ms.assetid: ef064995-3b84-4698-a708-9689b7723533
caps.latest.revision: 8
caps.handback.revision: 8
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Языки нейтральных ресурсов для локализации
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Класс <xref:System.Resources.NeutralResourcesLanguageAttribute> определяет язык и региональные параметры ресурсов, включаемых в основную сборку.  Этот атрибут применяется для повышения производительности, чтобы объект <xref:System.Resources.ResourceManager> не искал ресурсы, включенные в основную сборку.  
  
 Следующий фрагмент кода иллюстрирует задание языка нейтральных ресурсов.  Этот код можно поместить в скрипт построения, в файл AssemblyInfo.vb или AssemblyInfo.cs.  
  
```vb#  
' Set neutral resources language for assembly.  
<Assembly: NeutralResourcesLanguageAttribute("en")>  
  
```  
  
```c#  
// Set neutral resources language for assembly.  
[assembly: NeutralResourcesLanguageAttribute("en")]  
```  
  
## См. также  
 <xref:System.Resources.ResourceManager>   
 [Знакомство с международными приложениями на платформе .NET Framework](../ide/introduction-to-international-applications-based-on-the-dotnet-framework.md)   
 [Иерархическая организация ресурсов для локализации](../ide/hierarchical-organization-of-resources-for-localization.md)   
 [Локализация приложений](../ide/localizing-applications.md)   
 [Глобализация и локализация приложений](../ide/globalizing-and-localizing-applications.md)