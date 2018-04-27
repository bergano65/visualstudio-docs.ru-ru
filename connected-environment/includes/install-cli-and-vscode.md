---
ms.topic: include
ms.openlocfilehash: 78de57178350d4317896c41a455efbeeb553c58d
ms.sourcegitcommit: 928885ace538bef5b25961358d4f166d648f196a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2018
---
## <a name="install-the-connected-environment-cli"></a>Установка интерфейса командной строки в подключенной среде
Для подключенной среды требуется минимальная настройка локального компьютера. Большая часть конфигураций среды разработки хранится в облаке и используется совместно с другими пользователями.

### <a name="install-on-mac"></a>Установка на Mac
Загрузите и установите интерфейс командной строки подключенной среды:
```cmd
curl -L https://aka.ms/get-vsce-mac | bash
```

### <a name="install-on-windows"></a>Установка в Windows
1. Загрузите и запустите [установщик интерфейса командной строки для подключенной среды](https://aka.ms/get-vsce-windows). 

### <a name="install-on-linux"></a>Установка на Linux
Ожидается в ближайшее время...

## <a name="get-kubernetes-debugging-for-vs-code"></a>Отладка Kubernetes в VS Code
Конечно, вы можете использовать интерфейс командной строки для подключенных сред в качестве отдельного инструмента, но разработчикам .NET Core и Node.js в VS Code доступны широкие возможности, например отладка Kubernetes.

1. Установите [VS Code](https://code.visualstudio.com/Download), если вы еще этого не сделали.
1. Загрузите [расширение подключенной среды VS](https://aka.ms/get-vsce-code).
1. Установка расширения: 

```cmd
code --install-extension path-to-downloaded-extension/vsce-0.1.1.vsix
```
