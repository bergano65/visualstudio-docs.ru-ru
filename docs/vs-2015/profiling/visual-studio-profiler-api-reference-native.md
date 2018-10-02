---
title: Справочник по API-интерфейсам профилировщика Visual Studio (машинный код) | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- performance tools, API
- Profiler, API
ms.assetid: a0c3be92-c263-4678-9fb9-bafead3bd5f5
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 74a66580cf7fb0b5fb998442fe59a3cb601da437
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47560238"
---
# <a name="visual-studio-profiler-api-reference-native"></a>Справочник по API-интерфейсам профилировщика Visual Studio (машинный код)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [Profiler API Справочник по Visual Studio (машинный код)](https://docs.microsoft.com/visualstudio/profiling/visual-studio-profiler-api-reference-native).  
  
API-интерфейсы профилировщика Visual Studio позволяют программно управлять объемом собираемых данных и вставлять метки времени и метки профилей во время профилирования. Чтобы использовать собственный API, включите файл заголовка VSPerf.h и добавьте файл VSPerf.lib в свой проект.  
  
> [!NOTE]
>  По умолчанию файлы VSPerf.h и VSPerf.lib расположены в папке \< <диск>:\Program Files\Microsoft Visual Studio 9\Team Tools\Performance Tools\PerfSDK.  
  
## <a name="in-this-section"></a>В этом разделе  
 [CommentMarkAtProfile](../profiling/commentmarkatprofile.md)  
  
 [CommentMarkProfile](../profiling/commentmarkprofile.md)  
  
 [MarkProfile](../profiling/markprofile.md)  
  
 [NameProfile](../profiling/nameprofile.md)  
  
 [ResumeProfile](../profiling/resumeprofile.md)  
  
 [StartProfile](../profiling/startprofile.md)  
  
 [StopProfile](../profiling/stopprofile.md)  
  
 [SuspendProfile](../profiling/suspendprofile.md)  
  
 [PROFILE_CURRENTID](../profiling/profile-currentid.md)  
  
## <a name="see-also"></a>См. также  
 [Интерфейсы API средств профилирования](../profiling/profiling-tools-apis.md)   
 [Пошаговое руководство. Использование API-интерфейсов профилировщика](../profiling/walkthrough-using-profiler-apis.md)



