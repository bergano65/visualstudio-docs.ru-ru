---
title: Развертывание VS Shell
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 61cf6e716f082abf28043d56d1a8803853d894aa
ms.sourcegitcommit: ef828606e9758c7a42a2f0f777c57b2d39041ac3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/06/2018
ms.locfileid: "39566677"
---
# <a name="vs-shell-deployment"></a>Развертывание VS Shell

Изолированной оболочки позволяет определить, какие Visual Studio функциональные возможности, вам понадобится взаимодействовать с вашего доменного языка и как это решение должно выглядеть. Дополнительные сведения о изолированная оболочка Visual Studio, см. в разделе [Настройка изолированной оболочки](../extensibility/customizing-the-isolated-shell.md).

## <a name="to-set-a-visual-studio-shell-as-the-deployment-target"></a>Чтобы задать оболочку Visual Studio в качестве цели развертывания

1.  В **DslPackage** откройте проект **source.extension.tt**.

2.  В разделе `<SupportedProducts>` вставки:

    ```xml
    <IsolatedShell Version="1.0">MyIsolatedShell</IsolatedShell>
    ```

     Замените *MyIsolatedShell* с именем пакета изолированной оболочки.