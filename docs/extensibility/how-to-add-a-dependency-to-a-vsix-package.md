---
title: Как добавить зависимость в пакет VSIX | Документация Майкрософт
description: Узнайте, как настроить развертывание пакета VSIX, которое устанавливает все зависимости, отсутствующие на целевом компьютере.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
ms.openlocfilehash: d7ef19bafd0788ed15094979141679625e4e992f
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/10/2020
ms.locfileid: "96993839"
---
# <a name="how-to-add-a-dependency-to-a-vsix-package"></a>Как добавить зависимость в пакет VSIX

Можно настроить развертывание пакета VSIX, устанавливающего все зависимости, которые еще не существуют на целевом компьютере. Для этого включите зависимости VSIX в файл *source. extension. vsixmanifest* .

## <a name="to-add-a-dependency"></a>Добавление зависимости

1. Откройте файл *source. extension. vsixmanifest* в представлении **конструктора** . Перейдите на вкладку **зависимости** и нажмите кнопку **создать**.

2. Чтобы добавить установленное расширение, в диалоговом окне " **Добавление новой зависимости** " выберите **установленное расширение** , а затем в поле **имя** выберите расширение в списке.

3. Чтобы добавить еще не установленный VSIX: в диалоговом окне **Добавление новой зависимости** выберите **файл в файловой системе** , а затем нажмите кнопку **Обзор** , чтобы выбрать VSIX.

## <a name="require-a-specific-visual-studio-release"></a>Требовать конкретный выпуск Visual Studio

Например, если для расширения требуется определенная версия Visual Studio 2017, то она зависит от функции, выпущенной в 15,3, можно указать номер сборки в VSIX **InstallationTarget**. Например, выпуск 15,3 имеет номер сборки "15.0.26730.3". Сопоставление выпусков для номеров сборки можно увидеть [здесь](../install/visual-studio-build-numbers-and-release-dates.md). Обратите внимание, что использование номера выпуска "15,3" не будет работать правильно.

Если для расширения требуется 15,3 или более поздней версии, вы объявили **версию InstallationTarget** как [15.0.26730.3, 16,0):

```xml
<Installation>
  <InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[15.0.26730.3, 16.0)" />
</Installation>
```

Всиксинсталлер обнаружит более ранние версии Visual Studio и сообщит пользователю о необходимости последующего обновления.

## <a name="see-also"></a>См. также раздел

- [Справочник по схеме расширения VSIX 1,0](/previous-versions/dd393700(v=vs.110))
- [Анатомия пакета VSIX](../extensibility/anatomy-of-a-vsix-package.md)
- [Подготовка расширений для развертывания установщик Windows](../extensibility/preparing-extensions-for-windows-installer-deployment.md)