---
title: Языки нейтральных ресурсов для локализации
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- localization [Visual Studio], resources
- NeutralResourcesLanguageAttribute class
- globalization [Visual Studio], resources
- resources [Visual Studio], fallback system
- culture, locating resources
- neutral resources
ms.assetid: ef064995-3b84-4698-a708-9689b7723533
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c1a671eefae23fb369cd7398efb7589764ebb46f
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2019
ms.locfileid: "55912876"
---
# <a name="neutral-resources-languages-for-localization"></a>Языки нейтральных ресурсов для локализации

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

- <xref:System.Resources.ResourceManager>
- [Знакомство с международными приложениями на платформе .NET Framework](../ide/introduction-to-international-applications-based-on-the-dotnet-framework.md)
- [Иерархическая организация ресурсов для локализации](../ide/hierarchical-organization-of-resources-for-localization.md)
- [Локализация приложений](../ide/localizing-applications.md)
- [Глобализация и локализация приложений](../ide/globalizing-and-localizing-applications.md)