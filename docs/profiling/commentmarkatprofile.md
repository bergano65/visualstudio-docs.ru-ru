---
title: "CommentMarkAtProfile | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "CommentMarkAtProfile"
  - "CommentMarkAtProfileA"
ms.assetid: 04294ca3-bf9c-4c76-86f1-898c2140de27
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# CommentMarkAtProfile
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Метод `CommentMarkAtProfile` вставляет значение отметки времени, числовую метку и строку комментария в VSP\-файл.  Значение отметки времени можно использовать для синхронизации внешних событий.  Чтобы вставить метку и комментарий, необходимо включить профилирование для потока, содержащего функцию CommentMarkAtProfile.  
  
## Синтаксис  
  
```  
PROFILE_COMMAND_STATUS PROFILERAPI CommentMarkAtProfile (  
                                   __int64 dnTimestamp,  
                                   long lMarker,  
                                   LPCTSTR szComment);  
```  
  
#### Параметры  
 `dnTimestamp`  
  
 64\-разрядное целое число, представляющее значение отметки времени.  
  
 `lMarker`  
  
 Числовая метка для вставки.  Метка должна быть больше или равна нулю \(0\).  
  
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
 Состояние профилирования для потока, который содержит функцию метки профиля, должно быть включено, если метки и комментарии вставлены при помощи команды Mark или функций API \(CommentMarkAtProfile, CommentMarkProfile или MarkProfile\).  Метки профилирования имеют глобальную область видимости.  Например, метка профиля, вставленная в поток, может использоваться для отметки начала и конца сегмента данных в любом потоке, определенном в .VSP\-файле.  
  
> [!IMPORTANT]
>  Метод CommentMarkAtProfile должен использоваться только при профилировании с инструментированием.  
  
## Эквивалент в .NET Framework  
 Microsoft.VisualStudio.Profiler.dll  
  
## Сведения о функции  
  
|||  
|-|-|  
|**Заголовок**|Include VSPerf.h|  
|**Библиотека**|Use VSPerf.lib|  
|**Юникод**|Функция реализована как CommentMarkAtProfileW \(Юникод\) и CommentMarkAtProfileA \(ANSI\).|  
  
## Пример  
 В следующем коде показан вызов универсальной функции CommentMarkAtProfile.  Предполагается, что в этом примере используется строковый макрос Win32 и параметры компилятора для кодировки ANSI, чтобы определить, вызывается ли в коде функция, поддерживающая кодировку ANSI.  
  
```  
void ExerciseCommentMarkAtProfile(void)  
{  
    // Declare and initalize variables to pass to   
    // CommentMarkAtProfile.  The values of these   
    // parameters are assigned based on the needs   
    // of the code; and for the sake of simplicity  
    // in this example, the variables are assigned  
    // arbitrary values.  
    int64 timeStamp = 0x1111;  
    long markId = 01;  
    TCHAR * markText = TEXT("Exercising CommentMarkAtProfile...");  
  
    // Variables used to print output.  
    HRESULT hResult;  
    TCHAR tchBuffer[256];  
  
    // Declare MarkOperationResult Enumerator.    
    // Holds return value from call to CommentMarkAtProfile.  
    PROFILE_COMMAND_STATUS markResult;  
  
    markResult = CommentMarkAtProfile(  
        timeStamp,  
        markId,  
        markText);  
  
    // Format and print result.  
    LPCTSTR pszFormat = TEXT("%s %d.\0");  
    TCHAR* pszTxt = TEXT("CommentMarkAtProfile returned");  
    hResult = StringCchPrintf(tchBuffer, 256, pszFormat,   
    pszTxt, markResult);  
  
#ifdef DEBUG  
    OutputDebugString(tchBuffer);  
#endif  
}  
```  
  
## См. также  
 [Справочник по API\-интерфейсам профилировщика Visual Studio \(машинный код\)](../profiling/visual-studio-profiler-api-reference-native.md)