---
title: Справочник по API-интерфейсам профилировщика Visual Studio (машинный код) | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- performance tools, API
- Profiler, API
ms.assetid: a0c3be92-c263-4678-9fb9-bafead3bd5f5
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: d79399ebea9fd5dedd645b148910d6a4ced47902
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
---
# <a name="visual-studio-profiler-api-reference-native"></a>Справочник по API-интерфейсам профилировщика Visual Studio (машинный код)
API-интерфейсы профилировщика Visual Studio позволяют программно управлять объемом собираемых данных и вставлять метки времени и метки профилей во время профилирования. Чтобы использовать собственный API, включите файл заголовка VSPerf.h и добавьте файл VSPerf.lib в свой проект.  
  
> [!NOTE]
>  По умолчанию файлы VSPerf.h и VSPerf.lib расположены в папке с именем PerfSDK. Например, это может быть каталог \<диск>:\Program Files (x86)\Microsoft Visual Studio 14.0\Team Tools\Performance Tools\PerfSDK.  
  
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
