---
title: Платформа компиляторов .NET (&quot;Roslyn&quot;) расширяемости | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 564201b3-1e18-4b88-b615-42c2f57f3fe8
caps.latest.revision: 5
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: fba277731444a294f276f43cc67b098039f4a64f
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58979553"
---
# <a name="net-compiler-platform-quotroslynquot-extensibility"></a>Расширяемость платформы компилятора .NET (&quot;Roslyn&quot;)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Основная миссия платформы компилятора .NET («Roslyn») открывая компиляторы C# и Visual Basic и позволяя средствам и разработчикам совместно использовать в компиляторах ценные сведения о программах. Средства анализа кода повышение качества кода и кода генераторы шаблона можно найти в построение приложения. Как средства получать аналитическую, им требуется доступ к больше и больше из кода глубокого знания, обладают исключительно компиляторами. А не непрозрачные преобразователи (исходный код в и объектный код out), компиляторы Roslyn предоставляют API, которые можно использовать для задач, связанных с кодом, в средствах и приложениях.  
  
 Лучше всего то, что компиляторы Roslyn, их интерфейсы API, примеры и пошаговые руководства и реальные средства, созданная на основе этих API являются полностью открытым исходным кодом в [github.com/dotnet/roslyn](https://github.com/dotnet/Roslyn). Перейдите на сайт OSS, Дополнительные сведения и приступить к работе с Roslyn. Вы найдете ссылки для получения последних C# и VB функций, которые можно использовать в качестве конечного пользователя, а также ссылки для начала работы как средство построитель, используя API Roslyn.  
  
## <a name="see-also"></a>См. также  
 [Начало работы с анализаторами Roslyn](../extensibility/getting-started-with-roslyn-analyzers.md)
