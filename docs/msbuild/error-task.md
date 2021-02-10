---
title: Задача Error | Документы Майкрософт
description: Используйте задачу Error MSBuild, чтобы остановить сборку и зарегистрировать ошибку на основе вычисленного условного оператора.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Error
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Error task [MSBuild]
- MSBuild, Error task
ms.assetid: e96a90ee-a8ae-4e5b-8ef2-b5cf5fedd8b2
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4e4e1a91bc018bdf77671b13994ce57e4e10e694
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99877204"
---
# <a name="error-task"></a>Error - задача

Останавливает сборку и регистрирует ошибку в журнале событий на основании вычисленного условного оператора.

## <a name="parameters"></a>Параметры

В следующей таблице приводятся параметры задачи `Error` .

| Параметр | Описание |
|---------------| - |
| `Code` | Необязательный параметр `String`.<br /><br /> Код ошибки для связи с ошибкой. |
| `File` | Необязательный параметр `String`.<br /><br /> Имя файла, содержащего ошибку. Если имя файла не указано, используется файл, содержащий задачу Error. |
| `HelpKeyword` | Необязательный параметр `String`.<br /><br /> Ключевое слово справки, связанное с ошибкой. |
| `Text` | Необязательный параметр `String`.<br /><br /> Текст ошибки, регистрируемый в журнале MSBuild, если результат вычисления параметра `Condition` оказывается равным `true`. |

## <a name="remarks"></a>Remarks

Задача `Error` позволяет передавать текст ошибок в средства ведения журнала и останавливать выполнение сборки в проектах MSBuild.

Если результат вычисления параметра `Condition` оказывается равным `true`, сборка останавливается, а ошибка регистрируется в журнале. Если параметр `Condition` не существует, ошибка регистрируется в журнале, а выполнение сборки останавливается. Дополнительные сведения о ведении журнала см. в разделе [Получение журналов сборки](../msbuild/obtaining-build-logs-with-msbuild.md).

Помимо перечисленных выше параметров, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.TaskExtension>, который, в свою очередь, наследует от класса <xref:Microsoft.Build.Utilities.Task>. Список этих дополнительных параметров и их описания см. в статье [Базовый класс TaskExtension](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Пример

В следующем примере кода проверяется, что установлены все обязательные свойства. Если это не так, проект инициирует событие ошибки и регистрирует в журнале значение параметра `Text` задачи `Error`.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <Target Name="ValidateCommandLine">
        <Error
            Text=" The 0 property must be set on the command line."
            Condition="'$(0)' == ''" />
        <Error
            Text="The FREEBUILD property must be set on the command line."
            Condition="'$(FREEBUILD)' == ''" />
    </Target>
    ...
</Project>
```

## <a name="see-also"></a>См. также

- [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)
- [Получение журналов сборки](../msbuild/obtaining-build-logs-with-msbuild.md)
