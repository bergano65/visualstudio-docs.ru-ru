---
title: Платформа компиляторов .NET (&quot;Roslyn&quot;) расширяемости | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 564201b3-1e18-4b88-b615-42c2f57f3fe8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c9272ea9de8156d2fd5709c4b9dba6ccdce9a33a
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51768701"
---
# <a name="net-compiler-platform-quotroslynquot-extensibility"></a>Платформа компиляторов .NET (&quot;Roslyn&quot;) расширяемости
Основная миссия платформы компилятора .NET («Roslyn») открывая компиляторы C# и Visual Basic и позволяя средствам и разработчикам совместно использовать в компиляторах ценные сведения о программах. Средства анализа кода повышение качества кода и кода генераторы шаблона можно найти в построение приложения. Как средства получать аналитическую, им требуется доступ к больше и больше из кода глубокого знания, обладают исключительно компиляторами. А не непрозрачные преобразователи (исходный код в и объектный код out), компиляторы Roslyn предоставляют API, которые можно использовать для задач, связанных с кодом, в средствах и приложениях.

 Лучше всего то, что компиляторы Roslyn, их интерфейсы API, примеры и пошаговые руководства и реальные средства, созданная на основе этих API являются полностью открытым исходным кодом в [github.com/dotnet/roslyn](https://github.com/dotnet/Roslyn). Перейдите на сайт OSS, Дополнительные сведения и приступить к работе с Roslyn. Вы найдете ссылки на последние сведения C# и возможности Visual Basic, которые можно использовать как конечного пользователя, а также ссылки, чтобы приступить к работе, как построитель средство, используя API Roslyn.

## <a name="see-also"></a>См. также
 [Начало работы с анализаторами Roslyn](../extensibility/getting-started-with-roslyn-analyzers.md)