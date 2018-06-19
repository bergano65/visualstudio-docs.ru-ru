---
title: Устранение неполадок обнаружения шаблон в Visual Studio | Документы Microsoft
ms.custom: ''
ms.date: 01/02/2018
ms.technology: vs-ide-sdk
ms.topic: conceptual
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d183fd664258fbb7dbcf27c913c56c6f6160e6c4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31136732"
---
# <a name="troubleshooting-template-installation"></a>Устранение неполадок при установке шаблона

Если возникли проблемы при развертывании шаблонов проектов и элементов, можно включить сбор данных диагностики.

1. Создайте файл pkgdef в папке Common7\IDE\CommonExtensions для установки (например, C:\Program Files (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\IDE\CommonExtensions\EnablePkgDefLogging.pkgdef) со следующим содержимым:

    ```
    [$RootKey$\VsTemplate]
    "EnableTemplateDiscoveryLog"=dword:00000001
    ```

1. Откройте «Командная строка разработчика» для установки с использованием поиска в службе Windows search и выполните `devenv /updateConfiguration`.

1. Запустите Visual Studio и запустите диалоговых окон новый проект и новый элемент для инициализации обоих деревьях шаблона. Журнал Шаблон появится в **%LOCALAPPDATA%\Microsoft\VisualStudio\15.0_[instanceid]\VsTemplateDiagnosticsList.csv** (instanceid соответствует идентификатору установки экземпляра Visual Studio). Каждый шаблон дерева инициализации добавляет записи в этот журнал.

Файл журнала содержит следующие столбцы:

- **FullPathToTemplate**, который имеет следующие значения:

    - 1 для развертывания на основе манифеста

    - 0 для развертывания на диске

- **TemplateFileName**

- Другие свойства шаблона

> [!NOTE]
> Отключение ведения журнала, удалите файл pkgdef, или измените значение `EnableTemplateDiscoveryLog` для `dword:00000000`, а затем запустите `devenv /updateConfiguration` еще раз.

## <a name="see-also"></a>См. также

[Создание пользовательских шаблонов проектов и элементов](creating-custom-project-and-item-templates.md)