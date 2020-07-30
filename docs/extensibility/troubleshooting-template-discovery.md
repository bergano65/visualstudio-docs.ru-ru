---
title: Устранение неполадок при обнаружении шаблонов в Visual Studio | Документация Майкрософт
ms.date: 01/02/2018
ms.topic: troubleshooting
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 89ff5b9974f20841378f367c3cb631a8d4cf7787
ms.sourcegitcommit: 9a7fb8556a5f3dbb4459122fefc7e7a8dfda753a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/27/2020
ms.locfileid: "87235047"
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
