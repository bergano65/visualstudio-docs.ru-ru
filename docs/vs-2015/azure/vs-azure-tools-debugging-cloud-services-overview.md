---
title: Параметры отладки Azure облачные службы | Документация Майкрософт
description: Отладка облачных служб Azure
author: mikejo5000
manager: douge
ms.assetid: 80755da7-8350-4f5c-97ce-2962beabb36d
ms.topic: conceptual
ms.workload: azure-vs
ms.date: 03/18/2017
ms.author: mikejo
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.openlocfilehash: bd2608371871b7adc925fc11927fe061b00a1ec6
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/05/2018
ms.locfileid: "51002884"
---
# <a name="learn-the-various-ways-to-debug-an-azure-cloud-service"></a>Разные способы отладки облачной службы Azure
В этой статье ссылки на различные способы отладки облачной службы Azure. 

## <a name="debugging-an-azure-cloud-service-in-visual-studio"></a>Отладка облачной службы Azure в Visual Studio
Вы можете сэкономить время и деньги с помощью Azure эмулятора для отладки облачной службы на локальном компьютере. С локальной отладки службы перед ее развертыванием можно улучшить надежность и производительность без необходимости платить за вычислительное время. Тем не менее некоторые ошибки могут возникнуть только при запуске облачной службы в Azure. Ошибки, возникающие только в том случае, при запуске облачной службы в Azure можно устранить, если включить удаленную отладку при публикации службы, а затем подключить отладчик к экземпляру роли. Дополнительные сведения см. в разделе [отладка облачной службы на локальном компьютере](vs-azure-tools-debug-cloud-services-virtual-machines.md#debug-your-cloud-service-on-your-local-computer).

## <a name="using-intellitrace"></a>Использование IntelliTrace 
Если вы используете Visual Studio Enterprise для написания ролей .NET Framework 4.5, можно включить IntelliTrace в момент развертывания облачной службы Azure из Visual Studio. IntelliTrace предоставляет журнал, который можно использовать с Visual Studio для отладки приложения, как если бы оно было запущено в Azure. Дополнительные сведения см. в разделе [отладка опубликованной облачной службы с помощью IntelliTrace и Visual Studio](http://go.microsoft.com/fwlink/p/?LinkId=623016).

## <a name="remote-debugging"></a>Удаленная отладка 
Вы можете включить удаленную отладку облачных служб во время, при развертывании облачной службы из Visual Studio. Если вы решили включить удаленную отладку для развертывания, службы удаленной отладки устанавливаются на виртуальных машинах, которые выполняются экземпляры роли. Эти службы — такие как `msvsmon.exe` — не влияют на производительность и не требуют дополнительных расходов. Дополнительные сведения см. в разделе [отладка облачной службы в Azure](vs-azure-tools-debug-cloud-services-virtual-machines.md#debug-a-cloud-service-in-azure).

## <a name="next-steps"></a>Следующие шаги
- [Отладка облачной службы Azure или виртуальной Машины в Visual Studio](./vs-azure-tools-debug-cloud-services-virtual-machines.md) -ознакомьтесь с подробными сведениями об отладке облачных служб Azure.