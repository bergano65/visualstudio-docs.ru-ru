---
title: Страница "Событий построения" в конструкторе проектов (C#)
ms.date: 10/17/2019
ms.technology: vs-ide-compile
ms.topic: reference
f1_keywords:
- cs.ProjectPropertiesBuildEvents
helpviewer_keywords:
- build events
- Project Designer, Build Events page
- pre-build events
- post-build events
ms.assetid: 3fff9ae5-213c-46ea-a660-1d70acb6c922
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: cca0ec0491d7a2c513f8bc52acaadf7c80d7fd22
ms.sourcegitcommit: 58000baf528da220fdf7a999d8c407a4e86c1278
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2019
ms.locfileid: "72789827"
---
# <a name="build-events-page-project-designer-c"></a>Страница "Событий построения" в конструкторе проектов (C#)

Страница **События сборки** в **конструкторе проектов** позволяет задать инструкции по конфигурации сборки. На ней также можно указать условия, при которых будут выполняться события, следующие после сборки. Дополнительные сведения см. в разделе [Практическое руководство. Указание событий сборки (C#)](../../ide/how-to-specify-build-events-csharp.md) и [. Указание событий сборки (Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md).

## <a name="uielement-list"></a>Список элементов пользовательского интерфейса

**Конфигурация**

Данный элемент управления нельзя изменить на этой странице. Описание этого элемента управления см. в статье [Страница "Сборка" в конструкторе проектов (C#)](../../ide/reference/build-page-project-designer-csharp.md).

**Платформа**

Этот элемент управления нельзя изменить на этой странице. Описание этого элемента управления см. в статье [Страница "Сборка" в конструкторе проектов (C#)](../../ide/reference/build-page-project-designer-csharp.md).

**Командная строка события перед сборкой**

Определяет команды, выполняемые перед началом сборки. Для ввода длинных команд нажмите кнопку **Изменить событие "Перед сборкой"** , чтобы открыть диалоговое окно ["Командная строка события перед сборкой" или "Командная строка события после сборки"](../../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md).

> [!NOTE]
> События перед сборкой не выполняются, если проект актуален и сборка не запускается.

**Командная строка события после сборки**

Определяет все команды, выполняемые после завершения сборки. Для ввода длинных команд нажмите кнопку **Изменить событие "После сборки"** , чтобы открыть диалоговое окно **"Командная строка события перед сборкой" или "Командная строка события после сборки"** .

> [!NOTE]
> Добавьте оператор `call` перед всеми командами после сборки, запускающими BAT-файлы. Например, `call C:\MyFile.bat` или `call C:\MyFile.bat call C:\MyFile2.bat`.

**Выполнить событие после сборки**

Определяет следующие условия для выполнения события после сборки, как показано в приведенной ниже таблице.

|Параметр|Результат|
|------------|------------|
|**Всегда**|Событие после сборки будет выполняться независимо от успешности сборки.|
|**При удачной сборке**|Событие после сборки будет выполняться в случае успешной сборки. Событие будет выполняться даже для актуального проекта, если его сборка завершилась успешно.|
|**При обновлении выходных файлов проекта во время сборки**|Событие после сборки будет выполняться только в том случае, если выходной файл компилятора (EXE или DLL) отличается от предыдущего выходного файла компилятора. Таким образом, событие после сборки не выполняется, если проект актуален.|

## <a name="in-the-project-file"></a>В файле проекта

В более ранних версиях Visual Studio при изменении настроек **PreBuildEvent** или **PostBuildEvent** в IDE Visual Studio добавляет в файл проекта свойство `PreBuildEvent` или `PostBuildEvent`. Так, например, если параметр командной строки **PreBuildEvent** в IDE следующая:

```input
"$(ProjectDir)PreBuildEvent.bat" "$(ProjectDir)..\" "$(ProjectDir)" "$(TargetDir)"
```

затем параметр файла проекта имеет значение.

```xml
<PropertyGroup>
    <PreBuildEvent>"$(ProjectDir)PreBuildEvent.bat" "$(ProjectDir)..\" "$(ProjectDir)" "$(TargetDir)" />
</PropertyGroup>
```

Visual Studio 2019 (и Visual Studio 2017 в более последних обновлениях) добавляет целевой объект MSBuild с именем `PreBuild` или `PostBuild` для параметров **PreBuildEvent** и **PostBuildEvent**. Например, для предыдущего примера Visual Studio теперь создаст следующий код:

```xml
<Target Name="PreBuild" BeforeTargets="PreBuildEvent">
    <Exec Command="&quot;$(ProjectDir)PreBuildEvent.bat&quot; &quot;$(ProjectDir)..\&quot; &quot;$(ProjectDir)&quot; &quot;$(TargetDir)&quot;" />
</Target>
```

> [!NOTE]
> Эти изменения файла проекта были сделаны для поддержки проектов в стиле пакетов SDK. Если вы выполняете миграцию файла проекта из старого формата в формат пакета SDK вручную, следует удалить свойства `PreBuildEvent` и `PostBuildEvent`, после чего заменить их целевыми объектами `PreBuild` и `PostBuild`, как показано в предыдущем коде. Чтобы узнать, как определить, является ли ваш проект проектом в формате пакета SDK, см. раздел [Проверка формата проекта](/nuget/resources/check-project-format).

## <a name="see-also"></a>См. также

- [Практическое руководство. Указание событий сборки (Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md)
- [Практическое руководство. Указание событий сборки (C#)](../../ide/how-to-specify-build-events-csharp.md)
- [Справочник по свойствам проектов](../../ide/reference/project-properties-reference.md)
- [Компилирование и сборка](../../ide/compiling-and-building-in-visual-studio.md)