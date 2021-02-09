---
title: Устранение неполадок при обнаружении шаблонов в Visual Studio | Документация Майкрософт
description: Узнайте, как включить ведение журнала диагностики для устранения неполадок при развертывании пользовательских проектов и шаблонов в пакете SDK для Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 01/02/2018
ms.topic: troubleshooting
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 23e30ddb5f43a755fc2dc0206509e403e802c3e7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99893494"
---
# <a name="troubleshooting-template-installation"></a>Устранение неполадок при установке шаблона

При возникновении проблем с развертыванием шаблонов проектов или элементов можно включить ведение журнала диагностики.

::: moniker range="vs-2017"

1. Создайте файл pkgdef в папке *Common7\IDE\CommonExtensions* для своей установки. Например, *C:\Program Files (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\IDE\CommonExtensions\EnablePkgDefLogging.pkgdef*.

::: moniker-end

::: moniker range=">=vs-2019"

1. Создайте файл pkgdef в папке *Common7\IDE\CommonExtensions* для своей установки. Например, *C:\Program Files (x86) \Microsoft Visual Studio\2019\Enterprise\Common7\IDE\CommonExtensions\EnablePkgDefLogging.pkgdef*.

::: moniker-end

2. Добавьте следующий объект в файл pkgdef:

    ```
    [$RootKey$\VsTemplate]
    "EnableTemplateDiscoveryLog"=dword:00000001
    ```

3. Откройте [Командная строка разработчика](/dotnet/framework/tools/developer-command-prompt-for-vs) для установки и запуска `devenv /updateConfiguration` .

::: moniker range="vs-2017"

4. Откройте Visual Studio и запустите диалоговые окна Новый проект и новый элемент, чтобы инициализировать оба дерева шаблонов.

   Теперь журнал шаблона отображается в **%LocalAppData%\Microsoft\VisualStudio\15.0_ [InstanceId] \VsTemplateDiagnosticsList.csv** (InstanceId соответствует идентификатору установки вашего экземпляра Visual Studio). Каждая инициализация дерева шаблонов добавляет записи в этот журнал.

::: moniker-end

::: moniker range=">=vs-2019"

4. Откройте Visual Studio и запустите диалоговые окна **Создание нового проекта** и создание нового **элемента** , чтобы инициализировать оба дерева шаблонов.

   Теперь журнал шаблона отображается в **%LocalAppData%\Microsoft\VisualStudio\16.0_ [InstanceId] \VsTemplateDiagnosticsList.csv** (InstanceId соответствует идентификатору установки вашего экземпляра Visual Studio). Каждая инициализация дерева шаблонов добавляет записи в этот журнал.

::: moniker-end

Файл журнала содержит следующие столбцы:

- **Фуллпастотемплате**, который имеет следующие значения:

  - 1 для развертывания на основе манифеста

  - 0 для развертывания на основе диска

- **темплатефиленаме**

- Другие свойства шаблона

> [!NOTE]
> Чтобы отключить ведение журнала, удалите файл pkgdef либо измените значение `EnableTemplateDiscoveryLog` на `dword:00000000` , а затем `devenv /updateConfiguration` снова запустите.

## <a name="see-also"></a>См. также раздел

- [Создание пользовательских шаблонов проектов и элементов](creating-custom-project-and-item-templates.md)
- [Устранение неполадок в Visual Studio](/troubleshoot/visualstudio/welcome-visual-studio/)
