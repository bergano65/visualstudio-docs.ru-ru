---
title: "Справочник по API-интерфейсам профилировщика Visual Studio (машинный код) | Документация Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- performance tools, API
- Profiler, API
ms.assetid: a0c3be92-c263-4678-9fb9-bafead3bd5f5
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: c9df048a49580f3526b48e29041ef3758722ed27
ms.openlocfilehash: 142df9fbf327ee8ebc39c3558ef1632a1bd23ae7
ms.contentlocale: ru-ru
ms.lasthandoff: 05/03/2017

---
# <a name="visual-studio-profiler-api-reference-native"></a>Справочник по API-интерфейсам профилировщика Visual Studio (машинный код)
API-интерфейсы профилировщика Visual Studio позволяют программно управлять объемом собираемых данных и вставлять метки времени и метки профилей во время профилирования. Чтобы использовать собственный API, включите файл заголовка VSPerf.h и добавьте файл VSPerf.lib в свой проект.  
  
> [!NOTE]
>  По умолчанию файлы VSPerf.h и VSPerf.lib расположены в папке с именем PerfSDK. Например, это может быть каталог \<диск>:\Program Files (x86)\Microsoft Visual Studio 14.0\Team Tools\Performance Tools\PerfSDK.  
  
## <a name="in-this-section"></a>Содержание  
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

