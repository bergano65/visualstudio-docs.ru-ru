---
ms.openlocfilehash: 0170c6ed655ce54e2dbadf57341dff56616186ec
ms.sourcegitcommit: 2ee11676af4f3fc5729934d52541e9871fb43ee9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/17/2019
ms.locfileid: "65839428"
---
> [!WARNING]
> Когда вы включаете диагностику в существующей роли, при развертывании пакета все настроенные расширения будут отключены. Сюда входит следующее.
>
> * диагностика агента мониторинга Microsoft;
> * мониторинг системы безопасности Microsoft Azure;
> * Антивредоносное ПО Майкрософт                 
> * Агент наблюдения Microsoft
> * агент профилировщика службы Microsoft;      
> * расширение домена Microsoft Azure;        
> * Расширение Диагностики Azure для Windows   
> * расширение удаленного рабочего стола Microsoft Azure;
> * сборщик журналов Microsoft Azure.
>
> Развернув обновленную роль, вы сможете сбросить расширения с использованием портала Azure или PowerShell.
>
