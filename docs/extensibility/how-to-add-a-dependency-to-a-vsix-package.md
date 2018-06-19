---
title: 'Как: Добавление зависимости пакета VSIX | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- package reference
- package assembly
- package dll
- vsix reference
ms.assetid: 8f20177b-dab9-43a3-b959-81a591b451d6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0704a72ba70e2a00baab99d327702ec6c08f1775
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31133226"
---
# <a name="how-to-add-a-dependency-to-a-vsix-package"></a>Как: Добавление зависимости пакета VSIX

Можно настроить развертывание пакета VSIX, который устанавливает все зависимости, которые еще не присутствуют на конечном компьютере. Для выполнения этой задачи включают VSIX зависимости, чтобы файл source.extension.vsixmanifest.

## <a name="to-add-a-dependency"></a>Добавление зависимости

1. Откройте файл source.extension.vsixmanifest в **разработки** представления. Последовательно выберите пункты **зависимости** и нажмите кнопку **New**.

2. Чтобы добавить установленное расширение: в **Добавление новых зависимостей** установите флажок **установленное расширение** и затем для **имя**, выбрать расширение в списке.

3. Чтобы добавить другой файл VSIX, который не установлен:: в **Добавление новых зависимостей** выберите **файл в файловой системе** , а затем используйте **Обзор** кнопку, чтобы выбрать расширение VSIX.

## <a name="require-a-specific-visual-studio-release"></a>Требовать конкретного выпуска Visual Studio

Если расширение требует определенной версии Visual Studio 2017 г., например, зависит от компонентов, выпущенные в 15,3, можно указать номер сборки в вашего VSIX **InstallationTarget**. Например версия 15,3 содержит ряд построения "15.0.26730.3». Вы увидите сопоставление выпусков для номера построения [здесь](../install/visual-studio-build-numbers-and-release-dates.md). Обратите внимание, что с помощью номера версии «15.3"не будет работать правильно.

Если для модуля требуется 15,3 или более поздней версии, можно объявить **InstallationTarget версии** как [15.0.26730.3, 16.0):

```xml
<Installation>
  <InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[15.0.26730.3, 16.0)" />
</Installation>
```

VSIXInstaller обнаружит более ранних версиях Visual Studio и информировать пользователей о том, что более позднее обновление является обязательным.


## <a name="see-also"></a>См. также

 [Справочник по схеме 1.0 расширения VSIX](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b) [составляющие пакета VSIX](../extensibility/anatomy-of-a-vsix-package.md) [Подготовка расширения для развертывания установщика Windows](../extensibility/preparing-extensions-for-windows-installer-deployment.md)