---
title: Нейтральные языки ресурсов для локализации | Документы Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- localization [Visual Studio], resources
- NeutralResourcesLanguageAttribute class
- globalization [Visual Studio], resources
- resources [Visual Studio], fallback system
- culture, locating resources
- neutral resources
ms.assetid: ef064995-3b84-4698-a708-9689b7723533
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a9470718743e506a7a8cd5ad03d9b6f69b1d5477
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47559268"
---
# <a name="neutral-resources-languages-for-localization"></a>Языки нейтральных ресурсов для локализации
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Класс <xref:System.Resources.NeutralResourcesLanguageAttribute> определяет, какой язык и какие региональные параметры ресурсов включаются в основную сборку. Этот атрибут используется для повышения производительности, чтобы объект <xref:System.Resources.ResourceManager> не искал ресурсы, включенные в основную сборку.  
  
 В следующем примере кода показано, как задать нейтральный язык ресурсов. Код можно поместить в скрипт сборки либо в файл AssemblyInfo.vb или AssemblyInfo.cs.  
  
```vb  
' Set neutral resources language for assembly.  
<Assembly: NeutralResourcesLanguageAttribute("en")>  
  
```  
  
```csharp  
// Set neutral resources language for assembly.  
[assembly: NeutralResourcesLanguageAttribute("en")]  
```  
  
## <a name="see-also"></a>См. также  
 <xref:System.Resources.ResourceManager>   
 [Знакомство с международными приложениями на платформе .NET Framework](../ide/introduction-to-international-applications-based-on-the-dotnet-framework.md)   
 [Иерархическая организация ресурсов для локализации](../ide/hierarchical-organization-of-resources-for-localization.md)   
 [Локализация приложений](../ide/localizing-applications.md)   
 [Глобализация и локализация приложений](../ide/globalizing-and-localizing-applications.md)

