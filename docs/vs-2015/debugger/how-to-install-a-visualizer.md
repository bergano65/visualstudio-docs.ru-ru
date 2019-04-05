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
ms.openlocfilehash: 1a75386844e3653a4dbf791980737f8d339072c4
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58979290"
---
# <a name="how-to-install-a-visualizer"></a>Практическое руководство. установку визуализатора
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

После создания визуализатора необходимо установить его так, чтобы он стал доступен в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Установка визуализатора — это простой процесс.  
  
> [!NOTE]
>  В **Store** приложений, только стандартные текстовые визуализаторы HTML, XML и JSON поддерживаются. Пользовательские визуализаторы (то есть, созданные пользователем) не поддерживаются.  
  
### <a name="to-install-a-visualizer"></a>Установка визуализатора  
  
1.  Найдите библиотеку DLL, содержащую построенный визуализатор.  
  
2.  Скопируйте библиотеку DLL в одно из следующих мест:  
  
    -   *VisualStudioInstallPath* `\Common7\Packages\Debugger\Visualizers`  
  
    -   `My Documents\` *VisualStudioVersion* `\Visualizers`  
  
3.  Если нужно использовать визуализатор управляемого кода для удаленной отладки, скопируйте DLL по тому же пути на удаленном компьютере.  
  
4.  Перезапустите сеанс отладки.  
  
## <a name="see-also"></a>См. также  
 [Создание настраиваемых визуализаторов](../debugger/create-custom-visualizers-of-data.md)   
 [Практическое руководство. Написание визуализатора](../debugger/how-to-write-a-visualizer.md)
