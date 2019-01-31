---
title: Как выполнить Установка визуализатора | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugger, visualizers
- visualizers, installing
ms.assetid: 3310ef43-515c-4d97-b0f9-51047247d3da
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6e2ff65e5d410295e9ce7fa0512588b68ca25e55
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54965540"
---
# <a name="how-to-install-a-visualizer"></a>Как выполнить установку визуализатора
После создания визуализатора необходимо установить его так, чтобы он стал доступен в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Установка визуализатора — это простой процесс.  
  
> [!NOTE]
>  В приложениях UWP только стандартные текстовые визуализаторы HTML, XML и JSON поддерживаются. Пользовательские визуализаторы (то есть, созданные пользователем) не поддерживаются.  
  
### <a name="to-install-a-visualizer"></a>Установка визуализатора  
  
1.  Найдите библиотеку DLL, содержащую построенный визуализатор.  
  
2.  Скопируйте библиотеку DLL в одно из следующих мест:  
  
    -   *VisualStudioInstallPath* `\Common7\Packages\Debugger\Visualizers`  
  
    -   `My Documents\` *VisualStudioVersion* `\Visualizers`  
  
3.  Если нужно использовать визуализатор управляемого кода для удаленной отладки, скопируйте DLL по тому же пути на удаленном компьютере.  
  
4.  Перезапустите сеанс отладки.  
  
## <a name="see-also"></a>См. также раздел  
 [Создание настраиваемых визуализаторов](../debugger/create-custom-visualizers-of-data.md)   
 [Практическое руководство. Написание визуализатора](/visualstudio/debugger/create-custom-visualizers-of-data)