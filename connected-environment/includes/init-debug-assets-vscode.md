---
ms.topic: include
ms.openlocfilehash: dbf7482acb02c6347c9c0d0765ef962cfb43a050
ms.sourcegitcommit: 928885ace538bef5b25961358d4f166d648f196a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2018
---
## <a name="initialize-debug-assets-with-the-vs-code-extension"></a>Инициализации ресурсов отладки с расширением VS Code
Сначала нам нужно настроить наш проект кода, чтобы наладить взаимодействие между VS Code и нашей средой разработки в Azure. Расширение VS Code для подключенной среды предоставляет вспомогательную команду для настройки конфигурации отладки. 

Откройте **Палитру команд** (с помощью меню **Вид | Палитра команд**) и используйте автоматическое завершение, чтобы ввести и выбрать эту команду: `Connected Environment: Create configuration files for connected development`. 

При этом добавляется конфигурация отладки для подключенной среды в папке `.vscode`.

![](../media/vsce-command-palette.png)

> [!Note]
> **ВАЖНО**. В связи с ошибкой необходимо закрыть и повторно открыть VS Code, прежде чем продолжить.