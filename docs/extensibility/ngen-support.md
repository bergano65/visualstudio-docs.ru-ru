---
title: Поддержка Ngen в VSIX v3 Документы Майкрософт
ms.date: 11/09/2016
ms.topic: conceptual
ms.assetid: 1472e884-c74e-4c23-9d4a-6d8bdcac043b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cb75b9256ca937106235fa7a7d66d9cec71c9c60
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702401"
---
# <a name="ngen-support-in-vsix-v3"></a>Поддержка NGen в VSIX v3

С Visual Studio 2017 и новым форматом манифеста расширения VSIX v3 (версия 3) разработчики расширения теперь могут «утвориться» своими сборками во время установки.

Ниже приводится выдержка из MSDN, который объясняет, что "ngen" делает:

>Генератор изображений Native Image *(Ngen.exe)* является инструментом, который улучшает производительность управляемых приложений. *Ngen.exe* создает нативные изображения, которые представляют собой файлы, содержащие компилированный процессор-специфический машинный код, и устанавливает их в кэш нативного изображения на локальном компьютере. Среда выполнения может использовать образы в машинном коде, находящиеся в кэше, вместо использования JIT-компилятора для компиляции исходной сборки.
>
>от [Ngen.exe (Генератор изображений коренных народов)](/dotnet/framework/tools/ngen-exe-native-image-generator)

Для того, чтобы "ngen" сборки, VSIX должны быть установлены "на экземпляр на машину". Это может быть включено путем проверки "всех пользователей" флажок в дизайнере: `extension.vsixmanifest`

![проверить всех пользователей](media/check-all-users.png)

## <a name="how-to-enable-ngen"></a>Как включить Ngen

Для включения ngen для сборки можно использовать окно **Properties** в Visual Studio.

Есть 4 свойства, которые могут быть установлены:

1. **Ngen** (Boolean) - Если это правда, установка Visual Studio будет "ngen" сборки.
2. **Ngen приложение** (строка) - Ngen предоставляет возможность использовать файл *app.config* приложения для решения зависимостей сборки. Это значение должно быть установлено в *приложении, приложение* которого вы хотите использовать (относительно каталога установки Visual Studio).
3. **Ngen Architecture** (enum) - Архитектура для самостоятельной компиляции сборки. Варианты: a. Неопределенебно b. X86 c. X64 d. Все
4. **Ngen Priority** (между 1 и 3) - Уровень Приоритета Ngen задокументирован на [приоритетных уровнях Ngen.exe.](/dotnet/framework/tools/ngen-exe-native-image-generator#priority-levels)

Вот посмотрите на окно **Свойства** в действии:

![ngen по свойствам](media/ngen-in-properties.png)

Это добавит метаданные к ссылке проекта внутри файла *проекта VSIX.csproj:*

```xml
 <ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
    <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
    <Name>ClassLibrary1</Name>
    <Ngen>True</Ngen>
    <NgenApplication>vsn.exe</NgenApplication>
    <NgenArchitecture>X86</NgenArchitecture>
    <NgenPriority>2</NgenPriority>
</ProjectReference>
```

> [!NOTE]
> Вы можете отодвигать файл .csproj напрямую, если вы предпочитаете.

## <a name="extra-information"></a>Дополнительная информация

Изменения в проекте свойств применяются не только к ссылкам на проекты; Метаданные Ngen можно настроить также для элементов внутри проекта (используя те же методы, описанные выше), если элементы являются сборками .NET.
