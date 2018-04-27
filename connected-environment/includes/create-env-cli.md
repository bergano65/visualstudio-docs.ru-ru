---
ms.topic: include
ms.openlocfilehash: 97f9885780c9f697cfc6a58b78054761fdcd725d
ms.sourcegitcommit: 928885ace538bef5b25961358d4f166d648f196a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2018
---
## <a name="create-a-kubernetes-development-environment-in-azure"></a>Создание среды разработки Kubernetes в Azure
С помощью подключенных сред можно создавать среды на основе Kubernetes, полностью управляемые Azure и оптимизированные для разработки. Эта команда создает среду с именем `mydevenvironment` в `eastus`.
```cmd
vsce env create --name mydevenvironment --location eastus
```

Поддерживаемые расположения: `eastus`, `westeurope`

> [!Note]
> Выполнение этой команды занимает около шести минут. А пока вы можете продолжить изучение руководства.
