---
title: CommentMarkProfile | Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- CommentMarkProfile
- CommentMarkProfileA
ms.assetid: 33ccff45-c33a-4672-b41f-5b317b848cd1
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: d45bab6b909fffa107158236d9050632f114c530
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/18/2020
ms.locfileid: "74772795"
---
# <a name="commentmarkprofile"></a>CommentMarkProfile
Функция `CommentMarkProfile` вставляет числовую метку и текстовую строку в *VSP*-файл. Чтобы вставить метку и комментарий, необходимо включить профилирование для потока, содержащего функцию `CommentMarkProfile`.

## <a name="syntax"></a>Синтаксис

```cpp
PROFILE_COMMAND_STATUS PROFILERAPI CommentMarkProfile(
                                   long lMarker,
                                   LPCTSTR szComment);
```

#### <a name="parameters"></a>Параметры
 `lMarker`

 Вставляемая числовая метка. Метка должна быть больше или равна нулю (0).

 `szComment`

 Указатель на вставляемую текстовую строку. Длина строки не должна превышать 256 символов, включая маркер конца строки NULL.

## <a name="property-valuereturn-value"></a>Значение свойства, возвращаемое значение
 Функция информирует об успехе или неудаче с помощью перечисления **PROFILE_COMMAND_STATUS**. Может возвращаться одно из следующих значений:

|Перечислитель|Description|
|----------------|-----------------|
|MARK_ERROR_MARKER_RESERVED|Значение параметра меньше или равно нулю. Эти значения зарезервированы. Метка и комментарий не записываются.|
|MARK_ERROR_MODE_NEVER|На момент вызова функции был установлен режим профилирования NEVER. Метка и комментарий не записываются.|
|MARK_ERROR_MODE_OFF|На момент вызова функции был установлен режим профилирования OFF. Метка и комментарий не записываются.|
|MARK_ERROR_NO_SUPPORT|В данном контексте метки не поддерживаются. Метка и комментарий не записываются.|
|MARK_ERROR_OUTOFMEMORY|Недостаточно памяти для записи события. Метка и комментарий не записываются.|
|MARK_TEXTTOOLONG|Длина строки превышает 256 символов. Строка комментария усекается. Метка и комментарий записываются.|
|MARK_OK|В случае успеха возвращается MARK_OK.|

## <a name="remarks"></a>Remarks
 Для потока, содержащего функцию метки профиля, должно быть включено состояние профилирования, чтобы вставить метку и комментарий с помощью команды VSInstr Mark или функций (CommentMarkAtProfile, CommentMarkProfile или MarkProfile).

 Метки профилирования имеют глобальную область видимости. Например, вставленную в любом потоке метку профиля можно использовать для обозначения начала или конца сегмента данных в любом потоке в *VSP*-файле.

> [!IMPORTANT]
> Метод CommentMarkProfile можно использовать только при профилировании с инструментированием.

## <a name="net-framework-equivalent"></a>Эквивалент .NET Framework
 Microsoft.VisualStudio.Profiler.dll

## <a name="function-information"></a>Сведения о функции

|||
|-|-|
|**Верхняя часть**|Включение VSPerf.h|
|**Библиотека**|Использование VSPerf.lib|
|**Юникод**|Функция реализована как `CommentMarkProfileW` (Юникод) и `CommentMarkProfileA` (ANSI).|

## <a name="example"></a>Пример
 В приведенном ниже коде демонстрируется вызов функции CommentMarkProfile. Предполагается, что в этом примере используется строковый макрос Win32 и параметры компилятора для Юникода, чтобы определить, вызывается ли в коде функция [!INCLUDE[vcpransi](../profiling/includes/vcpransi_md.md)].

```cpp
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

## <a name="see-also"></a>См. также раздел
- [Справочник по API-интерфейсам профилировщика Visual Studio (машинный код)](../profiling/visual-studio-profiler-api-reference-native.md)
