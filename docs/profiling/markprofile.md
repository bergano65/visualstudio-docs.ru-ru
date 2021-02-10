---
title: MarkProfile | Документация Майкрософт
description: Метод MarkProfile вставляет метку профилирования в VSP-файл. Для добавления метки должно быть активировано профилирование для потока, содержащего функцию MarkProfile.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MarkProfile
ms.assetid: 54dac8c8-c8ee-4023-af27-b25466e3a6ec
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: b4e66049ec5547913dad8df7256f2db3d2395fa0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99851963"
---
# <a name="markprofile"></a>MarkProfile
Метод `MarkProfile` вставляет метку профилирования в *VSP*-файл. Для добавления метки должно быть активировано профилирование для потока, содержащего функцию `MarkProfile`.

## <a name="syntax"></a>Синтаксис

```cpp
PROFILE_COMMAND_STATUS PROFILERAPI MarkProfile( long lMarker );
```

#### <a name="parameters"></a>Параметры
 `lMarker`

 Метка, которую нужно вставить. Меткой должно быть число больше нуля или нуль (0).

## <a name="property-valuereturn-value"></a>Значение свойства, возвращаемое значение
 Функция информирует об успехе или неудаче с помощью перечисления **PROFILE_COMMAND_STATUS**. Может возвращаться одно из следующих значений:

|Перечислитель|Описание|
|----------------|-----------------|
|MARK_ERROR_MARKER_RESERVED|Значение параметра меньше или равно нулю. Эти значения зарезервированы. Метка и комментарий не записываются.|
|MARK_ERROR_MODE_NEVER|На момент вызова функции был установлен режим профилирования NEVER. Метка и комментарий не записываются.|
|MARK_ERROR_MODE_OFF|На момент вызова функции был установлен режим профилирования OFF. Метка и комментарий не записываются.|
|MARK_ERROR_NO_SUPPORT|В данном контексте метки не поддерживаются. Метка и комментарий не записываются.|
|MARK_ERROR_OUTOFMEMORY|Недостаточно памяти для записи события. Метка и комментарий не записываются.|
|MARK_TEXTTOOLONG|Длина строки превышает 256 символов. Строка комментария усекается. Метка и комментарий записываются.|
|MARK_OK|В случае успеха возвращается MARK_OK.|

## <a name="remarks"></a>Примечания
 Значение метки вставляется в *VSP*-файл при каждом выполнении кода, когда выполняется профилирование потока, содержащего функцию MarkProfile. MarkProfile можно вызывать многократно.

 Метки профилирования имеют глобальную область видимости. Например, вставленную в любом потоке метку профиля можно использовать для обозначения начала или конца сегмента данных в любом потоке в *VSP*-файле.

 Для потока, содержащего функцию метки профиля, должно быть включено состояние профилирования, чтобы вставить метку и комментарий с помощью команды Mark или функций API (CommentMarkAtProfile, CommentMarkProfile или MarkProfile).

> [!IMPORTANT]
> Метод MarkProfile следует использовать только при профилировании методом инструментирования.

## <a name="net-framework-equivalent"></a>Эквивалент .NET Framework
 *Microsoft.VisualStudio.Profiler.dll*

## <a name="function-information"></a>Сведения о функции
 Заголовок: объявлен в файле *VSPerf.h*

 Библиотека импорта: *VSPerf.lib*

## <a name="example"></a>Пример
 Следующий код демонстрирует использование функции MarkProfile.

```cpp
void ExerciseMarkProfile()
{
    // Declare and initialize variables to pass to
    // MarkProfile.  The values of these parameters
    // are assigned based on the needs of the code;
    // and for the sake of simplicity in this example,
    // the variables are assigned arbitrary values.
    int markId = 03;

    // Declare enumeration to hold return value of
    // call to MarkProfile.
    PROFILE_COMMAND_STATUS markResult;

    // Variables used to print output.
    HRESULT hResult;
    TCHAR tchBuffer[256];

    markResult = MarkProfile(markId);

    // Format and print result.
    LPCTSTR pszFormat = TEXT("%s %d.\0");
    TCHAR* pszTxt = TEXT("MarkProfile returned");
    hResult = StringCchPrintf(tchBuffer, 256, pszFormat,
        pszTxt, markResult);

#ifdef DEBUG
    OutputDebugString(tchBuffer);
#endif
}
```

## <a name="see-also"></a>См. также
- [Справочник по API-интерфейсам профилировщика Visual Studio (машинный код)](../profiling/visual-studio-profiler-api-reference-native.md)
