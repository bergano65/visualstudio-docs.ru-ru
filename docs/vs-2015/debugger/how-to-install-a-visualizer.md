---
title: Практическое руководство. Установка визуализатора | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, visualizers
- visualizers, installing
ms.assetid: 3310ef43-515c-4d97-b0f9-51047247d3da
caps.latest.revision: 29
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5726cea8b2e81c53b5f3fff963357946f26b199f
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63438229"
---
# <a name="how-to-install-a-visualizer"></a>Практическое руководство. установку визуализатора
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

После создания визуализатора необходимо установить его так, чтобы он стал доступен в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Установка визуализатора — это простой процесс.  
  
> [!NOTE]
> В **Store** приложений, только стандартные текстовые визуализаторы HTML, XML и JSON поддерживаются. Пользовательские визуализаторы (то есть, созданные пользователем) не поддерживаются.  
  
### <a name="to-install-a-visualizer"></a>Установка визуализатора  
  
1. Найдите библиотеку DLL, содержащую построенный визуализатор.  
  
2. Скопируйте библиотеку DLL в одно из следующих мест:  
  
    - *VisualStudioInstallPath* `\Common7\Packages\Debugger\Visualizers`  
  
    - `My Documents\` *VisualStudioVersion* `\Visualizers`  
  
3. Если нужно использовать визуализатор управляемого кода для удаленной отладки, скопируйте DLL по тому же пути на удаленном компьютере.  
  
4. Перезапустите сеанс отладки.  
  
## <a name="see-also"></a>См. также  
 [Создание настраиваемых визуализаторов](../debugger/create-custom-visualizers-of-data.md)   
 [Практическое руководство. Написание визуализатора](../debugger/how-to-write-a-visualizer.md)
