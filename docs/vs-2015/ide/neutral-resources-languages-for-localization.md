---
title: Нейтральные языки ресурсов для локализации | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: da39ed9373daaa1dbef21ad36931ce97ea1f1e1b
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "54764777"
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
  
## <a name="see-also"></a>См. также раздел  
 <xref:System.Resources.ResourceManager>   
 [Знакомство с международными приложениями на платформе .NET Framework](../ide/introduction-to-international-applications-based-on-the-dotnet-framework.md)   
 [Иерархическая организация ресурсов для локализации](../ide/hierarchical-organization-of-resources-for-localization.md)   
 [Локализация приложений](../ide/localizing-applications.md)   
 [Глобализация и локализация приложений](../ide/globalizing-and-localizing-applications.md)
