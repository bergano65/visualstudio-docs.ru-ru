---
title: Параметры отладки облачных служб Azure | Документация Майкрософт
description: Отладка облачных служб Azure
author: mikejo5000
manager: jmartens
ms.topic: conceptual
ms.workload: azure-vs
ms.date: 03/18/2017
ms.author: mikejo
ms.technology: vs-ide-debug
ms.openlocfilehash: 12b327c65b83acde09eeac748d614ca560f3e012
ms.sourcegitcommit: 5654b7a57a9af111a6f29239212d76086bc745c9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/03/2021
ms.locfileid: "101683086"
---
# <a name="learn-the-various-ways-to-debug-an-azure-cloud-service"></a>Разные способы отладки облачной службы Azure
В этой статье приведены ссылки на различные способы отладки облачной службы Azure.

## <a name="debugging-an-azure-cloud-service-in-visual-studio"></a>Отладка облачной службы Azure в Visual Studio
Вы можете сэкономить время и деньги с помощью эмулятора вычислений Azure для отладки облачной службы на локальном компьютере. Посредством локальной отладки службы перед ее развертыванием можно повысить надежность и производительность службы, не платя за время использования вычислительных ресурсов. Однако некоторые ошибки могут возникнуть только при запуске облачной службы в среде Azure. Ошибки, которые возникают только при запуске облачной службы в среде Azure, можно устранить, если включить удаленную отладку при публикации службы, а затем подключить отладчик к экземпляру роли. Дополнительные сведения см. в разделе [Отладка облачной службы на локальном компьютере](vs-azure-tools-debug-cloud-services-virtual-machines.md#debug-your-cloud-service-on-your-local-computer).

## <a name="using-intellitrace"></a>Использование IntelliTrace
Если Visual Studio Enterprise используется для написания ролей для .NET Framework 4.5, вы можете включить IntelliTrace в момент развертывания облачной службы Azure из Visual Studio. IntelliTrace предоставляет журнал, который можно использовать с Visual Studio для отладки приложения как в Azure. Дополнительные сведения см. в статье [Отладка опубликованной облачной службы с помощью IntelliTrace и Visual Studio](vs-azure-tools-intellitrace-debug-published-cloud-services.md).

## <a name="remote-debugging"></a>Удаленная отладка
Удаленную отладку облачной службы можно включить при развертывании облачной службы в Visual Studio. Если для развертывания выбрана удаленная отладка, службы удаленной отладки будут установлены на все виртуальные машины, где выполняются экземпляры роли. Такие службы (например, `msvsmon.exe`) не влияют на производительность и не требуют дополнительных расходов. Дополнительные сведения см. в разделе [Отладка облачной службы в Azure](vs-azure-tools-debug-cloud-services-virtual-machines.md#debug-a-cloud-service-in-azure).

## <a name="next-steps"></a>Дальнейшие действия
- [Отладка облачной службы или виртуальной машины Azure в Visual Studio](./vs-azure-tools-debug-cloud-services-virtual-machines.md): сведения об отладке облачных служб Azure.
