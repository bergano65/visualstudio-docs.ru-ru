---
title: Что нового в визуальной студии 2019 SDK Документы Майкрософт
ms.date: 03/29/2019
ms.topic: conceptual
ms.assetid: 4a07607b-0c87-4866-acd8-6d68358d6a47
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 187d3df4b5bcefefc0135c010c7d98951e9b3af8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740402"
---
# <a name="whats-new-in-the-visual-studio-2019-sdk"></a>Новые возможности пакета SDK для Visual Studio 2019

Визуальная студия SDK имеет следующие новые и обновленные функции для Visual Studio 2019.

## <a name="synchronously-autoloaded-extensions-warning"></a>Предупреждение о синхронно автоматическом загрузке расширений

Пользователи теперь будут видеть предупреждение, если какой-либо из их установленных расширений синхронно автоматически загружены на запуск. Вы можете узнать больше о предупреждении на [синхронно автоматически загруженных расширений.](synchronously-autoloaded-extensions.md)

## <a name="single-unified-visual-studio-sdk"></a>Одно-единая, единая визуальная студия SDK

Теперь вы можете получить все визуальные студии SDK активов через один пакет NuGet [Microsoft.VisualStudio.SDK](https://www.nuget.org/packages/microsoft.visualstudio.sdk).

## <a name="editor-registration-enhancements"></a>Улучшения регистрации редакторов

С момента своего создания Visual Studio поддерживает пользовательскую регистрацию редактора, где редактор может заявить о своей сродстве к конкретным расширениям (например, .xaml и .rc), или что он подходит для любого расширения (.). Начиная с Visual Studio 2019 версии 16.1, мы расширяем поддержку регистрации редактора.

### <a name="filenames"></a>Имена файлов

В дополнение к регистрации поддержки для конкретного расширения файла редактор может зарегистрировать, что он `ProvideEditorFilename` поддерживает определенные имена файлов, применяя новый атрибут к пакету редактора.

Например, редактор, поддерживающий все файлы `ProvideEditorExtension` .json, применяет этот атрибут к своему пакету:

```cs
[ProvideEditorExtension(typeof(MyEditor), ".json", MyEditor.Priority)]
```

Начиная с 16.1, если MyEditor поддерживает только несколько известных файлов .json, он может вместо этого применить эти `ProvideEditorFilename` атрибуты к своему пакету:

```cs
[ProvideEditorFilename(typeof(MyEditor), "particular.json", MyEditor.Priority)]
[ProvideEditorFilename(typeof(MyEditor), "special.json",    MyEditor.Priority)]
```

### <a name="uicontexts"></a>UIContexts

Редактор может зарегистрировать один или несколько UIContexts, которые представляют, когда он включен. UIContexts регистрируются, применяя один `ProvideEditorUIContextAttribute` или несколько экземпляров к пакету, который регистрирует редактор.

Если редактор зарегистрировал UIContexts:

- Если хотя бы один из зарегистрированных UIContexts активен при открытии файла с заданное расширение, редактор включен в поиск редактора.
- Если ни один из зарегистрированных UIContexts не активен, редактор не включен в поиск редактора.

Если редактор не регистрирует никаких UIContexts, он всегда включается в поиск редактора для этого расширения.

Например, если редактор доступен только при открытии проекта C', он может `ProvideEditorUIContext` объявить об этом сродстве, применяя атрибут:

```cs
[ProvideEditorUIContext(typeof(MyEditor), KnownUIContexts.CSharpProjectContext)]
```
