---
title: StartProfile | Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- StartProfile
ms.assetid: 1761311d-c9d5-48f5-b1f8-b3605829940a
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 9ff4b4973bff395cea6b73219a2098543ee6819e
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2019
ms.locfileid: "74778262"
---
# <a name="startprofile"></a>StartProfile
Функция `StartProfile` устанавливает для счетчика значение 1 (вкл) для указанного уровня профилирования.

## <a name="syntax"></a>Синтаксис

```cpp
PROFILE_COMMAND_STATUS PROFILERAPI StartProfile(
                        PROFILE_CONTROL_LEVEL Level,
                        unsigned int dwId);
```

#### <a name="parameters"></a>Параметры
 `Level`

 Указывает уровень профилирования, к которому можно применить сбор данных по производительности. Для указания одного из трех уровней, к которому можно применить сбор данных по производительности, следует использовать представленные ниже перечислители **PROFILE_CONTROL_LEVEL**:

|Перечислитель|ОПИСАНИЕ|
|----------------|-----------------|
|PROFILE_GLOBALLEVEL|Установка глобального уровня оказывает влияние на все процессы и потоки при выполнении профилирования.|
|PROFILE_PROCESSLEVEL|Установка уровня процесса оказывает влияние на все потоки, являющиеся частью указанного процесса.|
|PROFILE_THREADLEVEL|Установка уровня профилирования потока влияет на заданный поток.|

 `dwId`

 Идентификатор процесса или потока, созданный системой.

## <a name="property-valuereturn-value"></a>Значение свойства, возвращаемое значение
 Функция информирует об успехе или неудаче с помощью перечисления **PROFILE_COMMAND_STATUS**. Может возвращаться одно из следующих значений:

|Перечислитель|ОПИСАНИЕ|
|----------------|-----------------|
|PROFILE_ERROR_ID_NOEXIST|Идентификатор элемента профилирования не существует.|
|PROFILE_ERROR_LEVEL_NOEXIST|Заданный уровень профилирования не существует.|
|PROFILE_ERROR_MODE_NEVER|На момент вызова функции был установлен режим профилирования NEVER.|
|PROFILE_ERROR_NOT_YET_IMPLEMENTED|Вызов функции профилирования, уровень профилирования или сочетание вызова и уровня пока не реализованы.|
|PROFILE_OK|Вызов выполнен успешно.|

## <a name="remarks"></a>Примечания
 Функции StartProfile и StopProfile управляют состоянием начала и остановки для уровня профилирования. Значение по умолчанию для состояния начала и остановки равно 1. Начальное значение можно изменить в реестре. Каждый вызов StartProfile устанавливает счетчик начала и остановки в значение 1; каждый вызов StopProfile устанавливает его в значение 0.

 Если значение счетчика начала и остановки больше 0, состояние начала и остановки для уровня включено. Если это значение меньше или равно 0, состояние начала и остановки отключено.

 Если состояние начала и остановки, а также состояние приостановки и возобновления включены, состояние профилирования для данного уровня включено. Для профилируемого потока состояния глобального уровня, уровня процесса и потока должны иметь значение ON.

## <a name="net-framework-equivalent"></a>Эквивалент .NET Framework
 *Microsoft.VisualStudio.Profiler.dll*

## <a name="function-information"></a>Сведения о функции
 Заголовок: объявлен в файле *VSPerf.h*

 Библиотека импорта: *VSPerf.lib*

## <a name="example"></a>Пример
 В приведенном ниже примере демонстрируется вызов функции StartProfile.

```cpp
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

## <a name="see-also"></a>См. также
- [Справочник по API-интерфейсам профилировщика Visual Studio (машинный код)](../profiling/visual-studio-profiler-api-reference-native.md)
