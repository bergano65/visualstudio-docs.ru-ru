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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 85e0be0172f27732f8efeb882cbcde5b9c6aef3d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670389"
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

## <a name="see-also"></a>См. также:
 <xref:System.Resources.ResourceManager>[Общие сведения о международных приложениях на основе .NET Framework](../ide/introduction-to-international-applications-based-on-the-dotnet-framework.md) [иерархической организации ресурсов для локализации](../ide/hierarchical-organization-of-resources-for-localization.md) [приложений](../ide/localizing-applications.md) [Глобализация и локализация приложений](../ide/globalizing-and-localizing-applications.md)
