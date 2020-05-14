---
title: Обнаружение шаблона Troubleshoot в Visual Studio Документы Майкрософт
ms.date: 01/02/2018
ms.topic: conceptual
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 078d06c797c3b228c1ea5b1d836dceb0394b3174
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698936"
---
# <a name="troubleshooting-template-installation"></a>Установка шаблона устранения неполадок

Если у вас возникли проблемы с развертыванием шаблонов проекта или элемента, можно включить диагностическую систему.

::: moniker range="vs-2017"

1. Создайте файл pkgdef в папке *Common7-IDE-CommonExtensions для установки.* Например, *C:'Программные файлы (x86)»Microsoft Visual Studio-2017-Enterprise-Common7-IDE-CommonExtensions-EnablePkgDefLogging.pkgdef*.

::: moniker-end

::: moniker range=">=vs-2019"

1. Создайте файл pkgdef в папке *Common7-IDE-CommonExtensions для установки.* Например, *C:'Программные файлы (x86)»Microsoft Visual Studio/2019-Enterprise-Common7-IDE-CommonExtensions/EnablePkgDefLogging.pkgdef*.

::: moniker-end

2. Добавьте следующее в файл pkgdef:

    ```
    [$RootKey$\VsTemplate]
    "EnableTemplateDiscoveryLog"=dword:00000001
    ```

3. Откройте [командный запрос разработчика](/dotnet/framework/tools/developer-command-prompt-for-vs) для установки и запуска. `devenv /updateConfiguration`

::: moniker range="vs-2017"

4. Откройте Visual Studio и запустите диалоговые ящики нового проекта и нового элемента для инициализации обоих шаблонов деревьев.

   В настоящее время журнал шаблонов отображается в **%LOCALAPPDATA% -Microsoft-VisualStudio -15.0 "Instanceid"VsTemplateDiagnosticsList.csv** (instanceid соответствует идентификатору установки вашего экземпляра Visual Studio). Каждая инициализация дерева шаблонов придаткает записи к этому журналу.

::: moniker-end

::: moniker range=">=vs-2019"

4. Откройте Visual Studio и запустите **Создать новый проект** и диалоговые коробки **New Item** для инициализации обоих шаблонов деревьев.

   В настоящее время журнал шаблонов отображается в **%LOCALAPPDATA% -Microsoft-VisualStudio (16.0) «Instanceid»VsTemplateDiagnosticsList.csv** (instanceid соответствует идентификатору установки вашего экземпляра Visual Studio). Каждая инициализация дерева шаблонов придаткает записи к этому журналу.

::: moniker-end

Файл журнала содержит следующие столбцы:

- **FullPathToTemplate**, который имеет следующие значения:

  - 1 для развертывания на основе манифеста

  - 0 для развертывания на диске

- **TemplateFileName**

- Другие свойства шаблона

> [!NOTE]
> Чтобы отключить журнал, либо удалить файл pkgdef, или `EnableTemplateDiscoveryLog` `dword:00000000`изменить значение `devenv /updateConfiguration` до , а затем запустить снова.

## <a name="see-also"></a>См. также

- [Создание пользовательских шаблонов проектов и элементов](creating-custom-project-and-item-templates.md)
