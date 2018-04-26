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
ms.openlocfilehash: e7df1991832e954def71a6cee5bd5516dfd4e961
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
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