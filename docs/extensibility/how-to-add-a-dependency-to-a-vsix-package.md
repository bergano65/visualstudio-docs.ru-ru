---
title: 'Как: Добавление зависимости в пакет VSIX Документы Майкрософт'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- package reference
- package assembly
- package dll
- vsix reference
ms.assetid: 8f20177b-dab9-43a3-b959-81a591b451d6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f8b350f063c28762edf90edfe71330534451c75d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711068"
---
# <a name="how-to-add-a-dependency-to-a-vsix-package"></a>Как: Добавление зависимости в пакет VSIX

Можно настроить развертывание пакета VSIX, которое устанавливает любые зависимости, которые еще не присутствуют на целевом компьютере. Для достижения этой цели включите в файл *the source.extension.vsixmanifest* зависимости VSIX.

## <a name="to-add-a-dependency"></a>Добавление зависимости

1. Откройте файл *source.extension.vsixmanifest* в представлении **Design.** Перейдите на вкладку **"Зависимости"** и нажмите **"Новый".**

2. Чтобы добавить установленное расширение: в поле диалога **Add New Dependency** выберите **удлинение,** а затем, для **name,** выберите расширение в списке.

3. Чтобы добавить еще один VSIX, который не установлен: в диалоговом поле **Add New Dependency** выберите **файл в файловой системе,** а затем используйте кнопку **«Просмотр»** для выбора VSIX.

## <a name="require-a-specific-visual-studio-release"></a>Требуется специальный релиз Visual Studio

Если для расширения требуется конкретная версия Visual Studio 2017, например, это зависит от функции, выпущенной в 15.3, вы можете указать номер сборки в VSIX **InstallationTarget.** Например, выпуск 15.3 имеет номер сборки '15.0.26730.3'. Вы можете увидеть отображение релизов для создания чисел [здесь](../install/visual-studio-build-numbers-and-release-dates.md). Обратите внимание, что использование номера выпуска '15.3' не будет работать правильно.

Если ваше расширение требует 15,3 или выше, вы объявите **версию InstallationTarget** как 15.0.26730.3, 16.0):

```xml
<Installation>
  <InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[15.0.26730.3, 16.0)" />
</Installation>
```

VSIXInstaller обнаружит более ранние версии Visual Studio и сообщит пользователю о необходимости более позднего обновления.

## <a name="see-also"></a>См. также

- [Ссылка на схему расширения VSIX 1.0](https://msdn.microsoft.com/library/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)
- [Анатомия пакета VSIX](../extensibility/anatomy-of-a-vsix-package.md)
- [Подготовка расширений для развертывания установки Windows](../extensibility/preparing-extensions-for-windows-installer-deployment.md)
