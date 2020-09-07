---
title: Предупреждения о переносимости и взаимодействии
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.Portablityrules
- vs.codeanalysis.Interoperabilityrules
helpviewer_keywords:
- managed code analysis warnings, interoperability warnings, portability warnings
- portability warnings
- warnings, portability
- interoperability warnings
- warnings, interoperability
ms.assetid: 95de6eb3-40c4-4063-9f59-25cb70e3b2b3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 306c2477e6e5f731ed6dbf20b2cf4d03d4556467
ms.sourcegitcommit: 5caad925ca0b5d136416144a279e984836d8f28c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/07/2020
ms.locfileid: "89509917"
---
# <a name="portability-and-interoperability-warnings"></a>Предупреждения о переносимости и взаимодействии

Предупреждения переносимости поддерживают переносимость на разных платформах. Предупреждения взаимодействия поддерживают взаимодействие с клиентами COM.

## <a name="in-this-section"></a>в этом разделе

| Правило | Описание |
| - | - |
| [CA1401: методы P/Invoke не должны быть видимыми](../code-quality/ca1401.md) | Открытый или защищенный метод в открытом типе имеет атрибут System.Runtime.InteropServices.DllImportAttribute (также реализованное ключевым словом Declare в Visual Basic). Такие методы не следует делать видимыми. |
| [CA1417: не используйте `OutAttribute` в строковых параметрах для P/Invoke](../code-quality/ca1417.md) | Строковые параметры, передаваемые по значению, `OutAttribute` могут дестабилизировать среду выполнения, если строка является интернированной строкой. |