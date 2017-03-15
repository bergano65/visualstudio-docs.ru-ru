---
title: "CommentMarkProfile | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "CommentMarkProfile"
  - "CommentMarkProfileA"
ms.assetid: 33ccff45-c33a-4672-b41f-5b317b848cd1
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# CommentMarkProfile
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Функция `CommentMarkProfile` вставляет числовую метку и текстовую строку в VSP\-файл.  Чтобы вставить метку и комментарий, необходимо включить профилирование для потока, содержащего функцию `CommentMarkProfile`.  
  
## Синтаксис  
  
```  
PROFILE_COMMAND_STATUS PROFILERAPI CommentMarkProfile(  
                                   long lMarker,   
                                   LPCTSTR szComment);  
```  
  
#### Параметры  
 `lMarker`  
  
 Вставляемая числовая метка.  Метка должна быть больше или равна нулю \(0\).  
  
 `szComment`  
  
 Указатель на вставляемую текстовую строку.  Длина строки не должна превышать 256 знаков, включая токен конца строки NULL.  
  
## Значение свойства, возвращаемое значение  
 Функция указывает на успешное выполнение или сбой посредством перечисления **PROFILE\_COMMAND\_STATUS**.  Ниже перечислены возможные возвращаемые значения.  
  
|Enumerator|Описание|  
|----------------|--------------|  
|MARK\_ERROR\_MARKER\_RESERVED|Параметр меньше или равен нулю.  Эти значения зарезервированы.  Метка и комментарий не записываются.|  
|MARK\_ERROR\_MODE\_NEVER|При вызове функции для режима профилирования было задано значение NEVER.  Метка и комментарий не записываются.|  
|MARK\_ERROR\_MODE\_OFF|При вызове функции для режима профилирования было задано значение OFF.  Метка и комментарий не записываются.|  
|MARK\_ERROR\_NO\_SUPPORT|В данном контексте поддержка меток отсутствует.  Метка и комментарий не записываются.|  
|MARK\_ERROR\_OUTOFMEMORY|Недостаточно памяти для записи события.  Метка и комментарий не записываются.|  
|MARK\_TEXTTOOLONG|Длина строки превышает максимальный предел \(256 знаков\).  Строка комментария усекается, а метка и комментарий записываются.|  
|MARK\_OK|При успешном выполнении возвращается значение MARK\_OK.|  
  
## Заметки  
 Профилирования для потока, который содержит функцию меток профилирования, должно быть включено, если метки и комментарии вставляются при помощи команды VSInstr Mark или функций \(CommentMarkAtProfile, CommentMarkProfile или MarkProfile\).  
  
 Метки профилирования имеют глобальную область видимости.  Например, метка профиля, вставленная в поток, может использоваться для отметки начала и конца сегмента данных в любом потоке, определенном в .VSP\-файле.  
  
> [!IMPORTANT]
>  Метод CommentMarkProfile должен использоваться только при профилировании с инструментированием.  
  
## Эквивалент в .NET Framework  
 Microsoft.VisualStudio.Profiler.dll  
  
## Сведения о функции  
  
|||  
|-|-|  
|**Заголовок**|Include VSPerf.h|  
|**Библиотека**|Use VSPerf.lib|  
|**Юникод**|Функция реализована как `CommentMarkProfileW` \(Юникод\) и `CommentMarkProfileA` \(ANSI\).|  
  
## Пример  
 В следующем коде демонстрируется вызов функции CommentMarkProfile.  Предполагается, что в этом примере используется строковый макрос Win32 и параметры компилятора для Юникода, чтобы определить, вызывается ли в коде функция, поддерживающая кодировку [!INCLUDE[vcpransi](../profiling/includes/vcpransi_md.md)].  
  
```  
void ExerciseCommentMarkProfile()  
{  
    // Declare and initalize variables to pass to   
    // CommentMarkProfile.  The values of these   
    // parameters are assigned based on the needs   
    // of the code; and for the sake of simplicity  
    // in this example, the variables are assigned  
    // arbitrary values.  
    long markId = 01;  
    TCHAR * markText = TEXT("Exercising CommentMarkProfile...");  
  
    // Variables used to print output.  
    HRESULT hResult;  
    TCHAR tchBuffer[256];  
  
    // Declare MarkOperationResult Enumerator.    
    // Holds return value from call to CommentMarkProfile.  
    PROFILE_COMMAND_STATUS markResult;  
  
    markResult = CommentMarkProfile(  
        markId,  
        markText);  
  
    // Format and print result.  
    LPCTSTR pszFormat = TEXT("%s %d.\0");  
    TCHAR* pszTxt = TEXT("CommentMarkProfile returned");  
    hResult = StringCchPrintf(tchBuffer, 256, pszFormat,   
        pszTxt, markResult);  
  
#ifdef DEBUG  
    OutputDebugString(tchBuffer);  
#endif  
}  
```  
  
## См. также  
 [Справочник по API\-интерфейсам профилировщика Visual Studio \(машинный код\)](../profiling/visual-studio-profiler-api-reference-native.md)