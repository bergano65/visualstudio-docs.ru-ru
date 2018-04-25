---
title: Развертывание VS Shell
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 816997f971e90ddd27f8e24cdc1857559e04ff70
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/20/2018
---
# <a name="vs-shell-deployment"></a>Развертывание VS Shell

Изолированная оболочка позволяет определить, какие Visual Studio функциональности необходимо взаимодействовать с доменный язык и отображением этого решения. Дополнительные сведения о Visual Studio изолированной оболочки см. в разделе [Настройка изолированной оболочки](../extensibility/customizing-the-isolated-shell.md).

## <a name="to-set-a-visual-studio-shell-as-the-deployment-target"></a>Для установки оболочки Visual Studio в качестве цели развертывания

1.  В **DslPackage** откройте проект **source.extension.tt**.

2.  В разделе `<SupportedProducts>` вставки:

    ```
    <IsolatedShell Version="1.0">MyIsolatedShell</IsolatedShell>
    ```

     Замените *MyIsolatedShell* с именем пакета изолированной оболочки.