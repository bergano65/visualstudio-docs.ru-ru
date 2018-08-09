---
title: Поддержка NGen в VSIX v3 | Документация Майкрософт
ms.custom: ''
ms.date: 11/09/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 1472e884-c74e-4c23-9d4a-6d8bdcac043b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2919559a748769c3b30e09023ad4f10965d62ce6
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/08/2018
ms.locfileid: "39639494"
---
# <a name="ngen-support-in-vsix-v3"></a>Поддержка NGen в VSIX v3

С помощью Visual Studio 2017 и новый v3 VSIX расширения (версия 3) манифеста формат расширения дают возможность разработчикам «ngen» их сборки во время установки.

Ниже приведен отрывок из MSDN, объясняется, какие «ngen» делает.

>Генератор образов в машинном (*Ngen.exe*) — это средство повышения быстродействия управляемых приложений. *Ngen.exe* создает образы в машинном коде, которые файлов, содержащих скомпилированный для конкретного процессора машинный код и устанавливает их в кэш образов в машинном коде на локальном компьютере. Среда выполнения может использовать образы в машинном коде, находящиеся в кэше, вместо использования JIT-компилятора для компиляции исходной сборки.
>
>из [Ngen.exe (генератор образов в машинном коде)](https://msdn.microsoft.com/en-us/library/6t9t5wcf(v=vs.110).aspx)

Чтобы «ngen», сборка VSIX необходимо установить «для каждого экземпляра на уровне компьютера». Эту функцию можно включить, установив флажок «все пользователи» `extension.vsixmanifest` конструктора:

![Проверьте все пользователи](media/check-all-users.png)

## <a name="how-to-enable-ngen"></a>Как включить Ngen

Чтобы включить ngen для сборки, можно использовать **свойства** окно в Visual Studio.

Существует 4 свойства, которые могут быть установлены:

1. **NGen** (логическое) — значение true, если установщик Visual Studio будет «ngen» сборки.
2. **Приложение NGen** (строка) — Ngen предоставляет возможность использования приложения *app.config* файла для разрешения зависимостей сборки. Это значение должно быть присвоено приложения, *app.config* вы хотите использовать (относительно каталога установки Visual Studio).
3. **Архитектура NGen** (enum) — архитектура скомпилировать в собственном коде сборки. Возможные варианты::. NotSpecified b. X86 c. X64 d. Все
4. **NGen Priority** (целое число от 1 до 3) — уровень приоритета Ngen описан в [уровни приоритета Ngen.exe](https://msdn.microsoft.com/en-us/library/6t9t5wcf(v=vs.110).aspx#Anchor_3).

Ниже приведен краткий обзор **свойства** окно в действии:

![NGen в свойствах](media/ngen-in-properties.png)

Метаданные будут добавлены ссылки на проект в проект VSIX *.csproj* файла:

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

 >**Примечание:** CSPROJ-файл можно редактировать напрямую, если вы предпочитаете.

## <a name="extra-information"></a>Дополнительные сведения

Применить изменения свойств конструктора больше, чем просто перекрестные ссылки между проектами; можно задать метаданные Ngen для элементов в проекте, а также (используя те же методы, описанные выше) так долго, как элементы являются сборками .NET.