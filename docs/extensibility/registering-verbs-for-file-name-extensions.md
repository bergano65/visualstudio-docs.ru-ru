---
title: Регистрация глаголов для расширения имен файлов (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- verbs, registering
ms.assetid: 81a58e40-7cd0-4ef4-a475-c4e1e84d6e06
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ac2854f1799075cc14d9beb557335be5228be21d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701535"
---
# <a name="register-verbs-for-file-name-extensions"></a>Регистрация глаголов для расширения имен файлов
Связь расширения имени файла с приложением обычно имеет предпочтительное действие, которое происходит, когда пользователь дважды щелкает файл. Это предпочтительное действие связано с глаголом, например открытым, который соответствует действию.

 Вы можете зарегистрировать глаголы, связанные с программным идентификатором (ProgID) для расширения, используя ключ Shell, расположенный на **HKEY_CLASSES_ROOT\{progid.shell.** Для получения дополнительной информации [см.](/windows/desktop/shell/fa-file-types)

## <a name="register-standard-verbs"></a>Регистрация стандартных глаголов
 Операционная система распознает следующие стандартные глаголы:

- Открыть

- Изменить

- Воспроизведение

- Оператор print

- Предварительный просмотр

  По возможности зарегистрируйте стандартный глагол. Наиболее распространенным выбором является глагол Open. Используйте глагол Edit только в том случае, если есть явная разница между открытием файла и редактированием файла. Например, открытие файла *.htm* отображает его в браузере, в то время как редактирование файла *.htm* запускает HTML-редактор. Стандартные глаголы локализованы с помощью локальной операционной системы.

> [!NOTE]
> При регистрации стандартных глаголов не устанавливайте значение по умолчанию для ключа Open. Значение по умолчанию содержит строку отображения в меню. Операционная система поставляет эту строку для стандартных глаголов.

 Файлы проекта должны быть зарегистрированы, чтобы начать новый [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] экземпляр, когда пользователь открывает файл. Следующий пример иллюстрирует стандартную регистрацию глагола для [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] проекта.

```
[HKEY_CLASSES_ROOT\.csproj]
@="VisualStudio.csproj.8.0"

[HKEY_CLASSES_ROOT\.csproj\OpenWithList]
[HKEY_CLASSES_ROOT\.csproj\OpenWithList\VSLauncher.exe]
@=""

[HKEY_CLASSES_ROOT\.csproj\OpenWithProgids]
"VisualStudio.csproj.8.0"=""

[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe]
[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe\Shell]
[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe\Shell\Open]
[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe\Shell\Open\Command]
@="C:\\Program Files\\Common Files\\Microsoft Shared\\MSEnv\\VSLauncher.exe \"%1\""

[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0]
@="C# Project file"

[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\DefaultIcon]
@="C:\\VisualStudioPath\\VC#\\VCSPackages\\csproj.dll,0"

[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\shell]
[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\shell\Open]
[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\shell\Open\Command]
@="\"C:\\Program Files\\Common Files\\Microsoft Shared\\MSEnv\\VSLauncher.exe\" \"%1\""
```

 Чтобы открыть файл в существующем экземпляре, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]зарегистрируйте ключ DDEEXEC. Следующий пример иллюстрирует стандартную регистрацию глагола для файла [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] *.cs.*

```
[HKEY_CLASSES_ROOT\.cs]
@="VisualStudio.cs.8.0"

[HKEY_CLASSES_ROOT\.cs\OpenWithList]
[HKEY_CLASSES_ROOT\.cs\OpenWithList\devenv.exe]
@=""

[HKEY_CLASSES_ROOT\.cs\OpenWithProgids]
"VisualStudio.cs.8.0"=""

[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0]
@="C# Source file"

[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\DefaultIcon]
@="C:\\VisualStudioPath\\VC#\\VCSPackages\\csproj.dll,1"

[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell]
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open]
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\Command]
@="\"C:\\VisualStudioPath\\Common7\\IDE\\devenv.exe\" /dde \"%1\""

[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\ddeexec]
@="Open(\"%1\")"

[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\ddeexec\Application]
@="VisualStudio.8.0"

[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\ddeexec\Topic]
@="system"
```

## <a name="set-the-default-verb"></a>Установите глагол по умолчанию
 Глагол по умолчанию — это действие, выполняемые при двойном нажатии на файл в Windows Explorer. Глагол по умолчанию — это глагол, указанный в качестве значения по умолчанию для **\\HKEY_CLASSES_ROOT*progid*ключом Shell.** Если значение не указано, глагол по умолчанию является первым глаголом, указанным в **HKEY_CLASSES_ROOT\\*progid*sShell** key list.

> [!NOTE]
> Если вы планируете изменить глагол по умолчанию для расширения в боковом развертывании, учтите влияние на установку и удаление. Во время установки исходное значение по умолчанию перезаписано.

## <a name="see-also"></a>См. также
- [Управление бок о бок ассоциации файлов](../extensibility/managing-side-by-side-file-associations.md)
