---
ms.openlocfilehash: 0170c6ed655ce54e2dbadf57341dff56616186ec
ms.sourcegitcommit: 748d9cd7328a30f8c80ce42198a94a4b5e869f26
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68147229"
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
