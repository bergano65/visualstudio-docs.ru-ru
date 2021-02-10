---
title: Задача Warning | Документы Майкрософт
description: Узнайте, как MSBuild использует задачу Warning для записи предупреждения в журнал во время сборки на основе вычисленного условного оператора.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Warning
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Warning task [MSBuild]
- MSBuild, Warning task
ms.assetid: 96ba5507-8b43-4f54-a1d7-9b15644dd56c
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4f31ad26b6efffa540ecae6a61f0f7ff12115cef
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99933808"
---
# <a name="warning-task"></a>Warning - задача

Регистрирует в журнале предупреждение в процессе сборки на основе вычисленного условного оператора.

## <a name="parameters"></a>Параметры

 В следующей таблице приводятся параметры задачи `Warning` .

| Параметр | Описание |
|---------------| - |
| `Code` | Необязательный параметр `String`.<br /><br /> Код предупреждения для связи с предупреждением. |
| `File` | Необязательный параметр `String`.<br /><br /> Указывает соответствующий файл (при его наличии). Если файл не указан, используется файл, содержащий задачу Warning. |
| `HelpKeyword` | Необязательный параметр `String`.<br /><br /> Ключевое слово справки для связи с предупреждением. |
| `Text` | Необязательный параметр `String`.<br /><br /> Текст предупреждения, регистрируемый в журнале MSBuild, если результат вычисления параметра `Condition` оказывается равным `true`. |

## <a name="remarks"></a>Комментарии

 Задача `Warning` позволяет проектам MSBuild проверять наличие необходимой конфигурации или необходимого свойства перед переходом к следующему шагу сборки.

 Если параметр `Condition` задачи `Warning` равен `true`, значение параметра `Text` записывается в журнал, а процесс сборки продолжается. Если параметр `Condition` не существует, текст предупреждения записывается в журнал. Дополнительные сведения см. в статье о [получении журналов сборки](../msbuild/obtaining-build-logs-with-msbuild.md).

 Помимо перечисленных выше параметров, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.TaskExtension>, который, в свою очередь, наследует от класса <xref:Microsoft.Build.Utilities.Task>. Список этих дополнительных параметров и их описания см. в статье [Базовый класс TaskExtension](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Пример

 Следующий пример кода проверяет свойства, заданные в командной строке. Если заданные свойства отсутствуют, проект инициирует событие предупреждения и регистрирует в журнале значение параметра `Text` задачи `Warning`.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <Target Name="ValidateCommandLine">
        <Warning
            Text=" The 0 property was not set on the command line."
            Condition="'$(0)' == ''" />
        <Warning
            Text=" The FREEBUILD property was not set on the command line."
            Condition="'$(FREEBUILD)' == ''" />
    </Target>
    ...
</Project>
```

## <a name="see-also"></a>См. также

- [Получение журналов сборки](../msbuild/obtaining-build-logs-with-msbuild.md)
- [Справочник по схеме файла проекта](../msbuild/msbuild-project-file-schema-reference.md)
