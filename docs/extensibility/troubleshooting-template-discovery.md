---
title: "Устранение неполадок обнаружения шаблон в Visual Studio | Документы Microsoft"
ms.custom: 
ms.date: 01/02/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 72663d56844fcc34164e9408ab14c8ead234683e
ms.sourcegitcommit: 9357209350167e1eb7e50b483e44893735d90589
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/05/2018
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