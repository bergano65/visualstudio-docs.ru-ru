---
title: NameProfile | Документы Майкрософт
description: Сведения о функции NameProfile, которая назначает строку указанному процессу или потоку. Кроме того, API NameProfile доступен только для профилирования инструментирования.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- NameProfile
- NameProfileA
ms.assetid: 1bb05441-c4ff-4323-9fef-f3924fba4430
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 53d6dcc6cdc903f0050eeb326ebd3c5fa36252ae
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99964749"
---
# <a name="nameprofile"></a>NameProfile
Функция `NameProfile` назначает строку указанному процессу или потоку.

 API NameProfile доступен только для профилирования с инструментированием. API NameProfile не поддерживается для профилирования с выборкой.

## <a name="syntax"></a>Синтаксис

```cpp
PROFILE_COMMAND_STATUS PROFILERAPI NameProfile(
                                   LPCTSTR pszName,
                                   PROFILE_CONTROL_LEVEL Level,
                                   unsigned int dwId);
```

#### <a name="parameters"></a>Параметры
 `pszName`

 Имя элемента профилирования. Имя не является допустимым (в результате чего возвращается NAME_ERROR_INVALID_NAME NameProfileA) в следующих случаях:

- Указатель, переданный в NameProfileA, имеет значение NULL.

- Строковые данные параметра pszName начинаются с числа.

- Строковые данные параметра pszName содержат пробел.

- Строковые данные параметра pszName содержат любой из следующих знаков: ,;.`~!@#$%^&*()=[]{}&#124;\\?/<>

  `Level`

  Указывает уровень профилирования, к которому можно применить сбор данных по производительности. Чтобы указать один из трех уровней, к которому можно применить сбор данных производительности, следует использовать представленные ниже значения **PROFILE_CONTROL_LEVEL**.

|Перечислитель|Описание|
|----------------|-----------------|
|PROFILE_GLOBALLEVEL|Установка глобального уровня оказывает влияние на все процессы и потоки при выполнении профилирования.|
|PROFILE_PROCESSLEVEL|Установка уровня процесса оказывает влияние на все потоки, являющиеся частью указанного процесса.|
|PROFILE_THREADLEVEL|Установка уровня профилирования потока влияет на заданный поток.|

 `dwId`

 Идентификатор уровня профилирования. Используйте идентификатор процесса или потока, созданный системой.

## <a name="property-valuereturn-value"></a>Значение свойства, возвращаемое значение
 Функция информирует об успехе или неудаче с помощью перечисления **PROFILE_COMMAND_STATUS**. Может возвращаться одно из следующих значений:

|Перечислитель|Описание|
|----------------|-----------------|
|NAME_ERROR_ID_NOEXIST|Заданный элемент профилирования не существует.|
|NAME_ERROR_INVALID_NAME|Недопустимое имя.|
|NAME_ERROR_LEVEL_NOEXIST|Заданный уровень профилирования не существует.|
|NAME_ERROR_NO_SUPPORT|Указанная операция не поддерживается.|
|NAME_ERROR_OUTOFMEMORY|Недостаточно памяти для записи события.|
|NAME_ERROR_REDEFINITION|Имя уже присвоено элементу профиля. Имя в этой функции не учитывается.|
|NAME_ERROR_TEXTTRUNCATED|Длина имени превысила 32 символа, включая символ null, и поэтому оно было усечено.|
|NAME_OK|Имя зарегистрировано успешно.|

## <a name="remarks"></a>Примечания
 Каждому процессу или потоку можно назначить только одно имя. После присвоения имени элементу профилирования последующие вызовы метода NameProfile для этого элемента пропускаются.

 Если одно и то же имя задано для разных потоков или процессов, в отчет будут включены данные из всех элементов с таким именем на данном уровне.

 Если вы указываете процесс или поток, отличный от текущего, убедитесь, что он инициализирован и запущен, прежде чем задавать для него имя. В противном случае метод NameProfile завершается с ошибкой.

> [!IMPORTANT]
> Функции API CreateThread() API и CreateProcess() могут возвращать данные до инициализации потока или процесса.

## <a name="net-framework-equivalent"></a>Эквивалент .NET Framework
 *Microsoft.VisualStudio.Profiler.dll*

## <a name="function-information"></a>Сведения о функции

|Элемент|Значение|
|-|-|
|**Заголовок**|Включение *VSPerf.h*|
|**Библиотека**|Использование *VSPerf.lib*|
|**Юникод**|Функция реализована как `NameProfileW` (Юникод) и `NameProfileA` (ANSI).|

## <a name="example"></a>Пример
 Приведенный ниже код демонстрирует вызов функции NameProfile. Предполагается, что в этом примере используется строковый макрос Win32 и параметры компилятора для кодировки ANSI, чтобы определить, вызывается ли в коде функция, поддерживающая кодировку ANSI.

```cpp
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

## <a name="see-also"></a>См. также
- [Справочник по API-интерфейсам профилировщика Visual Studio (машинный код)](../profiling/visual-studio-profiler-api-reference-native.md)
