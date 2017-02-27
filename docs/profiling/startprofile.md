---
title: "StartProfile | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "StartProfile"
ms.assetid: 1761311d-c9d5-48f5-b1f8-b3605829940a
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# StartProfile
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Функция `StartProfile` устанавливает для счетчика значение 1 \(on\) для указанного уровня профилирования.  
  
## Синтаксис  
  
```  
PROFILE_COMMAND_STATUS PROFILERAPI StartProfile(  
                        PROFILE_CONTROL_LEVEL Level,   
                        unsigned int dwId);  
```  
  
#### Параметры  
 `Level`  
  
 Указывает уровень профилирования, к которому можно применить сбор данных о производительности.  Для указания одного из трех уровней, к которому можно применить сбор данных о производительности, следует использовать следующие перечислители **PROFILE\_CONTROL\_LEVEL**.  
  
|Enumerator|Описание|  
|----------------|--------------|  
|PROFILE\_GLOBALLEVEL|Установка глобального уровня оказывает влияние на все процессы и потоки при выполнении профилирования.|  
|PROFILE\_PROCESSLEVEL|Установка уровня процесса оказывает влияние на все потоки, являющиеся частью указанного процесса.|  
|PROFILE\_THREADLEVEL|Установка уровня профилирования потока влияет на заданный поток.|  
  
 `dwId`  
  
 Идентификатор процесса или потока, созданный системой.  
  
## Значение свойства, возвращаемое значение  
 Функция указывает на успешное выполнение или сбой посредством перечисления **PROFILE\_COMMAND\_STATUS**.  Ниже перечислены возможные возвращаемые значения.  
  
|Enumerator|Описание|  
|----------------|--------------|  
|PROFILE\_ERROR\_ID\_NOEXIST|Идентификатор элемента профилирования не существует.|  
|PROFILE\_ERROR\_LEVEL\_NOEXIST|Заданный уровень профилирования не существует.|  
|PROFILE\_ERROR\_MODE\_NEVER|При вызове функции для режима профилирования было задано значение NEVER.|  
|PROFILE\_ERROR\_NOT\_YET\_IMPLEMENTED|Вызов функции профилирования, уровень профилирования или сочетание вызова и уровня пока не реализованы.|  
|PROFILE\_OK|Вызов выполнен успешно.|  
  
## Заметки  
 Функции StartProfile и StopProfile управляют состоянием начала\/остановки для уровня профилирования.  Значение по умолчанию Start\/Stop равно 1.  Начальное значение можно изменить в реестре.  Каждый вызов StartProfile устанавливает счетчик Пуск\/Остановка в 1; каждый вызов StopProfile устанавливает Пуск\/Остановка в 0.  
  
 Если значение счетчика Пуск\/Остановка больше 0, состояние Пуск\/Остановка для уровня включено.  Если это значение меньше или равно 0, состояние Пуск\/Остановка выключено.  
  
 Если Пуск\/Остановка, и Пауза\/Возобновление включены, состояние профилирования для данного уровня включено.\<\/para\>  Для профилируемого потока состояния глобального уровня, уровня процесса и потока должны быть равны значению ON.  
  
## Эквивалент в .NET Framework  
 Microsoft.VisualStudio.Profiler.dll  
  
## Сведения о функции  
 Заголовок: объявлен в файле VSPerf.h.  
  
 Импортируемая библиотека: VSPerf.lib  
  
## Пример  
 В следующем примере демонстрируется использование функции StartProfile.  
  
```  
void ExerciseStartProfile()  
{  
    // StartProfile and StopProfile control the  
    // Start/Stop state for the profiling level.   
    // The default initial value of Start/Stop is 1.   
    // The initial value can be changed in the registry.   
    // Each call to StartProfile sets Start/Stop to 1;   
    // each call to StopProfile sets it to 0.   
  
    // Variables used to print output.  
    HRESULT hResult;  
    TCHAR tchBuffer[256];  
  
    // Declare enumeration to hold return value of   
    // the call to StartProfile.  
    PROFILE_COMMAND_STATUS profileResult;  
  
    profileResult = StartProfile(  
        PROFILE_THREADLEVEL,  
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
  
## См. также  
 [Справочник по API\-интерфейсам профилировщика Visual Studio \(машинный код\)](../profiling/visual-studio-profiler-api-reference-native.md)