---
ms.topic: include
ms.openlocfilehash: 502bd8d206b43fc219c850ab870db35e6c3af1c0
ms.sourcegitcommit: 928885ace538bef5b25961358d4f166d648f196a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2018
ms.locfileid: "32031213"
---
## <a name="sign-in-to-azure"></a>Вход в Azure
Нам нужно будет войти в Azure, чтобы создать нашу среду разработки. В окне терминала введите следующую команду:
```cmd
az login
```

> [!Note]
> Если у вас нет подписки Azure, вы можете создать [бесплатную учетную запись](https://azure.microsoft.com/free).

### <a name="if-you-have-multiple-azure-subscriptions"></a>Если у вас несколько подписок Azure...
Вы можете просмотреть подписки, выполнив: 
```cmd
az account list
```
Найдите подписку, имеющую `isDefault: true` в выходных данных JSON.
Если вы хотите использовать не эту подписку, можно изменить подписку по умолчанию:
```cmd
az account set --subscription <subscription ID>
```
