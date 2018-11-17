---
title: PROFILE_CURRENTID | Документы Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- PROFILE_CURRENTID
ms.assetid: 55ccf665-a05e-48c3-adf7-7714c0a9aaef
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f8e39234d9767be0cfb1305d25d107324ee073e7
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51792844"
---
# <a name="profilecurrentid"></a>PROFILE_CURRENTID
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Параметр PROFILE_CURRENTID возвращает псевдотокен для идентификатора потока или идентификатора процесса в вызове функций NameProfile, StartProfile, StopProfile, SuspendProfile и ResumeProfile. Этот параметр предписывает функции выполнять действия в текущем потоке или процессе, а не в специально указанном потоке или процессе.  
  
## <a name="example"></a>Пример  
 PROFILE_CURRENTID определяется в файле VSPerf.h следующим образом:  
  
```  
static const unsigned int PROFILE_CURRENTID = (unsigned int)-1;  
```  
  
## <a name="example"></a>Пример  
 В приведенном ниже примере демонстрируется использование параметра PROFILE_CURRENTID. В этом примере PROFILE_CURRENTID передается как параметр в вызове функции [StartProfile](../profiling/startprofile.md) для определения текущего потока.  
  
```  
void ExerciseProfileCurrentID()  
{  
    // Declare ProfileOperationResult enumeration   
    // to hold return value of a call to StartProfile.  
    PROFILE_COMMAND_STATUS profileResult;  
  
    // Variables used to print output.  
    HRESULT hResult;  
    TCHAR tchBuffer[256];  
  
    profileResult = StartProfile(  
        PROFILE_GLOBALLEVEL,  
        PROFILE_CURRENTID);  
  
    // Format and print result.  
    LPCTSTR pszFormat = TEXT("%s %d.\0");  
    TCHAR* pszTxt = TEXT("StartProfile returned");  
    hResult = StringCchPrintf(tchBuffer, 256, pszFormat,   
        pszTxt, profileResult);  
  
#ifdef DEBUG  
    OutputDebugString(tchBuffer);  
#endif  
}  
```  
  
## <a name="see-also"></a>См. также  
 [Справочник по API-интерфейсам профилировщика Visual Studio (машинный код)](../profiling/visual-studio-profiler-api-reference-native.md)   
 [NameProfile](../profiling/nameprofile.md)   
 [ResumeProfile](../profiling/resumeprofile.md)   
 [StartProfile](../profiling/startprofile.md)   
 [StopProfile](../profiling/stopprofile.md)   
 [SuspendProfile](../profiling/suspendprofile.md)



