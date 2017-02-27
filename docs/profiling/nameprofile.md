---
title: "NameProfile | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "NameProfile"
  - "NameProfileA"
ms.assetid: 1bb05441-c4ff-4323-9fef-f3924fba4430
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# NameProfile
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Функция `NameProfile` назначает строку указанному процессу или потоку.  
  
 API\-интерфейс NameProfile доступен только при профилировании с инструментированием.  API\-интерфейс NameProfile не поддерживается при профилировании с выборкой.  
  
## Синтаксис  
  
```  
PROFILE_COMMAND_STATUS PROFILERAPI NameProfile(  
                                   LPCTSTR pszName,   
                                   PROFILE_CONTROL_LEVEL Level,  
                                   unsigned int dwId);  
```  
  
#### Параметры  
 `pszName`  
  
 Имя элемента профилирования.  Ниже перечислены условия, при которых имя является недопустимым \(то есть функция NameProfileA возвращает значение NAME\_ERROR\_INVALID\_NAME\).  
  
-   Указатель, переданный в функцию NameProfileA, имеет значение NULL.  
  
-   Строковые данные параметра pszName начинаются с числа.  
  
-   Строковые данные параметра pszName начинаются с пробела.  
  
-   Строковые данные параметра pszName содержат любой из следующих знаков: ,;.\`~\!@\#$%^&\*\(\)\=\[\]{}&#124;\\?\/\<\>  
  
 `Level`  
  
 Указывает уровень профилирования, к которому можно применить сбор данных о производительности.  Для указания одного из трех уровней, к которому можно применить сбор данных о производительности, следует использовать следующие значения **PROFILE\_CONTROL\_LEVEL**:  
  
|Enumerator|Описание|  
|----------------|--------------|  
|PROFILE\_GLOBALLEVEL|Установка глобального уровня оказывает влияние на все процессы и потоки при выполнении профилирования.|  
|PROFILE\_PROCESSLEVEL|Установка уровня процесса оказывает влияние на все потоки, являющиеся частью указанного процесса.|  
|PROFILE\_THREADLEVEL|Установка уровня профилирования потока влияет на заданный поток.|  
  
 `dwId`  
  
 Идентификатор уровня профилирования.  Используйте идентификатор процесса или потока, созданный системой.  
  
## Значение свойства, возвращаемое значение  
 Функция указывает на успешное выполнение или сбой посредством перечисления **PROFILE\_COMMAND\_STATUS**.  Ниже перечислены возможные возвращаемые значения.  
  
|Enumerator|Описание|  
|----------------|--------------|  
|NAME\_ERROR\_ID\_NOEXIST|Заданный элемент профилирования не существует.|  
|NAME\_ERROR\_INVALID\_NAME|Недопустимое имя.|  
|NAME\_ERROR\_LEVEL\_NOEXIST|Заданный уровень профилирования не существует.|  
|NAME\_ERROR\_NO\_SUPPORT|Заданная операция не поддерживается.|  
|NAME\_ERROR\_OUTOFMEMORY|Недостаточно памяти для записи события.|  
|NAME\_ERROR\_REDEFINITION|Имя уже назначено элементу профиля.  Имя в этой функции пропускается.|  
|NAME\_ERROR\_TEXTTRUNCATED|Длина текста имени превышает 32 знака, включая знак NULL, поэтому имя было усечено.|  
|NAME\_OK|Имя успешно зарегистрировано.|  
  
## Заметки  
 Каждому процессу или потоку может быть присвоено только одно имя.  После присвоения имени элементу профилирования последующие вызовы функции NameProfile для этого элемента пропускаются.  
  
 Если одно и то же имя дается разным потокам или процессам, в отчет будут включены данные всех элементов на уровне с этим именем.  
  
 Если задается процесс или поток, отличный от текущего, то перед присвоением имени его необходимо инициализировать и запустить.  В противном случае функция NameProfile создает ошибку.  
  
> [!IMPORTANT]
>  Функции API CreateProcess\(\) и CreateThread\(\) могут вернуть значение до инициализации потока или процесса.  
  
## Эквивалент в .NET Framework  
 Microsoft.VisualStudio.Profiler.dll  
  
## Сведения о функции  
  
|||  
|-|-|  
|**Заголовок**|Include VSPerf.h|  
|**Библиотека**|Use VSPerf.lib|  
|**Юникод**|Функция реализована как `NameProfileW` \(Юникод\) и `NameProfileA` \(ANSI\).|  
  
## Пример  
 В следующем коде демонстрируется вызов функции NameProfile.  Предполагается, что в этом примере используется строковый макрос Win32 и параметры компилятора для кодировки ANSI, чтобы определить, вызывается ли в коде функция, поддерживающая кодировку ANSI.  
  
```  
void ExerciseNameProfile()  
{  
    // Variables used to print output.  
    HRESULT hResult;  
    TCHAR tchBuffer[256];  
  
    // Create and initialize variables to pass to   
    // ExerciseNameProfile.  The value of this   
    // parameter is based on the needs of the code;  
    // and for the sake of simplicity in this example,   
    // the variable is assigned an arbitrary value.  
    TCHAR * profileName = TEXT("ExerciseNameProfile");  
  
    // Declare enumeration to hold result of call to   
    // ExerciseNameProfle.  
    PROFILE_COMMAND_STATUS nameResult;  
  
    nameResult =  NameProfile(  
        profileName,  
        PROFILE_GLOBALLEVEL,  
        PROFILE_CURRENTID);  
  
    // Format and print result.  
    LPCTSTR pszFormat = TEXT("%s %d.\0");  
    TCHAR* pszTxt = TEXT("NameProfile returned");  
    hResult = StringCchPrintf(tchBuffer, 256, pszFormat,   
        pszTxt, nameResult);  
  
#ifdef DEBUG  
    OutputDebugString(tchBuffer);  
#endif  
}  
```  
  
## См. также  
 [Справочник по API\-интерфейсам профилировщика Visual Studio \(машинный код\)](../profiling/visual-studio-profiler-api-reference-native.md)