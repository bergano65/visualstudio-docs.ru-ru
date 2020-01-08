---
title: Задача Message | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Message
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, Message task
- Message task [MSBuild]
ms.assetid: 2293309d-42b6-46dc-9684-8c146f66bc28
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c5a2e2a1adb810a8468d318298747eec226846df
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/01/2020
ms.locfileid: "75592182"
---
# <a name="message-task"></a>Message - задача
Записывает сообщения в журнал в процессе сборки.

## <a name="parameters"></a>Параметры
 В следующей таблице приводятся параметры задачи `Message` .

|Параметр|Описание|
|---------------|-----------------|
|`Importance`|Необязательный параметр `String`.<br /><br /> Определяет важность сообщения. Этот параметр может иметь значение `high`, `normal` или `low`. Значение по умолчанию — `normal`.|
|`Text`|Необязательный параметр `String`.<br /><br /> Текст ошибки для записи в журнал.|

## <a name="remarks"></a>Примечания
 Задача `Message` позволяет проектам [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] отправлять сообщения в средства ведения журнал на разных этапах процесса сборки.

 Если параметр `Condition` равен `true`, значение параметра `Text` записывается, а процесс сборки продолжает выполняться. Если параметр `Condition` не существует, текст сообщения записывается в журнал. Дополнительные сведения см. в статье о [получении журналов сборки](../msbuild/obtaining-build-logs-with-msbuild.md).

 По умолчанию сообщение отправляется в средство ведения журнала консоли MSBuild. Это поведение можно изменить, присвоив параметру <xref:Microsoft.Build.Tasks.TaskExtension.Log%2A> необходимое значение. Средство ведения журнала интерпретирует параметр `Importance`. Как правило, сообщение со свойством `high` отправляется, если для детализации средства ведения журнала задано значение <xref:Microsoft.Build.Framework.LoggerVerbosity>`Minimal` или более высокое. Сообщение со свойством `low` отправляется, если для детализации средства ведения журнала задано значение <xref:Microsoft.Build.Framework.LoggerVerbosity>`Detailed`.

 Помимо перечисленных выше параметров, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.TaskExtension>, который, в свою очередь, наследует от класса <xref:Microsoft.Build.Utilities.Task>. Список этих дополнительных параметров и их описания см. в статье [Базовый класс TaskExtension](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Пример
 В следующем примере кода сообщения регистрируются во всех зарегистрированных средствах ведения журнала.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <Target Name="DisplayMessages">
        <Message Text="Project File Name = $(MSBuildProjectFile)" />
        <Message Text="Project Extension = $(MSBuildProjectExtension)" />
    </Target>
    ...
</Project>
```

## <a name="see-also"></a>См. также
- [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)
- [Получение журналов сборки](../msbuild/obtaining-build-logs-with-msbuild.md)
