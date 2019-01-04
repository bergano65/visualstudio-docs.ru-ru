---
title: Устранение неполадок обнаружения шаблонов в Visual Studio | Документация Майкрософт
ms.date: 01/02/2018
ms.topic: conceptual
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 39ebb7c49e5a8482ab0b2ef5c3a5257d0237b39c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53836157"
---
# <a name="troubleshooting-template-installation"></a>Устранение неполадок установки шаблона

Если возникли проблемы при развертывании шаблонов проекта или элемента, вы можете включить ведение журналов диагностики.

1. Создайте файл pkgdef в папке Common7\IDE\CommonExtensions для установки (например, C:\Program Files (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\IDE\CommonExtensions\EnablePkgDefLogging.pkgdef) со следующим содержимым:

    ```
    [$RootKey$\VsTemplate]
    "EnableTemplateDiscoveryLog"=dword:00000001
    ```

1. Откройте «командную строку разработчика» для установки, выполнив поиск в службе поиска Windows и выполните `devenv /updateConfiguration`.

1. Запустите Visual Studio и запустить новый проект и новый элемент диалоговых окнах, чтобы инициализировать обоих деревьях шаблона. В журнале шаблон появится в **%LOCALAPPDATA%\Microsoft\VisualStudio\15.0_[instanceid]\VsTemplateDiagnosticsList.csv** (instanceid соответствует Идентификатору установки экземпляра Visual Studio). Каждый шаблон дерева инициализации добавляет записи в этот журнал.

Файл журнала содержит следующие столбцы:

- **FullPathToTemplate**, который имеет следующие значения:

    - 1 для развертывания на основе манифеста

    - 0 для развертывания на основе диска

- **TemplateFileName**

- Другие свойства шаблона

> [!NOTE]
> Отключение ведения журнала, удалите файл pkgdef, или измените значение свойства `EnableTemplateDiscoveryLog` для `dword:00000000`, а затем запустите `devenv /updateConfiguration` еще раз.

## <a name="see-also"></a>См. также

[Создание пользовательских шаблонов проектов и элементов](creating-custom-project-and-item-templates.md)