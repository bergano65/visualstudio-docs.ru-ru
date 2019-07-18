---
title: Новые возможности в Visual Studio SDK 2019 г. | Документация Майкрософт
ms.date: 03/29/2019
ms.topic: conceptual
ms.assetid: 4a07607b-0c87-4866-acd8-6d68358d6a47
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d4be152cfb39ddea9ddaeea56464a3447be4f2c6
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66320608"
---
# <a name="whats-new-in-the-visual-studio-2019-sdk"></a>Новые возможности пакета SDK для Visual Studio 2019

Пакет SDK для Visual Studio содержит следующие новые и обновленные функции для Visual Studio 2019.

## <a name="synchronously-autoloaded-extensions-warning"></a>Предупреждение синхронно загружаться автоматически расширения

Теперь пользователи будут видеть предупреждение, если какой-либо их установленных расширений синхронно загружаться автоматически при запуске. Дополнительные сведения о предупреждении в [синхронно расширения загружены автоматически](synchronously-autoloaded-extensions.md).

## <a name="single-unified-visual-studio-sdk"></a>Единую Visual Studio SDK

Все ресурсы пакета SDK для Visual Studio теперь можно получить через одного пакета NuGet [Microsoft.VisualStudio.SDK](https://www.nuget.org/packages/microsoft.visualstudio.sdk).

## <a name="editor-registration-enhancements"></a>Усовершенствования регистрации редактора

С момента его создания, Visual Studio поддерживается регистрации настраиваемого редактора, где редактор можно объявить его соответствие для определенного расширения (например, .xaml и .rc), или он подходит для любого расширения (. *). Начиная с версии 16.1 2019 г. Visual Studio, мы расширить поддержку регистрации редактора.

### <a name="filenames"></a>Имена файлов

В дополнение или вместо, регистрация поддержки для файлов с определенным расширением, редактор можно зарегистрировать, что он поддерживает определенные имена файлов путем применения нового `ProvideEditorFilename` атрибута для пакета редактора.

Например, это будет применена редактор, который поддерживает все файлы .json `ProvideEditorExtension` атрибут пакета:

```cs
[ProvideEditorExtension(typeof(MyEditor), ".json", MyEditor.Priority)]
```

Начиная с 16.1, если MyEditor поддерживает только несколько хорошо известных JSON-файлы, его можно вместо этого применить их `ProvideEditorFilename` атрибуты для своего пакета:

```cs
[ProvideEditorFilename(typeof(MyEditor), "particular.json", MyEditor.Priority)]
[ProvideEditorFilename(typeof(MyEditor), "special.json",    MyEditor.Priority)]
```

### <a name="uicontexts"></a>Объектов UIContext

Редактор можно зарегистрировать один или несколько объектов UIContext, представляющие, если он включен. Зарегистрированных объектов UIContext, применяя один или несколько экземпляров `ProvideEditorUIContextAttribute` к пакету, который регистрирует редактор.

Если редактор имеет зарегистрированных объектов UIContext:

- Если хотя бы один из его зарегистрированных объектов UIContext активен, при открытии файла с заданным расширением, редактор включается в поиске редактора.
- Если ни один из зарегистрированных объектов UIContext не активна, редактор не включается в поиск редактора.

Если редактор не регистрирует все объектов UIContext, всегда включается в поиск редактор для этого расширения.

Например, если редактор доступен только тогда, когда C# проекта открыт, его можно объявить этот сходства, применяя `ProvideEditorUIContext` атрибут:

```cs
[ProvideEditorUIContext(typeof(MyEditor), KnownUIContexts.CSharpProjectContext)]
```
