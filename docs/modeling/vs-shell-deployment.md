---
title: Развертывание VS Shell
ms.date: 11/04/2016
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3ca497244a806324d9d2315fa1b1b89404838ff3
ms.sourcegitcommit: 7b60e81414a82c6d34f6de1a1f56115c9cd26943
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2020
ms.locfileid: "81445003"
---
# <a name="vs-shell-deployment"></a>Развертывание VS Shell

Изолированная оболочка позволяет определить, какая функция Visual Studio вам нужна для взаимодействия с языком, на котором предназначен для домена, и как должно отображаться это решение. Для получения дополнительной информации об изолированной оболочке Visual Studio [см.](https://docs.microsoft.com/visualstudio/extensibility/customizing-the-isolated-shell)

Чтобы установить Visual Studio Shell в качестве цели развертывания:

1. В проекте **DslPackage,** **открытые source.extension.tt**.

2. Под `<SupportedProducts>` вставкой:

   ```xml
   <IsolatedShell Version="1.0">MyIsolatedShell</IsolatedShell>
   ```

   Замените *MyIsolatedShell* именем изолированного пакета оболочки.
