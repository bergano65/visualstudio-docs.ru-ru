---
title: CommentMarkAtProfile | Документы Майкрософт
description: Используйте метод CommentMarkAtProfile для вставки значения метки времени, цифровой метки и строки комментария в VSP-файл.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- CommentMarkAtProfile
- CommentMarkAtProfileA
ms.assetid: 04294ca3-bf9c-4c76-86f1-898c2140de27
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: b40620388ffb3aefcd77eeb3f60355ed293ea59d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99970573"
---
# <a name="commentmarkatprofile"></a>CommentMarkAtProfile
Метод `CommentMarkAtProfile` вставляет значение метки времени, числовую метку и строку комментария в *VSP*-файл. Значение метки времени можно использовать для синхронизации внешних событий. Чтобы вставить метку и комментарий, необходимо включить профилирование для потока, содержащего функцию CommentMarkAtProfile.

## <a name="syntax"></a>Синтаксис

```cpp
PROFILE_COMMAND_STATUS PROFILERAPI CommentMarkAtProfile (
                                   __int64 dnTimestamp,
                                   long lMarker,
                                   LPCTSTR szComment);
```

#### <a name="parameters"></a>Параметры
 `dnTimestamp`

 64-разрядное целое число, представляющее значение метки времени.

 `lMarker`

 Числовая метка для вставки. Метка должна быть больше или равна нулю (0).

 `szComment`

 Указатель на вставляемую текстовую строку. Длина строки не должна превышать 256 символов, включая маркер конца строки NULL.

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
 Для потока, содержащего функцию метки профиля, должно быть включено состояние профилирования, чтобы вставить метку и комментарий с помощью команды Mark или функций API (CommentMarkAtProfile, CommentMarkProfile или MarkProfile). Метки профилирования имеют глобальную область видимости. Например, вставленную в любом потоке метку профиля можно использовать для обозначения начала или конца сегмента данных в любом потоке в VSP-файле.

> [!IMPORTANT]
> Методы CommentMarkAtProfile следует использовать только при профилировании с инструментированием.

## <a name="net-framework-equivalent"></a>Эквивалент .NET Framework
 *Microsoft.VisualStudio.Profiler.dll*

## <a name="function-information"></a>Сведения о функции

|Элемент|Значение|
|-|-|
|**Заголовок**|Включение *VSPerf.h*|
|**Библиотека**|Использование *VSPerf.lib*|
|**Юникод**|Функция реализована как CommentMarkAtProfileW (Юникод) и CommentMarkAtProfileA (ANSI).|

## <a name="example"></a>Пример
 В приведенном ниже коде показан вызов универсальной функции CommentMarkAtProfile. Предполагается, что в этом примере используется строковый макрос Win32 и параметры компилятора для кодировки ANSI, чтобы определить, вызывается ли в коде функция, поддерживающая кодировку ANSI.

```cpp
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

## <a name="see-also"></a>См. также
- [Справочник по API-интерфейсам профилировщика Visual Studio (машинный код)](../profiling/visual-studio-profiler-api-reference-native.md)
