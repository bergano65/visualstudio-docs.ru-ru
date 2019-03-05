---
title: Устранение неполадок обнаружения шаблонов в Visual Studio | Документация Майкрософт
ms.date: 01/02/2018
ms.topic: conceptual
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d9ae6220ac38de7bf2edc7b5c305ecb377a46f18
ms.sourcegitcommit: 11337745c1aaef450fd33e150664656d45fe5bc5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/04/2019
ms.locfileid: "57324004"
---
# <a name="troubleshooting-template-installation"></a>Устранение неполадок установки шаблона

Если возникли проблемы при развертывании шаблонов проекта или элемента, вы можете включить ведение журналов диагностики.

::: moniker range="vs-2017"

1. Создайте файл pkgdef в *Common7\IDE\CommonExtensions* папку для установки. Например *\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\CommonExtensions\EnablePkgDefLogging.pkgdef C:\Program Files (x86)*.

::: moniker-end

::: moniker range=">=vs-2019"

1. Создайте файл pkgdef в *Common7\IDE\CommonExtensions* папку для установки. Например *\Microsoft Visual Studio\2019\Enterprise\Common7\IDE\CommonExtensions\EnablePkgDefLogging.pkgdef C:\Program Files (x86)*.

::: moniker-end

2. Добавьте файл pkgdef следующее:

    ```
    [$RootKey$\VsTemplate]
    "EnableTemplateDiscoveryLog"=dword:00000001
    ```

3. Откройте [Командная строка разработчика](/dotnet/framework/tools/developer-command-prompt-for-vs) для установки и запуска `devenv /updateConfiguration`.

::: moniker range="vs-2017"

4. Запустите Visual Studio и запустить новый проект и новый элемент диалоговых окнах, чтобы инициализировать обоих деревьях шаблона.

   В журнале шаблон появится в **%LOCALAPPDATA%\Microsoft\VisualStudio\15.0_[instanceid]\VsTemplateDiagnosticsList.csv** (instanceid соответствует Идентификатору установки экземпляра Visual Studio). Каждый шаблон дерева инициализации добавляет записи в этот журнал.

::: moniker-end

::: moniker range=">=vs-2019"

4. Запустите Visual Studio и запустить новый проект и новый элемент диалоговых окнах, чтобы инициализировать обоих деревьях шаблона.

   В журнале шаблон появится в **%LOCALAPPDATA%\Microsoft\VisualStudio\16.0_[instanceid]\VsTemplateDiagnosticsList.csv** (instanceid соответствует Идентификатору установки экземпляра Visual Studio). Каждый шаблон дерева инициализации добавляет записи в этот журнал.

::: moniker-end

Файл журнала содержит следующие столбцы:

- **FullPathToTemplate**, который имеет следующие значения:

    - 1 для развертывания на основе манифеста

    - 0 для развертывания на основе диска

- **TemplateFileName**

- Другие свойства шаблона

> [!NOTE]
> Отключение ведения журнала, удалите файл pkgdef, или измените значение свойства `EnableTemplateDiscoveryLog` для `dword:00000000`, а затем запустите `devenv /updateConfiguration` еще раз.

## <a name="see-also"></a>См. также

- [Создание пользовательских шаблонов проектов и элементов](creating-custom-project-and-item-templates.md)