---
title: Развертывание VS Shell
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: bc86574b380e0a29042dcc1dc20851258c9f1bc3
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "55033575"
---
# <a name="vs-shell-deployment"></a>Развертывание VS Shell

Изолированной оболочки позволяет определить, какие Visual Studio функциональные возможности, вам понадобится взаимодействовать с вашего доменного языка и как это решение должно выглядеть. Дополнительные сведения о изолированная оболочка Visual Studio, см. в разделе [Настройка изолированной оболочки](https://vspartner.com/pages/vsshells).

Чтобы задать оболочку Visual Studio в качестве цели развертывания:

1. В **DslPackage** откройте проект **source.extension.tt**.

2. В разделе `<SupportedProducts>` вставки:

   ```xml
   <IsolatedShell Version="1.0">MyIsolatedShell</IsolatedShell>
   ```

   Замените *MyIsolatedShell* с именем пакета изолированной оболочки.