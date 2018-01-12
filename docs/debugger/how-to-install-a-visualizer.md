---
title: "Как: Установка визуализатора | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "26"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: e9864a2a8f3f39e368ae1293b4b27fc0a8d9e056
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-install-a-visualizer"></a>Практическое руководство. Установка визуализатора
После создания визуализатора необходимо установить его так, чтобы он стал доступен в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Установка визуализатора — это простой процесс.  
  
> [!NOTE]
>  В приложениях UWP только стандартные текстовые визуализаторы HTML, XML и JSON поддерживаются. Пользовательские визуализаторы (то есть, созданные пользователем) не поддерживаются.  
  
### <a name="to-install-a-visualizer"></a>Установка визуализатора  
  
1.  Найдите библиотеку DLL, содержащую построенный визуализатор.  
  
2.  Скопируйте библиотеку DLL в одно из следующих мест:  
  
    -   *VisualStudioInstallPath*`\Common7\Packages\Debugger\Visualizers`  
  
    -   `My Documents\`*VisualStudioVersion*`\Visualizers`  
  
3.  Если нужно использовать визуализатор управляемого кода для удаленной отладки, скопируйте DLL по тому же пути на удаленном компьютере.  
  
4.  Перезапустите сеанс отладки.  
  
## <a name="see-also"></a>См. также  
 [Создание пользовательских визуализаторов](../debugger/create-custom-visualizers-of-data.md)   
 [Практическое руководство. Написание визуализатора](../debugger/how-to-write-a-visualizer.md)