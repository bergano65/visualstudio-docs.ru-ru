---
title: '&quot;Расширяемость .NET Compiler Platform (Roslyn &quot; ) | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 564201b3-1e18-4b88-b615-42c2f57f3fe8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 62ceac6e2be8a0a84d82f6b86b685c7c8b20a182
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80712077"
---
# <a name="net-compiler-platform-quotroslynquot-extensibility"></a>&quot;Расширяемость .NET Compiler Platform (Roslyn &quot; )
Основной задачей .NET Compiler Platform ("Roslyn") является открытие компиляторов C# и Visual Basic и предоставление средствам и разработчикам возможности совместного использования в компиляторах с богатыми сведениями о программах. Средства анализа кода улучшают качество кода и помогают создавать генераторы кода в разработке приложений. По мере того как инструменты получают более широкие преимущества, им нужен доступ к более и более подробным знаниям кода, которые имеют только компиляторы. Вместо того чтобы делать непрозрачные трансляторы (исходный код в и исходящие объекты), компиляторы Roslyn предлагают интерфейсы API, которые можно использовать для задач, связанных с кодом, в средствах и приложениях.

 Лучшая часть состоит в том, что компиляторы Roslyn, их API-интерфейсы, примеры и пошаговые руководства, а также реальные средства, основанные на этих API, являются полностью открытыми источниками на [GitHub.com/DotNet/Roslyn](https://github.com/dotnet/Roslyn). Перейдите на сайт OSS, чтобы узнать больше и приступить к работе с Roslyn. Вы найдете ссылки для получения новейших функций C# и Visual Basic, которые можно использовать в качестве конечных пользователей, а также ссылки для начала работы в качестве построителя средств, использующего API-интерфейсы Roslyn.

## <a name="see-also"></a>См. также
- [Начало работы с анализаторами Roslyn](../extensibility/getting-started-with-roslyn-analyzers.md)
