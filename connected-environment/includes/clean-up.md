---
ms.topic: include
ms.openlocfilehash: 94e82185b05900101f91e4b368bb30d2aaceac03
ms.sourcegitcommit: 928885ace538bef5b25961358d4f166d648f196a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2018
---
## <a name="clean-up"></a>Очистка
Чтобы полностью удалить среду подключения в Azure, в том числе все запущенные службы, используйте команду `vsce env rm`. Не забывайте, что это действие необратимо.

В следующем примере указаны подключенные среды в вашей действующей подписке Azure, а затем удаляется среда с именем myenv в группе ресурсов myenv-rg.

```cmd
vsce env list
vsce env rm --name myenv --resource-group myenv-rg
```

