---
title: "Платформа компиляторов .NET (&quot;Roslyn&quot;) расширяемости | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 564201b3-1e18-4b88-b615-42c2f57f3fe8
caps.latest.revision: "4"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1f9811440146e1d758158a64fd227ba0a2c2e1e4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="net-compiler-platform-quotroslynquot-extensibility"></a>Платформа компиляторов .NET (&quot;Roslyn&quot;) расширяемости
Критически core платформы компилятора .NET («Roslyn») открыл компиляторы C# и Visual Basic и позволяя средств и разработчикам использовать в компиляторах подробные сведения о программах. Средства анализа кода улучшение качества кода и кода поможет генераторы построение приложения. Как лучше понимать средств, они иметь доступа из кода глубокого знания, обладают только компиляторы и дополнительные. А не непрозрачные трансляторы (исходный код в и объектный код out), компиляторы Roslyn предоставляют интерфейсы API, которые можно использовать для задач, связанных с кодом, средств и приложений.  
  
 Лучше всего то, что компиляторы Roslyn, их интерфейсов API, образцы и пошаговые руководства и реальные средства, построена на базе эти API-интерфейсы являются полностью открытым исходным кодом на [github.com/dotnet/roslyn](https://github.com/dotnet/Roslyn). Перейдите на сайт операционные системы для получения дополнительных сведений и приступить к работе с помощью Roslyn. Вы найдете ссылки для получения последних C# и VB функции, которые можно использовать в качестве конечного пользователя, а также ссылки, чтобы приступить к работе, где работает построитель средство, используя API Roslyn.  
  
## <a name="see-also"></a>См. также  
 [Начало работы с анализаторами Roslyn](../extensibility/getting-started-with-roslyn-analyzers.md)